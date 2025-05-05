---
title: 'Composer-Update bei Adobe Commerce fehlgeschlagen: Inkompatibler Argumenttyp'
description: Dieser Artikel bietet eine Lösung für den Fall, dass die Bereitstellung blockiert ist, da ein Problem bei der Code-Kompilierung besteht. Dieses Problem wird durch eine neue Version der symfony/console-Abhängigkeit (4.4.27, 4.4.28) verursacht.
exl-id: ba2dd229-29f6-43e2-9467-8bd1bf59e6ef
feature: Console
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# Composer-Update bei Adobe Commerce fehlgeschlagen: Inkompatibler Argumenttyp

>[!NOTE]
>
>Dieses Problem wurde jetzt in der neuesten symfony Version 4.4.29 behoben.

Dieser Artikel bietet eine Lösung für den Fall, dass die Bereitstellung blockiert ist, da ein Problem bei der Code-Kompilierung besteht. Dieses Problem wird durch eine neue Version der symfony/console-Abhängigkeit (4.4.27, 4.4.28) verursacht.

## Betroffene Produkte und Versionen

* Adobe Commerce (alle Bereitstellungsmethoden) und Magento Open Source:
   * 2.4.0, 2.4.0-p1, 2.4.1, 2.4.1-p1, 2.4.2, 2.4.2-p1, 2.4.2-p2, 2.4.3
   * 2.3.5, 2.3.5-P1, 2.3.5-P2, 2.3.6, 2.3.6-P1, 2.3.7, 2.3.7-P1
* symfony/console-Abhängigkeit (4.4.27, 4.4.28).

## Problem

Eine neue Version der symfony/console-Abhängigkeit (4.4.27, 4.4.28) führt dazu, dass die Abhängigkeitskompilierung fehlschlägt.

<u>Schritte zur Reproduktion</u>:

Wenn Sie Adobe Commerce installieren oder aktualisieren oder Composer aktualisieren, schlägt die Ausführung mit der folgenden Fehlermeldung fehl:
*Inkompatibler Argumenttyp: Erforderlicher Typ: int. Tatsächlicher Typ: Zeichenfolge*

## Ursache

Das Problem wird durch die Inkompatibilität des Adobe Commerce-Kern-Codes mit der neuesten „symfony/console“-Abhängigkeit verursacht, die in den Versionen 4.4.27 und 4.4.28 veröffentlicht wurde.

## Lösung

Das Problem wird automatisch behoben, sobald eine neue symfony/console-Version 4.2.29 veröffentlicht wurde (voraussichtlich im August 2021).

**Fehlerbehebung in Adobe Commerce On-Premise:**

Adobe Commerce On-Premises 2.4.x

Führen Sie den folgenden Befehl in der CLI/Terminal aus:

``composer require symfony/console:">=4.4.0 <4.4.27 || ~4.4.29"``

Ab Version 2.3.5 sollten lokale Adobe Commerce-Händler den folgenden CLI-Befehl ausführen:

``composer require symfony/console:"~4.1.0||~4.2.0||~4.3.0||>=4.4.0 <4.4.27 || ~4.4.29"``

**Fehlerbehebung in Adobe Commerce in der Cloud-Infrastruktur:**

Führen Sie die oben genannten Befehle aus oder aktualisieren Sie auf die neueste Version der ECE-Tools (ece-tools: 2002.1.7), die am Donnerstag, 29. Juli verfügbar sein wird. Anweisungen hierzu finden Sie unter [Cloud für Adobe Commerce > ECE-Tools-Version aktualisieren](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package) in unserer Entwicklerdokumentation.

Die vollständige Fehlerbehebung wird in Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 veröffentlicht.

## Verwandtes Lesen

* GitHub: [2021-07-27 Composer Update Inkompatibler Argumenttyp: Erforderlicher Typ: int. Tatsächlicher Typ: Zeichenfolge](https://github.com/magento/magento2/issues/33595)
