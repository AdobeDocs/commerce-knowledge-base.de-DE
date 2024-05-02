---
title: '[!DNL Advanced Reporting] 404-Fehler bei Adobe Commerce'
description: Dieser Artikel enthält einen Patch für das Adobe Commerce-Problem, wenn ein Händler einen 404-Fehler erhält, wenn er versucht, auf [ zuzugreifen.[!DNL Advanced Reporting]](https://experienceleague.adobe.com/docs/commerce-admin/config/general/advanced-reporting.html). Nachdem dieser Patch installiert wurde, können Benutzer auf [!DNL Advanced Reporting].
exl-id: bac61704-44fe-4bd2-b342-af90219231ef
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# [!DNL Advanced Reporting] 404-Fehler in Adobe Commerce

Dieser Artikel enthält einen Patch für das Adobe Commerce-Problem, wenn ein Händler einen 404-Fehler erhält, wenn er versucht, auf [[!DNL Advanced Reporting]](https://experienceleague.adobe.com/docs/commerce-admin/config/general/advanced-reporting.html). Nachdem dieser Patch installiert wurde, können Benutzer auf [!DNL Advanced Reporting].

Um zu überprüfen, ob dieser Patch dieses Problem lösen kann, überprüfen Sie zunächst die Protokolle mit dem folgenden Befehl:

`zgrep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz`

Wenn die Variable `Not valid cipher` -Fehler, wenden Sie den angehängten Patch an.

## Betroffene Produkte und Versionen

Adobe Commerce 2.2.6

## Problem

Ein Händler erhält einen 404-Fehler beim Versuch, auf [!DNL Advanced Reporting].

## Lösung

Um das Problem zu beheben, wenden Sie bitte den an diesen Artikel angehängten Patch an. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link: [MDVA-18980\_EE\_2.2.6\_COMPOSER\_v1 herunterladen](assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip)

## Anwenden des Pflasters

Siehe [Anwenden eines von Adobe bereitgestellten Composer-Patches](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) für Anweisungen.

## Attached files
