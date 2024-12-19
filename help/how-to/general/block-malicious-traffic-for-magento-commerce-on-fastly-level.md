---
title: Blockieren von bösartigem Traffic für Adobe Commerce auf Fastly-Ebene
description: In diesem Artikel finden Sie die Schritte, die Sie unternehmen können, um bösartigen Traffic zu blockieren, wenn Sie vermuten, dass Ihr Adobe Commerce im Cloud-Infrastrukturspeicher einen DDoS-Angriff durchläuft.
exl-id: 1a834a0a-753b-432e-9c3b-ef8dd034d294
feature: Cache, Marketing Tools
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 0%

---

# Blockieren von bösartigem Traffic für Adobe Commerce auf Fastly-Ebene

In diesem Artikel finden Sie die Schritte, die Sie unternehmen können, um bösartigen Traffic zu blockieren, wenn Sie vermuten, dass Ihr Adobe Commerce im Cloud-Infrastrukturspeicher einen DDoS-Angriff durchläuft.

## Betroffene Produkte und Versionen:

* Adobe Commerce auf Cloud-Infrastruktur 2.3.x

In diesem Artikel gehen wir davon aus, dass Sie bereits über die böswilligen IPs und/oder deren Länder- und Benutzeragenten verfügen. Benutzende von Adobe Commerce auf Cloud-Infrastrukturen erhalten diese Informationen normalerweise vom Adobe Commerce-Support. In den folgenden Abschnitten finden Sie Schritte zum Sperren des Traffics auf der Grundlage dieser Informationen. Alle Änderungen sollten in der Produktionsumgebung vorgenommen werden.

## Zugriff auf das Admin-Bedienfeld erhalten

Wenn Ihre Website durch DDoS überlastet ist, können Sie sich möglicherweise nicht bei Ihrem Commerce-Administrator anmelden (und alle in diesem Artikel beschriebenen Schritte ausführen).

Um Zugriff auf den Admin zu erhalten, setzen Sie Ihre Website in den Wartungsmodus, wie in [Aktivieren oder Deaktivieren des Wartungsmodus](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) beschrieben, und setzen Sie Ihre IP-Adresse auf die Zulassungsliste. Deaktivieren Sie danach den Wartungsmodus.

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

1. Navigieren Sie in der Commerce Admin zu **Stores** > **Configuration** > **Advanced** > **System** > **Full Page Cache**.
1. Dann **Fastly Configuration** > **Benutzerdefinierte VCL-Snippets**.
1. Erstellen Sie das neue benutzerdefinierte Snippet wie im Handbuch [Benutzerdefinierte VCL-Snippets](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/CUSTOM-VCL-SNIPPETS.md) für das Modul Fastly\_Cdn beschrieben. Sie können das folgende Codebeispiel als Beispiel verwenden. In diesem Beispiel wird Traffic für die `AhrefsBot` und `SemrushBot` Benutzeragenten nicht zugelassen.

```php
name: block_bad_useragents
  type: recv
  priority: 5
  VCL:
  if ( req.http.User-Agent ~ "(AhrefsBot|SemrushBot)" ) {
      error 405 "Not allowed";
  }
```

## Ratenbegrenzung (experimentelle Fastly-Funktion)

Es gibt eine experimentelle Fastly-Funktion für Adobe Commerce in der Cloud-Infrastruktur, mit der Sie die Ratenbeschränkung für bestimmte Pfade und Crawler angeben können. Einzelheiten finden Sie in der [Fastly](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/RATE-LIMITING.md)Moduldokumentation.

Die Funktion muss ausführlich in der Staging-Umgebung getestet werden, bevor sie in der Produktion verwendet wird, da sie legitimen Traffic blockieren könnte.

## Empfehlung: Aktualisieren Sie ggf. robots.txt

Das Aktualisieren Ihrer `robots.txt` kann dazu beitragen, dass bestimmte Suchmaschinen, Crawler und Roboter bestimmte Seiten nicht durchsuchen. Beispiele für Seiten, die nicht durchsucht werden sollten, sind Suchergebnisseiten, Checkout, Kundeninformationen usw. Wenn Sie verhindern möchten, dass Roboter diese Seiten durchsuchen, kann dies dazu beitragen, die Anzahl der von diesen Robotern generierten Anfragen zu verringern.

Bei der Verwendung von `robots.txt` sind zwei wichtige Aspekte zu beachten:

* Roboter können Ihre `robots.txt` ignorieren. Vor allem Malware-Roboter, die das Internet nach Sicherheitslücken durchsuchen, und E-Mail-Adressen-Harvester, die von Spammern verwendet werden, werden keine Aufmerksamkeit schenken.
* Die `robots.txt` ist eine öffentlich verfügbare Datei. Jeder kann sehen, welche Bereiche des Servers Roboter nicht benutzen sollen.

Die grundlegenden Informationen und die standardmäßige Adobe Commerce `robots.txt`-Konfiguration finden Sie im Artikel [Suchmaschinenroboter](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/seo/seo-overview#search-engine-robots) in unserer Entwicklerdokumentation.

Allgemeine Informationen und Empfehlungen zu `robots.txt` finden Sie unter:

* [Erstellen einer Datei „robots.txt](https://developers.google.com/search/docs/advanced/robots/create-robots-txt) von Google Support
* [Über /robots.txt](https://www.robotstxt.org/robotstxt.html) von robotstxt.org

Arbeiten Sie mit Ihrem Entwickler und/oder SEO-Experten zusammen, um zu bestimmen, welche Benutzeragenten Sie zulassen möchten oder welche Sie nicht zulassen möchten.

## Verwandtes Lesen

[Produktspezifische Lizenzbedingungen für Adobe Commerce on Cloud](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/PSLT-AdobeCommerceCloud-WW-2023v1.pdf)
