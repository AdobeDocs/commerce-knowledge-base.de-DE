---
title: "Composer-Update schlägt in Adobe Commerce fehl: Inkompatibler Argumenttyp"
description: Dieser Artikel bietet eine Lösung für den Fall, dass die Implementierung blockiert ist, da es ein Problem mit der Code-Kompilierung gibt. Dieses Problem wird durch eine neue Version der Abhängigkeit von symfony/console verursacht (4.4.27, 4.4.28).
exl-id: ba2dd229-29f6-43e2-9467-8bd1bf59e6ef
feature: Console
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# Komponentenaktualisierung schlägt in Adobe Commerce fehl: Inkompatibler Argumenttyp

>[!NOTE]
>
>Dieses Problem wurde in der neuesten symfony Version 4.4.29 behoben.

Dieser Artikel bietet eine Lösung für den Fall, dass die Implementierung blockiert ist, da es ein Problem mit der Code-Kompilierung gibt. Dieses Problem wird durch eine neue Version der Abhängigkeit von symfony/console verursacht (4.4.27, 4.4.28).

## Betroffene Produkte und Versionen

* Adobe Commerce (alle Bereitstellungsmethoden) und Magento Open Source:
   * 2.4.0, 2.4.0-p1, 2.4.1, 2.4.1-p1, 2.4.2, 2.4.2-p1, 2.4.2-p2, 2.4.3
   * 2.3.5, 2.3.5-p1, 2.3.5-p2, 2.3.6, 2.3.6-p1, 2.3.7, 2.3.7-p1
* symfony/console dependency (4.4.27, 4.4.28).

## Problem

Eine neue Version der Abhängigkeit von symfony/console (4.4.27, 4.4.28) führt dazu, dass der Prozess der Abhängigkeitskompilierung fehlschlägt.

<u>Zu reproduzierende Schritte</u>:

Wenn Sie Adobe Commerce installieren oder aktualisieren oder das Composer-Update ausführen, schlägt die Ausführung mit der folgenden Fehlermeldung fehl:
*Inkompatibler Argumenttyp: Erforderlicher Typ: int. Tatsächlicher Typ: string*

## Ursache

Das Problem wird durch die Inkompatibilität des Adobe Commerce-Core-Codes mit der neuesten Abhängigkeiten von &quot;symfony/console&quot;verursacht, die in den Versionen 4.4.27 und 4.4.28 veröffentlicht wurden.

## Lösung

Das Problem wird automatisch behoben, sobald eine neue symfony/console-Version 4.2.29 veröffentlicht wird (voraussichtlich im August 2021).

**Fehlerbehebung bei Adobe Commerce On-Premise:**

Adobe Commerce On-Premise 2.4.x

Führen Sie den folgenden Befehl im CLI/Terminal aus:

``composer require symfony/console:">=4.4.0 <4.4.27 || ~4.4.29"``

Alle Vor-Ort-Händler von Adobe Commerce 2.3.5 und höher sollten den folgenden CLI-Befehl ausführen:

``composer require symfony/console:"~4.1.0||~4.2.0||~4.3.0||>=4.4.0 <4.4.27 || ~4.4.29"``

**Fehlerbehebung in Adobe Commerce in der Cloud-Infrastruktur:**

Führen Sie die oben genannten Befehle aus oder aktualisieren Sie auf die neueste Version der ECE-Tools (ece-tools: 2002.1.7), die am Donnerstag, den 29. Juli verfügbar sein wird. Anweisungen hierzu finden Sie in unserer Entwicklerdokumentation unter [Cloud für Adobe Commerce > Aktualisierung der ece-tools-Version](https://devdocs.magento.com/cloud/project/ece-tools-update.html) .

Die vollständige Fehlerbehebung wird in Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 veröffentlicht.

## Verwandtes Lesen

* GitHub: [2021-07-27 Composer-Update Inkompatibler Argumenttyp: Erforderlicher Typ: int. Tatsächlicher Typ: string](https://github.com/magento/magento2/issues/33595)
