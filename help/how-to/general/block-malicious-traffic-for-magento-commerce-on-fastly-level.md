---
title: Begrenzen Sie schädlichen Traffic für Adobe Commerce auf der schnellsten Ebene.
description: Dieser Artikel enthält die Schritte, die Sie unternehmen können, um böswilligen Traffic zu verhindern, wenn Sie vermuten, dass Ihr Adobe Commerce im Cloud-Infrastrukturspeicher einen DDoS-Angriff durchmacht.
exl-id: 1a834a0a-753b-432e-9c3b-ef8dd034d294
feature: Cache, Marketing Tools
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 0%

---

# Begrenzen Sie schädlichen Traffic für Adobe Commerce auf der schnellsten Ebene.

Dieser Artikel enthält die Schritte, die Sie unternehmen können, um böswilligen Traffic zu verhindern, wenn Sie vermuten, dass Ihr Adobe Commerce im Cloud-Infrastrukturspeicher einen DDoS-Angriff durchmacht.

## Betroffene Produkte und Versionen:

* Adobe Commerce auf Cloud-Infrastruktur 2.3.x

In diesem Artikel gehen wir davon aus, dass Sie bereits über die böswilligen IPs und/oder deren Land und Benutzeragenten verfügen. Adobe Commerce für Cloud-Infrastrukturbenutzer erhalten diese Informationen normalerweise vom Adobe Commerce-Support. Die folgenden Abschnitte enthalten Schritte zum Blockieren des Traffics auf der Grundlage dieser Informationen. Alle Änderungen sollten in der Produktionsumgebung vorgenommen werden.

## Zugriff auf das Admin Panel

Wenn Ihre Website von DDoS überlastet ist, können Sie sich möglicherweise nicht bei Ihrem Commerce-Administrator anmelden (und alle in diesem Artikel beschriebenen Schritte ausführen).

Um Zugriff auf den Admin zu erhalten, stellen Sie Ihre Website in den Wartungsmodus, wie unter [Wartungsmodus aktivieren oder deaktivieren](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) beschrieben, und setzen Sie Ihre IP-Adresse auf die Whitelist. Deaktivieren Sie den Wartungsmodus, nachdem dies abgeschlossen ist.

## Blockieren des Datenverkehrs nach IP

Für die Adobe Commerce im Cloud-Infrastrukturspeicher besteht die wirksamste Möglichkeit, den Traffic nach bestimmten IP-Adressen und Subnetzen zu blockieren, darin, im Commerce-Admin eine ACL für Fastly hinzuzufügen. Im Folgenden finden Sie die Schritte mit Links zu detaillierteren Anweisungen:

1. Navigieren Sie im Commerce-Admin zu &quot;**Stores**&quot;> &quot;**Konfiguration**&quot;> &quot;**Erweitert**&quot;> &quot;**System**&quot;> &quot;**Gesamter Seiten-Cache**&quot;> &quot;**Schnelle Konfiguration**&quot;.
1. [Erstellen Sie eine neue ACL](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/ACL.md) mit einer Liste von IP-Adressen oder Subnetzen, die Sie blockieren werden.
1. Fügen Sie ihn zur ACL-Liste und zum Block hinzu, wie im Handbuch [Blocking](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md) für das Fastly\_CDN-Modul für Adobe Commerce beschrieben.

## Blockieren des Datenverkehrs nach Ländern

Für die Adobe Commerce im Cloud-Infrastrukturspeicher besteht die wirksamste Möglichkeit, den Datenverkehr nach Ländern zu blockieren, darin, im Commerce-Administrator eine ACL für Fastly hinzuzufügen.

1. Navigieren Sie im Commerce-Admin zu &quot;**Stores**&quot;> &quot;**Konfiguration**&quot;> &quot;**Erweitert**&quot;> &quot;**System**&quot;> &quot;**Gesamter Seiten-Cache**&quot;> &quot;**Schnelle Konfiguration**&quot;.
1. Wählen Sie die Länder aus und konfigurieren Sie die Blockierung mithilfe von ACL, wie im Handbuch [Blocking](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md) für das Fastly\_CDN-Modul für Adobe Commerce beschrieben.

