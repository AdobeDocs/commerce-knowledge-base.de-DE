---
title: Unbekanntes Modul Magento_BundleSampleData
description: Dieser Artikel enthält eine Fehlerbehebung für den Fehler „Unbekanntes Modul“ bei der Installation von Adobe Commerce.
exl-id: c927bc8f-d70b-4305-87c1-223001212555
feature: Extensions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---

# Unbekanntes Modul Magento_BundleSampleData

Dieser Artikel enthält eine Fehlerbehebung für den Fehler „Unbekanntes Modul“ bei der Installation von Adobe Commerce.

## Problem {#details}

Während der Installation wird eine Meldung ähnlich der folgenden angezeigt:

```text
[ERROR] exception 'LogicException' with message 'Unknown module in the requested list: 'Magento_BundleSampleData''
```

## Lösung {#solution}

Führen Sie die folgenden Schritte einzeln aus, und wiederholen Sie dann die Installation.

1. Ausführen des Websetup-Assistenten. Die Module werden unter **Erweiterte Modulkonfigurationen** aufgeführt. Um das Modul **Magento\_BundleSampleData** zu deaktivieren, deaktivieren Sie das Kontrollkästchen **Magento\_BundleSampleData**, wie in der folgenden Abbildung dargestellt.

   ![tshot_bundlesampledata.png](assets/tshoot_bundlesampledata.png)

1. Löschen Sie den gesamten Browser-Verlauf und alle Daten aus Ihrem Webbrowser.
1. Wenn Sie über Chrome verfügen, löschen Sie alle Browser-Daten im Zusammenhang mit Ihrer Site.  Gehen Sie zu **Einstellungen** > **Erweiterte Optionen** > **Datenschutz** > **Inhaltseinstellungen** > **Alle Cookies und Website-Daten**. Klicken Sie in der Spalte Site auf die Adresse Ihres Adobe Commerce-Servers und dann auf **Alle entfernen**.
