---
title: Blockieren von bösartigem Traffic für Adobe Commerce auf Fastly-Ebene
description: In diesem Artikel finden Sie die Schritte, die Sie unternehmen können, um bösartigen Traffic zu blockieren, wenn Sie vermuten, dass Ihr Adobe Commerce im Cloud-Infrastrukturspeicher einen DDoS-Angriff durchläuft.
exl-id: 1a834a0a-753b-432e-9c3b-ef8dd034d294
feature: Cache, Marketing Tools
source-git-commit: 8e64b148938394e67265da543784b2769df56c58
workflow-type: tm+mt
source-wordcount: '932'
ht-degree: 0%
---
# Blockieren von bösartigem Traffic für Adobe Commerce auf Fastly-Ebene

In diesem Artikel wird erläutert, wie Sie unerwünschten Traffic in Ihrem Geschäft blockieren können, nicht nur als Reaktion auf bösartige Bedrohungen, sondern auch als Methode zur geografischen Filterung.

Adobe Commerce on Cloud Infrastructure (und Fastly CDN) bietet Tools zur Verwaltung des Traffics an Ihrem Store als Reaktion auf bösartige Bedrohungen wie DDoS-Angriffe. Darüber hinaus können Sie Anfragen aus bestimmten Ländern oder Regionen blockieren, auch wenn keine böswillige Absicht erkannt wird, um Geschäftsrichtlinien, gesetzliche Anforderungen oder andere betriebliche Anforderungen zu erfüllen.

## Betroffene Produkte und Versionen:

* Adobe Commerce auf Cloud-Infrastruktur 2.3.x

In diesem Artikel gehen wir davon aus, dass Sie bereits über die böswilligen IPs und/oder deren Länder- und Benutzeragenten verfügen. Benutzende von Adobe Commerce auf Cloud-Infrastrukturen erhalten diese Informationen normalerweise vom Adobe Commerce-Support. In den folgenden Abschnitten finden Sie Schritte zum Sperren des Traffics auf der Grundlage dieser Informationen. Alle Änderungen sollten in der Produktionsumgebung vorgenommen werden.

## Zugriff auf das Admin-Bedienfeld erhalten

Wenn Ihre Website durch DDoS überlastet ist, können Sie sich möglicherweise nicht bei Ihrem Commerce-Administrator anmelden (und alle in diesem Artikel beschriebenen Schritte ausführen).

Um Zugriff auf den Admin zu erhalten, setzen Sie Ihre Website in den Wartungsmodus, wie in [Aktivieren oder Deaktivieren des Wartungsmodus](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) beschrieben, und setzen Sie Ihre IP-Adresse auf die Zulassungsliste. Deaktivieren Sie danach den Wartungsmodus.

## Blockieren des Traffics nach IP

Für den Adobe Commerce on Cloud Infrastructure Store besteht die effektivste Möglichkeit, den Traffic durch bestimmte IP-Adressen und Subnetze zu blockieren, darin, eine ACL für Fastly in Commerce Admin hinzuzufügen. Im Folgenden finden Sie die Schritte mit Links zu detaillierteren Anweisungen:

1. Navigieren Sie in Commerce Admin zu **Stores** > **Configuration** > **Advanced** > **System** > **Full Page Cache** > **Fastly Configuration**.
1. [Erstellen Sie eine neue ACL](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/ACL.md) mit einer Liste von IP-Adressen oder Subnetzen, die Sie blockieren werden.
1. Fügen Sie es zur ACL-Liste hinzu und blockieren Sie es, wie im [Blocking](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md)-Handbuch für das Fastly\_Cdn-Modul für Adobe Commerce beschrieben.

## Blockieren des Traffics nach Land

Für den Adobe Commerce on Cloud Infrastructure Store besteht die effektivste Möglichkeit, Traffic nach Land(ern) zu blockieren, darin, eine ACL für Fastly in der Commerce-Admin hinzuzufügen.

1. Navigieren Sie in Commerce Admin zu **Stores** > **Configuration** > **Advanced** > **System** > **Full Page Cache** > **Fastly Configuration**.
1. Wählen Sie die Länder aus und konfigurieren Sie die Blockierung mithilfe von ACL, wie [Blockierung](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md) Handbuch für das Fastly\_Cdn-Modul für Adobe Commerce beschrieben.

## Blockieren des Traffics durch den Benutzeragenten

Um die Blockierung basierend auf dem Benutzeragenten einzurichten, müssen Sie ein benutzerdefiniertes VCL-Snippet zu Ihrer Fastly-Konfiguration hinzufügen. Gehen Sie dazu wie folgt vor:

1. Navigieren Sie in der Commerce-**[!UICONTROL Admin]** zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]**.
1. Dann **[!UICONTROL Fastly Configuration]** > **[!UICONTROL Custom VCL Snippets]**.
1. Erstellen Sie das neue benutzerdefinierte Snippet wie im Handbuch [Benutzerdefinierte VCL-Snippets](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/CUSTOM-VCL-SNIPPETS.md) für das Modul Fastly\_Cdn beschrieben. Sie können das folgende Codebeispiel als Beispiel verwenden. In diesem Beispiel wird Traffic für den `AhrefsBot` Benutzeragenten nicht zugelassen.