## Blockieren des Traffics durch den Benutzeragenten

Um eine Blockierung basierend auf dem Benutzeragenten einzurichten, müssen Sie Ihrer Fastly-Konfiguration ein benutzerdefiniertes VCL-Snippet hinzufügen. Gehen Sie dazu wie folgt vor:

1. Navigieren Sie im Commerce-Admin zu &quot;**Stores**&quot;> &quot;**Konfiguration**&quot;> &quot;**Erweitert**&quot;> &quot;**System**&quot;> &quot;**Gesamter Seiten-Cache**&quot;.
1. Dann **Fastly Configuration** > **Custom VCL Snippets**.
1. Erstellen Sie das neue benutzerdefinierte Snippet wie im Handbuch [Benutzerdefinierte VCL-Snippets](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/CUSTOM-VCL-SNIPPETS.md) für das Fastly\_Cdn-Modul beschrieben. Sie können das folgende Codebeispiel verwenden. In diesem Beispiel wird der Traffic für die Benutzeragenten `AhrefsBot` und `SemrushBot` deaktiviert.

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

Es gibt eine experimentelle Fastly-Funktion für Adobe Commerce in der Cloud-Infrastruktur, mit der Sie das Ratenlimit für bestimmte Pfade und Crawler festlegen können. Weitere Informationen finden Sie in der Dokumentation zum [Fastly-Modul](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/RATE-LIMITING.md) .

Die Funktionalität muss vor der Verwendung in der Produktion umfassend auf dem Staging getestet werden, da dies legitimen Traffic blockieren kann.

## Empfohlen: Aktualisieren Sie robots.txt

Durch die Aktualisierung Ihrer `robots.txt` -Datei können Sie verhindern, dass bestimmte Suchmaschinen, Crawler und Roboter bestimmte Seiten durchsuchen. Beispiele für Seiten, die nicht durchsucht werden sollten, sind Suchergebnisseiten, Checkout, Kundeninformationen usw. Wenn Roboter diese Seiten nicht durchsuchen können, kann die Anzahl der von diesen Robotern generierten Anfragen reduziert werden.

Bei Verwendung von `robots.txt` sind zwei wichtige Aspekte zu beachten:

* Roboter können Ihre `robots.txt` ignorieren. Insbesondere Malware-Roboter, die das Web auf Sicherheitslücken scannen, und E-Mail-Adressen-Ernster, die von Spammern verwendet werden, werden keine Beachtung finden.
* Die Datei &quot;`robots.txt`&quot; ist eine öffentlich verfügbare Datei. Jeder kann sehen, welche Bereiche Ihres Servers Sie nicht von Robotern verwenden möchten.

Die grundlegenden Informationen und die standardmäßige Adobe Commerce `robots.txt`-Konfiguration finden Sie im Artikel [Suchmaschinen-Roboter](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/seo/seo-overview#search-engine-robots) in unserer Entwicklerdokumentation.

Allgemeine Informationen und Empfehlungen zu `robots.txt` finden Sie unter:

* [Erstellen Sie eine robots.txt](https://developers.google.com/search/docs/advanced/robots/create-robots-txt) -Datei durch den Google-Support
* [Über /robots.txt](https://www.robotstxt.org/robotstxt.html) von robotstxt.org

Arbeiten Sie mit Ihrem Entwickler und/oder SEO-Experte zusammen, um zu bestimmen, welche Benutzeragenten Sie zulassen möchten oder welche Sie nicht zulassen möchten.

## Verwandte Informationen

[Produktspezifische Lizenzbedingungen für Adobe Commerce on Cloud](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/PSLT-AdobeCommerceCloud-WW-2023v1.pdf)
