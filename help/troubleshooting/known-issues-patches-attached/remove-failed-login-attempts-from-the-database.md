---
title: Fehlgeschlagene Anmeldeversuche aus der Datenbank entfernen
description: In diesem Artikel wird erläutert, wie Sie bereits vorhandene fehlgeschlagene Anmeldedaten aus der lokalen Adobe Commerce-Datenbank und Adobe Commerce in der Cloud-Infrastrukturdatenbank entfernen können. Für die Versionen 2.2.10+ und 2.3.3+ müssen Sie nur das angehängte Skript ausführen. Bei älteren Versionen 2.3.0-2.3.2-p2 müssen Sie einen Patch anwenden, um die Protokollierung zu beenden und das angehängte Skript auszuführen, um bereits vorhandene fehlgeschlagene Anmeldedaten zu entfernen.
exl-id: 0d7e3674-3563-414f-86a2-297eb8104099
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 0%

---

# Fehlgeschlagene Anmeldeversuche aus der Datenbank entfernen

>[!NOTE]
>
>Dieser Artikel wurde am 13. April 2020 mit einem neuen Skript namens DB\_CLEANUP\_SCRIPT\_v2 aktualisiert. Verwenden Sie das angehängte DB\_CLEANUP\_SCRIPT\_v2 Skript, um bereits vorhandene fehlgeschlagene Anmeldedaten in zusätzlichen Tabellen zu löschen. Sie müssen DB\_CLEANUP\_SCRIPT\_v2 verwenden, auch wenn Sie zuvor DB\_CLEANUP\_SCRIPT\_v1 ausgeführt haben, um sicherzustellen, dass zusätzliche Tabellen bereinigt werden.

In diesem Artikel wird erläutert, wie Sie bereits vorhandene fehlgeschlagene Anmeldedaten aus der lokalen Adobe Commerce-Datenbank und Adobe Commerce in der Cloud-Infrastrukturdatenbank entfernen können. Für die Versionen 2.2.10+ und 2.3.3+ müssen Sie nur das angehängte Skript ausführen. Bei älteren Versionen 2.3.0-2.3.2-p2 müssen Sie einen Patch anwenden, um die Protokollierung zu beenden und das angehängte Skript auszuführen, um bereits vorhandene fehlgeschlagene Anmeldedaten zu entfernen.

## **Betroffene Produkte und Versionen**

* Dieses Problem betrifft die Magento Open Source, Adobe Commerce vor Ort und Adobe Commerce in der Cloud-Infrastruktur 2.2.x, 2.3.x und früheren Versionen.
* Adobe Commerce 1.x-Implementierungen sind nicht betroffen.

## Problem

2019 wurde Adobe Commerce ein Fehler gemeldet, durch den fehlgeschlagene Anmeldeversuche in einer Datenbank in Adobe Commerce 2.3.x und 2.2.x protokolliert werden konnten. Als Antwort darauf hat Adobe Commerce in Adobe Commerce 2.3.3 und 2.2.10 (veröffentlicht im Oktober 2019) eine Korrektur für dieses Problem eingefügt. Während die Fehlerbehebung für diesen Fehler die Protokollierung fehlgeschlagener Anmeldeversuche stoppte, sind möglicherweise noch Informationen vorhanden, die vor der Aktualisierung auf diese aktuellen Versionen erfasst wurden. Diese neueste Fehlerbehebung löscht die Informationen zu Anmeldeversuchen, die zuvor protokolliert wurden (falls vorhanden).   CVE-2019-8118 wird beschrieben und verfolgt in [Häufige Schwachstellen und Risikopositionen](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-8118).

## Lösung

Ob Sie das angehängte Skript und den Patch oder nur das Skript verwenden müssen, hängt von Ihrer Adobe Commerce-Version ab:

**Adobe Commerce- und Magento Open Source-Versionen 2.3.0-2.3.2-p2**

Für diese Versionen müssen Sie den Patch anwenden und das angehängte Datenbankbereinigungsskript ausführen, um die fortlaufende Protokollierung zu beenden und Protokolle zu eliminieren.

1. Führen Sie den Composer-Patch aus, um die Protokollierung zu beenden. Dieser Patch ist an den Artikel angehängt. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link [CLEANUP\_PATCH\_COMPOSER\_2.3.2.patch](assets/CLEANUP_PATCH_COMPOSER_2.3.2.patch.zip). Eine Anleitung zum Auftragen des Pflasters finden Sie unter [Anwenden eines von Adobe Commerce bereitgestellten Komponentenpatches](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in unserer Wissensdatenbank.

1. Führen Sie nun das Skript aus, um die Datenbank der bereits vorhandenen fehlgeschlagenen Anmeldeversuche zu bereinigen. Dieses Skript ist an den Artikel angehängt. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link [DB\_CLEANUP\_SCRIPT\_v2.php](assets/DB_CLEANUP_SCRIPT_v2.php.zip).

Weitere Informationen finden Sie unter [**Ausführen des Skripts**](/help/troubleshooting/known-issues-patches-attached/remove-failed-login-attempts-from-the-database.md#run_script) Anweisungen.

**Adobe Commerce- und Magento Open Source-Versionen 2.3.3 und höher/2.2.10 und höher**<br>
Führen Sie nur für diese Versionen das folgende Skript aus, um alte Protokolle zu löschen (die Protokollierung wurde zuvor für diese Versionen über eine im Oktober 2019 veröffentlichte Fehlerbehebung beendet). Dieses Skript ist an den Artikel angehängt. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link [DB\_CLEANUP\_SCRIPT\_v2.php](assets/DB_CLEANUP_SCRIPT_v2.php.zip).

Weitere Informationen finden Sie unter [**Ausführen des Skripts**](/help/troubleshooting/known-issues-patches-attached/remove-failed-login-attempts-from-the-database.md#run_script) in unserer Support-Wissensdatenbank, für Anweisungen.

**Ausführen des Skripts**

Befolgen Sie die folgenden Anweisungen, um das Skript auszuführen:

1. Put `DB_CLEANUP_SCRIPT_v2.php` im Stammverzeichnis der Adobe Commerce- oder Magento Open Source-Installation (im selben Ordner wie die App, die `app/bootstrap.php`).
1. Führen Sie diesen Befehl im Terminal aus: `php DB_CLEANUP_SCRIPT_v2.php` und der Bereinigungsprozess der Datenbank gestartet wird.

Wenn beim Ausführen des Skripts Probleme auftreten, wenden Sie sich an [Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) oder per E-Mail an uns senden [security@magento.com](mailto:security@magento.com).

**Attached files**

[CLEANUP\_PATCH\_COMPOSER\_2.3.2.patch](assets/CLEANUP_PATCH_COMPOSER_2.3.2.patch.zip)

[DB\_CLEANUP\_SCRIPT\_v2.php](assets/DB_CLEANUP_SCRIPT_v2.php.zip)