```php
name: block_bad_useragents
  type: recv
  priority: 5
  VCL:
  if ( req.http.User-Agent ~ "(AhrefsBot)" ) {
      error 405 "Not allowed";
  }
```

## Blockieren des Traffics durch JA3/JA4/OH-Signaturen (Erfassen Sie die JA3-, JA4- und OHFP-Werte von Newrelic)

1. Wörterbuch erstellen: Navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full page cache]** > **[!UICONTROL Fastly configuration]** > **[!UICONTROL Edge Dictionary]** und erstellen Sie diesen Beispielblock:

   ```
   #table ja3_blocklist:
   table ja3_blocklist {
       "********************************": "********************************",
   }
   
   #table ja4_blocklist:
   table filter_bad_ja4 {
       "************************************": "************************************",
   }
   ```

1. Fügen Sie dann eine VCL hinzu, um alle in der oben definierten Tabelle aufgelisteten JA3, JA4 zu blockieren:

   ```
   name: block_traffic_ja3_ja4
   type: recv 
   priority: 5 
   
   VCL:
   if (req.restarts == 0 && fastly.ff.visits_this_service == 0) {
     if(table.contains(ja3_blocklist, tls.client.ja3_md5)){
       error 403;
     }
     if(table.contains(ja4_blocklist, tls.client.ja4)){
       error 403;
     }
   }
   ```

1. Blockbeispiel basierend auf OHFP:

   ```
   #table ohfp_h2fp_blocklist
   table ohfp_h2fp_blocklist {
       "xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx":"xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx",
   }
   ```


1. Fügen Sie dann eine VCL hinzu, um alle in der oben definierten Tabelle aufgelisteten OHFP zu blockieren:

   ```
   # Snippet block_ohfp_h2fp
   name: block_ohfp_h2fp
   type: recv 
   Priority: 5
   
   if (table.contains(ohfp_h2fp_blocklist, fastly_info.oh_fingerprint)) {
     error 403 "Forbidden";
   }
   ```


## Ratenbegrenzung (experimentelle Fastly-Funktion)

Es gibt eine experimentelle Fastly-Funktion für Adobe Commerce in der Cloud-Infrastruktur, mit der Sie die Ratenbeschränkung für bestimmte Pfade und Crawlers angeben können. Einzelheiten finden Sie in der [Fastly](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/RATE-LIMITING.md)Moduldokumentation.

Die Funktion muss ausführlich in der Staging-Umgebung getestet werden, bevor sie in der Produktion verwendet wird, da sie legitimen Traffic blockieren könnte.

## Empfehlung: Aktualisieren Sie ggf. robots.txt

Das Aktualisieren der `robots.txt` kann dazu beitragen, dass bestimmte Suchmaschinen, Crawler und Roboter bestimmte Seiten nicht crawlen werden. Beispiele für Seiten, die nicht crawlen werden sollten, sind Suchergebnisseiten, Checkout, Kundeninformationen usw. Wenn Roboter diese Seiten nicht crawlen haben, kann dies dazu beitragen, die Anzahl der von diesen Robotern generierten Anfragen zu verringern.

Bei der Verwendung von `robots.txt` sind zwei wichtige Aspekte zu beachten:

* Roboter können Ihre `robots.txt` ignorieren. Vor allem Malware-Roboter, die das Internet nach Sicherheitslücken durchsuchen, und E-Mail-Adressen-Harvester, die von Spammern verwendet werden, werden keine Aufmerksamkeit schenken.
* Die `robots.txt` ist eine öffentlich verfügbare Datei. Jeder kann sehen, welche Bereiche des Servers Roboter nicht benutzen sollen.

Die grundlegenden Informationen und die standardmäßige Adobe Commerce `robots.txt`-Konfiguration finden Sie im Artikel [Suchmaschinenroboter](https://experienceleague.adobe.com/de/docs/commerce-admin/marketing/seo/seo-overview#search-engine-robots) in unserer Entwicklerdokumentation.

Allgemeine Informationen und Empfehlungen zu `robots.txt` finden Sie unter:

* [Erstellen einer Datei „robots.txt](https://developers.google.com/search/docs/advanced/robots/create-robots-txt) von Google Support
* [Über /robots.txt](https://www.robotstxt.org/robotstxt.html) von robotstxt.org

Arbeiten Sie mit Ihrem Entwickler und/oder SEO-Experten zusammen, um zu bestimmen, welche Benutzeragenten Sie zulassen möchten oder welche Sie nicht zulassen möchten.

## Verwandtes Lesen

* [Produktspezifische Lizenzbedingungen für Adobe Commerce on Cloud Service](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/PSLT-AdobeCommerceCloud-WW-2023v1.pdf)
* [Benutzerdefinierte VCL zum Blockieren von Anfragen](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/cdn/custom-vcl-snippets/fastly-vcl-blocking) im Handbuch zu Commerce in Cloud Manager
