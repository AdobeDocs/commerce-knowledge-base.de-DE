---
title: Mehrere für denselben Zeitraum geplante Cron-Aufträge
description: Dieser Artikel enthält einen Patch für ein bekanntes Adobe Commerce 2.2.2-Problem im Zusammenhang mit der gleichzeitigen Ausführung mehrerer Cron-Aufträge, nachdem die Zeitvariablen für bestimmte Aufgaben in Commerce Admin bearbeitet wurden.
exl-id: a3c1fe77-ed4c-43b5-8d6f-e5c549096c73
feature: Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 0%

---

# Mehrere für denselben Zeitraum geplante Cron-Aufträge

Dieser Artikel enthält einen Patch für ein bekanntes Adobe Commerce 2.2.2-Problem im Zusammenhang mit der gleichzeitigen Ausführung mehrerer Cron-Aufträge, nachdem die Zeitvariablen für bestimmte Aufgaben in Commerce Admin bearbeitet wurden.

## Problem

Wenn cron so konfiguriert ist, dass es jede Minute ausgeführt wird, wenn Sie Zeitvariablen für drei geplante Aufgaben in Admin bearbeiten, wird die `cron_schedule` Datenbanktabelle zeigt Gruppen mehrerer Aufgaben an, die zur gleichen Zeit ausgeführt werden sollen.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie in Commerce Admin zu **Stores** > Einstellungen > **Konfiguration** > **ERWEITERT** > **System** > **Cron (Scheduled Tasks)** > **Cron-Konfigurationsoptionen für Gruppen: Standard.**
1. Konfigurieren Sie die folgenden Optionen:
   * **Verlaufsbereinigung alle**: Löschen Sie die **System verwenden** und legen Sie *1440*.
   * **Lebensdauer des Erfolgsverlaufs**: Löschen Sie die **System verwenden** und legen Sie *1440*.
   * **Lebensdauer des Fehlerverlaufs**: Löschen Sie die **System verwenden** und legen Sie *1440*.

1. Klicks **Konfiguration speichern**.
1. Führen Sie in SSH den `crontab -e` Befehl.
1. Legen Sie cron so fest, dass es jede Minute ausgeführt wird.
1. Öffnen Sie drei Terminal-Registerkarten/-Fenster.
1. Navigieren Sie zur Adobe Commerce `root/base/project` in jedem Terminal-Fenster.
1. Führen Sie in jedem Tab/Fenster den folgenden Befehl aus:

   ```bash
   bin/magento cache:flush && bin/magento cron:run && bin/magento cache:flush && bin/magento cron:run
   ```

1. Gehen Sie zu MySQL und führen Sie die folgende Abfrage aus:

   ```sql
   SELECT job_code, scheduled_at, count as count FROM cron_schedule GROUP BY job_code, scheduled_at HAVING count > 1 ORDER BY scheduled_at;
   ```

1. Siehe Gruppen von Aufgaben, deren Ausführung geplant ist.

<u>Erwartetes Ergebnis</u>: Ein Cron `job_code` sollte für den bestimmten Zeitraum geplant werden.

<u>Tatsächliches Ergebnis</u>: Es sind mehrere Cron-Aufträge für denselben Zeitraum geplant.

## Lösung

Für Adobe Commerce für Cloud-Infrastrukturhändler: [Aktualisierung der ECE-Instrumente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html) löst das Problem.

Vor Ort tätige Adobe Commerce-Händler sollten zur Lösung des Problems einen der beigefügten Patches anwenden.

## Patches

Die Patches sind diesem Artikel beigefügt. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf einen der folgenden Links:

* [MDVA-11304\_EE\_2.1.4\_COMPOSER\_v1.patch herunterladen](assets/MDVA-11304_EE_2.1.4_COMPOSER_v1.patch.zip)
* [MDVA-11304\_EE\_2.1.5\_COMPOSER\_v1.patch herunterladen](assets/MDVA-11304_EE_2.1.5_COMPOSER_v1.patch.zip)
* [MDVA-11304\_EE\_2.1.13\_COMPOSER\_v1.patch herunterladen](assets/MDVA-11304_EE_2.1.13_COMPOSER_v1.patch.zip)
* [MDVA-11304\_EE\_2.1.14\_COMPOSER\_v1.patch herunterladen](assets/MDVA-11304_EE_2.1.14_COMPOSER_v1.patch.zip)
* [MDVA-11304\_EE\_2.2.0\_COMPOSER\_v1.patch herunterladen](assets/MDVA-11304_EE_2.2.0_COMPOSER_v1.patch.zip)
* [MDVA-11304\_EE\_2.2.2\_COMPOSER\_v1.patch herunterladen](assets/MDVA-11304_EE_2.2.2_COMPOSER_v1.patch.zip)
* [MDVA-11304\_EE\_2.2.4\_COMPOSER\_v1.patch herunterladen](assets/MDVA-11304_EE_2.2.4_COMPOSER_v1.patch.zip)

