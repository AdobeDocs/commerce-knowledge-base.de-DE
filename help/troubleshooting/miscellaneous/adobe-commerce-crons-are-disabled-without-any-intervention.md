---
title: Adobe Commerce [!DNL crons] deaktiviert ohne Eingriff
description: Verwenden Sie diesen Artikel, um das Problem zu beheben, bei dem [!DNL crons] ohne Eingreifen deaktiviert sind.
exl-id: 5172d2ae-53ad-4db6-ae00-7b27c96911e9
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# Adobe Commerce-Kronen ohne Eingriffe deaktiviert

Dieser Artikel bietet eine Lösung für den Fall, dass [!DNL crons] ohne Eingriff deaktiviert ist.

## Betroffene Produkte und Versionen

* Adobe Commerce in der Cloud-Infrastruktur, alle [unterstützten Versionen](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Problem

Ihre [!DNL crons] sind nach der Bereitstellung deaktiviert.

<u>Zu reproduzierende Schritte</u>:

Bereitstellen.

<u>Erwartetes Ergebnis</u>:

Ihre [!DNL crons] werden ausgeführt.

<u>Tatsächliches Ergebnis</u>:

Ihre [!DNL crons] sind nach der Bereitstellung deaktiviert.

## Ursache

Ein Problem mit den [!DNL OPcache] -Einstellungen.

## Lösung

Aktualisieren Sie [!DNL ECE Tools] auf die neueste Version [2002.1.13](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package#v2002113).

## Verwandtes Lesen

* [Langsame Leistung, langsame und lange Ausführung [!DNL crons]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.html) in unserer Wissensdatenbank.
* [[!DNL Cron] Aufgaben sperren Aufgaben von anderen Gruppen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-tasks-lock-tasks-from-other-groups.html?lang=en) in unserer Support-Wissensdatenbank.
* [[!DNL Cron] Auftrag ist in unserem Support-Wissensstamm im Status &quot;Wird ausgeführt&quot;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en) stecken geblieben.
