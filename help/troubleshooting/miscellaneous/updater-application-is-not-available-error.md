---
title: Fehler „Aktualisierungsanwendung ist nicht verfügbar“
description: In diesem Artikel wird die Lösung des Problems „Aktualisierungsanwendung ist nicht verfügbar“ beschrieben, das auftreten kann, wenn Sie versuchen, Adobe Commerce On-Premise mithilfe des Websetup-Assistenten zu aktualisieren/installieren.
exl-id: 85e55ed8-0bc9-4378-b722-46be98ce2638
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# Fehler „Aktualisierungsanwendung ist nicht verfügbar“

In diesem Artikel wird die Lösung des Problems „Aktualisierungsanwendung ist nicht verfügbar“ beschrieben, das auftreten kann, wenn Sie versuchen, Adobe Commerce On-Premise mithilfe des Websetup-Assistenten zu aktualisieren/installieren.

## Problem

Die folgende Meldung wird bei der Bereitschaftsprüfung angezeigt:

![screen_shot_2019-08-29_at_1.39.12_PM.png](assets/Screen_Shot_2019-08-29_at_1.39.12_PM.png)

## Betroffene Produkte/Versionen

* Adobe Commerce On-Premises 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x


## Lösung

Um dieses Problem zu beheben, überprüfen Sie, ob es ein `<magento_root>/update`-Verzeichnis gibt, das Dateien und Unterverzeichnisse enthält. Andernfalls finden Sie weitere Informationen unter [Einrichten des ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/updater-application-is-not-available-error)) in unserer Entwicklerdokumentation.
