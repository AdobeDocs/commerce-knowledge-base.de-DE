---
title: '[!DNL Advanced Reporting] 404-Fehler bei Adobe Commerce'
description: Dieser Artikel enthält einen Patch für das Adobe Commerce-Problem, wenn ein Händler einen 404-Fehler erhält, wenn er versucht, auf [[!DNL Advanced Reporting]](https://experienceleague.adobe.com/docs/commerce-admin/config/general/advanced-reporting.html) zuzugreifen. Nachdem dieser Patch installiert wurde, können Benutzer auf [!DNL Advanced Reporting] zugreifen.
exl-id: bac61704-44fe-4bd2-b342-af90219231ef
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# [!DNL Advanced Reporting] 404-Fehler bei Adobe Commerce

Dieser Artikel enthält einen Patch für das Adobe Commerce-Problem, wenn ein Händler einen 404-Fehler erhält, wenn er versucht, auf [[!DNL Advanced Reporting]](https://experienceleague.adobe.com/docs/commerce-admin/config/general/advanced-reporting.html) zuzugreifen. Nachdem dieser Patch installiert wurde, können Benutzer auf [!DNL Advanced Reporting] zugreifen.

Um zu überprüfen, ob dieser Patch dieses Problem lösen kann, überprüfen Sie zunächst die Protokolle mit dem folgenden Befehl:

`zgrep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz`

Wenn der Fehler `Not valid cipher` angezeigt wird, wenden Sie den angehängten Patch an.

## Betroffene Produkte und Versionen

Adobe Commerce 2.2.6

## Problem

Ein Händler erhält einen 404-Fehler, wenn er versucht, auf [!DNL Advanced Reporting] zuzugreifen.

## Lösung

Um das Problem zu beheben, wenden Sie bitte den an diesen Artikel angehängten Patch an. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link: [MDVA-18980\_EE\_2.2.6\_COMPOSER\_v1](assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip) herunterladen

## Anwenden des Pflasters

Anweisungen finden Sie unter [Anwenden eines von Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) bereitgestellten Composer-Patches.

## Attached files
