---
title: Adobe Commerce [!DNL crons] ohne Eingriff deaktiviert
description: Verwenden Sie diesen Artikel, um das Problem zu beheben, dass [!DNL crons] ohne Eingreifen deaktiviert werden.
exl-id: 5172d2ae-53ad-4db6-ae00-7b27c96911e9
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 0%
---
# Adobe Commerce Crons ohne Eingreifen deaktiviert

Dieser Artikel bietet eine Lösung für den Fall, dass [!DNL crons] ohne Eingriff deaktiviert werden.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur, alle [unterstützten Versionen](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Problem

Ihre [!DNL crons] sind nach der Bereitstellung deaktiviert.

<u>Schritte zur Reproduktion</u>:

Bereitstellen.

<u>Erwartetes Ergebnis</u>:

Ihre [!DNL crons] laufen.

<u>Tatsächliches </u>:

Ihre [!DNL crons] sind nach der Bereitstellung deaktiviert.

## Ursache

Ein Problem mit den [!DNL OPcache].

## Lösung

Aktualisieren Sie [!DNL ECE Tools] auf die neueste Version [2002.1.](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package#v2002113).

## Verwandtes Lesen

* [Langsame Leistung, langsamer und langer Betrieb [!DNL crons]](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-42802) in unserer Support-Wissensdatenbank.
* [[!DNL Cron] Aufgaben sperren Aufgaben von anderen Gruppen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-tasks-lock-tasks-from-other-groups.html?lang=en) in unserer Support-Wissensdatenbank.
* [[!DNL Cron] Der Vorgang ist in unserer Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en)Wissensdatenbank im Status „Läuft“ festgefahren.
