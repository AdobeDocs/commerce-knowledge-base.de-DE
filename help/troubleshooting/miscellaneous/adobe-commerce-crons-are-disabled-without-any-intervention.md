---
title: Adobe Commerce [!DNL crons] deaktiviert ohne Intervention
description: Verwenden Sie diesen Artikel, um das Problem zu beheben, bei dem [!DNL crons] sind ohne Eingriffe deaktiviert.
exl-id: 5172d2ae-53ad-4db6-ae00-7b27c96911e9
source-git-commit: 9cd7cabc37c0f290c41f790b0fb06177c3156d48
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# Adobe Commerce-Kronen ohne Eingriffe deaktiviert

Dieser Artikel bietet eine Lösung für den Zeitpunkt [!DNL crons] sind ohne Eingriffe deaktiviert.

## Betroffene Produkte und Versionen

* Adobe Commerce in der Cloud-Infrastruktur, alle [unterstützte Versionen](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Problem

Ihre [!DNL crons] nach der Bereitstellung deaktiviert werden.

<u>Zu reproduzierende Schritte</u>:

Bereitstellen.

<u>Erwartetes Ergebnis</u>:

Ihre [!DNL crons] laufen.

<u>Tatsächliches Ergebnis</u>:

Ihre [!DNL crons] nach der Bereitstellung deaktiviert werden.

## Ursache

Ein Problem mit der [!DNL OPcache] -Einstellungen.

## Lösung

Upgrade [!DNL ECE Tools] auf die neueste Version [2002.1.13](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html#v2002113).

## Verwandtes Lesen

* [Langsame Leistung, Langsamkeit und Langsamkeit [!DNL crons]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.html) in unserer Wissensdatenbank.
* [[!DNL Cron] Aufgaben sperren Aufgaben von anderen Gruppen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-tasks-lock-tasks-from-other-groups.html?lang=en) in unserer Wissensdatenbank.
* [[!DNL Cron] Auftrag ist im Status &quot;Wird ausgeführt&quot;stecken](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en) in unserer Wissensdatenbank.
