---
title: Unbekanntes Modul Magento_BundleSampleData
description: Dieser Artikel enthält eine Fehlerbehebung für den unbekannten Modulfehler während der Installation von Adobe Commerce.
exl-id: c927bc8f-d70b-4305-87c1-223001212555
feature: Extensions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---

# Unbekanntes Modul Magento_BundleSampleData

Dieser Artikel enthält eine Fehlerbehebung für den unbekannten Modulfehler während der Installation von Adobe Commerce.

## Problem {#details}

Während der Installation wird eine Meldung ähnlich der folgenden angezeigt:

```text
[ERROR] exception 'LogicException' with message 'Unknown module in the requested list: 'Magento_BundleSampleData''
```

## Lösung {#solution}

Versuchen Sie jeden der folgenden Schritte einzeln und versuchen Sie dann erneut, Ihre Installation durchzuführen.

1. Führen Sie den Web-Setup-Assistenten aus. Module werden unter **Erweiterte Modulkonfigurationen** aufgeführt. Um das Modul **Magento\_BundleSampleData** zu deaktivieren, deaktivieren Sie das Kontrollkästchen **Magento\_BundleSampleData** , wie in der folgenden Abbildung dargestellt.

   ![tshooting_bundlesampledata.png](assets/tshoot_bundlesampledata.png)

1. Löschen Sie den gesamten Browserverlauf und alle Daten aus Ihrem Webbrowser.
1. Wenn Sie über Chrome verfügen, löschen Sie alle Browserdaten, die mit Ihrer Site verbunden sind.  Navigieren Sie zu **Einstellungen** > **Erweiterte Optionen** > **Datenschutz** > **Inhaltseinstellungen** > **Alle Cookies und Site-Daten**. Klicken Sie in der Spalte &quot;Site&quot;auf die Adresse Ihres Adobe Commerce-Servers und klicken Sie auf **Alle entfernen**.