### Kompatible Adobe Commerce-Versionen

Die Patches wurden für eine bestimmte Version erstellt, die im Patch-Dateinamen vermerkt ist. Beispielsweise wurde MDVA-11304\_EE\_2.2.4\_COMPOSER\_v1.patch für Adobe Commerce 2.2.4 erstellt und ist der beste Patch für diese Version.

Die Patches sind auch mit den folgenden Versionen kompatibel:

* Für Adobe Commerce vor Ort 2.1.0-2.1.4: [MDVA-11304\_EE\_2.1.4\_COMPOSER\_v1.patch herunterladen](assets/MDVA-11304_EE_2.1.4_COMPOSER_v1.patch.zip) Der Patch ist auch mit den folgenden Adobe Commerce-Versionen und -Editionen kompatibel (löst das Problem jedoch möglicherweise nicht):
   * Adobe Commerce auf Cloud-Infrastruktur 2.1.0-2.1.4
* Für Adobe Commerce vor Ort 2.1.5-2.1.12: [MDVA-11304\_EE\_2.1.5\_COMPOSER\_v1.patch herunterladen](assets/MDVA-11304_EE_2.1.5_COMPOSER_v1.patch.zip) Der Patch ist auch mit den folgenden Adobe Commerce-Versionen und -Editionen kompatibel (löst das Problem jedoch möglicherweise nicht):
   * Adobe Commerce auf Cloud-Infrastruktur 2.1.5-2.1.12
* Für Adobe Commerce auf Cloud-Infrastruktur 2.1.13: [MDVA-11304\_EE\_2.1.13\_COMPOSER\_v1.patch herunterladen](assets/MDVA-11304_EE_2.1.13_COMPOSER_v1.patch.zip)
* Für Adobe Commerce vor Ort 2.1.14-2.1.17: [MDVA-11304\_EE\_2.1.14\_COMPOSER\_v1.patch herunterladen](assets/MDVA-11304_EE_2.1.14_COMPOSER_v1.patch.zip) Der Patch ist auch mit den folgenden Adobe Commerce-Versionen und -Editionen kompatibel (löst das Problem jedoch möglicherweise nicht):
   * Adobe Commerce vor Ort 2.1.18
   * Adobe Commerce auf Cloud-Infrastruktur 2.1.14-2.1.18
* Für Adobe Commerce vor Ort 2.2.0-2.2.1: [MDVA-11304\_EE\_2.2.0\_COMPOSER\_v1.patch herunterladen](assets/MDVA-11304_EE_2.2.0_COMPOSER_v1.patch.zip) Der Patch ist auch mit den folgenden Adobe Commerce-Versionen und -Editionen kompatibel (löst das Problem jedoch möglicherweise nicht):
   * Adobe Commerce auf Cloud-Infrastruktur 2.2.0-2.2.1
* Für Adobe Commerce vor Ort 2.2.0-2.2.3: [MDVA-11304\_EE\_2.2.2\_COMPOSER\_v1.patch herunterladen](assets/MDVA-11304_EE_2.2.2_COMPOSER_v1.patch.zip) Der Patch ist auch mit den folgenden Adobe Commerce-Versionen und -Editionen kompatibel (löst das Problem jedoch möglicherweise nicht):
   * Adobe Commerce auf Cloud-Infrastruktur 2.2.0-2.2.3
* Für Adobe Commerce vor Ort 2.2.4: [MDVA-11304\_EE\_2.2.4\_COMPOSER\_v1.patch herunterladen](assets/MDVA-11304_EE_2.2.4_COMPOSER_v1.patch.zip) Der Patch ist auch mit den folgenden Adobe Commerce-Versionen und -Editionen kompatibel (löst das Problem jedoch möglicherweise nicht):
   * Adobe Commerce in Cloud-Infrastruktur 2.2.4

## Anwenden des Pflasters

Siehe [Anwenden eines von Adobe Commerce bereitgestellten Komponentenpatches](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in unserer Support-Wissensdatenbank, für Anweisungen.

## Attached Files
