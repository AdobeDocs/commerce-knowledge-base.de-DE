---
title: Abgelaufene Google-Bilddiagramme durch Bilddiagramme ersetzen
description: Die meisten Adobe Commerce-Editionen und -Versionen verwenden derzeit [Google Image Charts](https://developers.google.com/chart/image/) zum Rendern statischer Diagramme in Admin-Dashboards. Ab dem 14. März 2019 wird Google Google Image Charts nicht mehr unterstützen. Um dieses Problem zu beheben, stellen wir einen Patch bereit, um Google Image Charts durch [Image-Charts](https://www.image-charts.com/) kostenlosen Service zu ersetzen.
exl-id: f86f0bb9-8a03-471d-8696-1eba4b8acbd1
feature: Cache, Compliance
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 0%

---

# Abgelaufene Google-Bilddiagramme durch Bilddiagramme ersetzen

Die meisten Adobe Commerce-Editionen und -Versionen verwenden derzeit [Google Image Charts](https://developers.google.com/chart/image/) zum Rendern von statischen Diagrammen in Admin-Dashboards. Ab dem 14. März 2019 wird Google Google Image Charts nicht mehr unterstützen. Um dieses Problem zu beheben, stellen wir einen Patch bereit, mit dem Google Image Charts durch den kostenlosen Dienst [Image-Charts](https://www.image-charts.com/) ersetzt werden.

## Betroffene Versionen

* Adobe Commerce 1.X, alle Editionen
* Adobe Commerce 2.x, alle Editionen

>[!NOTE]
>
>Adobe Commerce On-Premise 1.14.4.1, Magento Open Source 1.9.4.1, Adobe Commerce On-Premise und Adobe Commerce on Cloud Infrastructure 2.3.2 werden dieses Diagramm-Update enthalten. Durch die Aktualisierung auf diese Versionen wird die Unterstützung für Bilddiagramme ohne zusätzliche Patches fortgesetzt.

## Problem

Am 14. März 2019 stellte Google die Unterstützung für Google Image Charts ein. Benutzer von Adobe Commerce 1.X und Adobe Commerce 2.2.X können keine statischen Diagramme anzeigen, es sei denn, sie laden den Patch herunter und wenden ihn an und ersetzen Google-Bilddiagramme durch die Image-Charts-Lösung. Angezeigte Diagramme verfügen über dasselbe Design und dieselbe Funktionalität wie Google Image Charts über den kostenlosen Kontodienst für Bilddiagramme mit der Datenschutzrichtlinie für die Einhaltung der [DSGVO](https://www.image-charts.com/data-processing-addendum.html) . Weitere Optionen finden Sie unter [Bilddiagramme](https://www.image-charts.com/).

## Lösung

Um statische Diagramme in Commerce Admin anzeigen zu können, laden Sie den von Adobe Commerce bereitgestellten Patch herunter und wenden Sie ihn an. Es ist keine zusätzliche Konfiguration erforderlich.

### Adobe Commerce vor Ort

1. Speichern Sie den Patch [Attached MAGETWO-98833\_composer\_patch-2019-04-15-04-38-57.patch](assets/MAGETWO-98833_composer_patch-2019-04-15-04-38-57.patch.zip) und laden Sie ihn in Ihr Adobe Commerce-Stammverzeichnis hoch.
1. Führen Sie den folgenden SSH-Befehl aus, nachdem Sie den Patch-Namen durch den tatsächlichen ersetzt haben:

   ```git
   patch -p1 < MAGETWO-98833_composer_patch-2019-04-15-04-38-57.patch
   ```

   Wenn der obige Befehl nicht funktioniert, versuchen Sie, `-p2` anstelle von `-p1` zu verwenden.)

1. Damit die Änderungen übernommen werden, aktualisieren Sie den Cache im Admin unter **System** > **Cache-Verwaltung**.

### Adobe Commerce auf Cloud-Infrastruktur

Bei Cloud-Händlern wird der Patch auf das nächste ECE-Tools-Update gesetzt.

### Magento 2 Source öffnen

1. Wechseln Sie zu [https://magento.com/tech-resources/download\#download291](https://magento.com/tech-resources/download#download2291).
1. Wählen Sie in der Dropdownliste **Format auswählen** die Komponentenversion aus und klicken Sie auf **Herunterladen**.
1. Laden Sie den Patch in das Stammverzeichnis von Adobe Commerce hoch.
1. Führen Sie den folgenden SSH-Befehl aus, nachdem Sie den Patch-Namen durch den tatsächlichen ersetzt haben:

   ```git
   patch -p1 < MAGETWO-98833_composer_patch-2019-04-15-04-37-48.patch
   ```

   (Wenn der obige Befehl nicht funktioniert, versuchen Sie, `-p2` anstelle von `-p1` zu verwenden.)

1. Damit die Änderungen übernommen werden, aktualisieren Sie den Cache im Admin unter **System** > **Cache-Verwaltung**.

### Adobe Commerce 1 vor Ort

Führen Sie die folgenden Schritte aus, um den Patch herunterzuladen und anzuwenden:

1. Speichern Sie den Patch [Attached MPERF-10509-EE-2019-03-13-06-32-19.diff](assets/MPERF-10509-EE-2019-03-13-06-32-19.diff.zip) und laden Sie ihn in Ihr Adobe Commerce-Stammverzeichnis hoch.
1. Führen Sie den folgenden SSH-Befehl aus:

   ```git
   patch -p1 < MPERF-10509-EE-2019-03-13-06-32-19.diff
   ```

   (Wenn der obige Befehl nicht funktioniert, versuchen Sie, `-p2` anstelle von `-p1` zu verwenden.)

1. Damit die Änderungen übernommen werden, aktualisieren Sie den Cache im Admin unter **System** > **Cache-Verwaltung**.

### Magento 1 Source öffnen

Führen Sie die folgenden Schritte aus, um den Patch herunterzuladen und anzuwenden:

1. Klicken Sie auf [**diesen Link**](https://magento.com/tech-resources/download#download2283) , um den Patch für die Admin Dashboard-Diagramme zu finden.
1. Auswählen

   ```git
   MPERF-10509.diff
   ```

   Wählen Sie in der Dropdown-Liste **Format auswählen** Ihr Format aus und klicken Sie auf Herunterladen.

1. Laden Sie die Datei in den Stammordner von Adobe Commerce hoch.
1. Führen Sie den folgenden SSH-Befehl aus:

   ```git
   patch -p1 < MPERF-10509.diff
   ```

   (Wenn der obige Befehl nicht funktioniert, versuchen Sie, `-p2` anstelle von `-p1` zu verwenden.)

1. Damit die Änderungen übernommen werden, aktualisieren Sie den Cache im Admin unter **System** > **Cache-Verwaltung**.

## Attached Files

[MAGETWO-98833_composer_patch-2019-04-15-04-38-57.patch herunterladen](assets/MAGETWO-98833_composer_patch-2019-04-15-04-38-57.patch)

[MPERF-10509-EE-2019-03-13-06-32-19.diffh herunterladen](assets/MPERF-10509-EE-2019-03-13-06-32-19.diff)
