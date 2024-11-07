---
title: Fehler "Update application not available"
description: In diesem Artikel wird die Lösung für das Problem "Update-Anwendung ist nicht verfügbar"beschrieben, mit der Sie möglicherweise konfrontiert sind, wenn Sie versuchen, Adobe Commerce lokal mit dem Web-Setup-Assistenten zu aktualisieren/zu installieren.
exl-id: 85e55ed8-0bc9-4378-b722-46be98ce2638
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# Fehler &quot;Aktualisierungsanwendung ist nicht verfügbar&quot;

In diesem Artikel wird die Lösung für das Problem &quot;Update-Anwendung ist nicht verfügbar&quot;beschrieben, mit der Sie möglicherweise konfrontiert sind, wenn Sie versuchen, Adobe Commerce lokal mit dem Web-Setup-Assistenten zu aktualisieren/zu installieren.

## Problem

Die folgende Meldung wird in der Bereitschaftsprüfung angezeigt:

![screen_shot_2019-08-29_at_1.39.12_PM.png](assets/Screen_Shot_2019-08-29_at_1.39.12_PM.png)

## Betroffene Produkte/Versionen

* Adobe Commerce lokal 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x


## Lösung

Um dieses Problem zu beheben, überprüfen Sie, ob ein &quot;`<magento_root>/update`&quot;-Ordner vorhanden ist, der Dateien und Unterverzeichnisse enthält. Weitere Informationen finden Sie unter [Einrichten des Aktualisierungsdienstes](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/updater-application-is-not-available-error) in unserer Entwicklerdokumentation.
