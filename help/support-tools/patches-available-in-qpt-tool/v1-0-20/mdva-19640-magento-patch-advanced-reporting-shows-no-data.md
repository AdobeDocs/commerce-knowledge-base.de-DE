---
title: "MDVA-19640: Erweiterte Berichterstellung zeigt keine Daten an"
description: Der Patch MDVA-19640 behebt das Problem, wenn die erweiterte Berichterstellung keine Daten anzeigt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 installiert ist. Die Patch-ID lautet MDVA-19640. Bitte beachten Sie, dass es derzeit keinen Plan gibt, dieses Problem in zukünftigen Versionen zu beheben.
exl-id: 6df70f10-5d34-4540-b2ae-3a0be32f2bfd
feature: Commerce Intelligence
role: Admin
source-git-commit: 2914a110444898f78d2ed43ea96a9c5f6e70229f
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# MDVA-19640: Erweiterte Berichterstellung zeigt keine Daten an

Der Patch MDVA-19640 behebt das Problem, wenn die erweiterte Berichterstellung keine Daten anzeigt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 installiert ist. Die Patch-ID lautet MDVA-19640. Bitte beachten Sie, dass es derzeit keinen Plan gibt, dieses Problem in zukünftigen Versionen zu beheben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.3.0

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.1 - 2.4.6-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Wechseln Sie im Admin zu **Berichte** > **Business Intelligence** und wählen Sie **Fortschrittliche Berichterstellung** aus.
1. Anzeigen der Seite **Erweiterte Berichterstellung** .

<u>Erwartete Ergebnisse</u>:

Der Bericht &quot;Fortschrittliche Berichterstellung&quot;enthält wie erwartet Informationen.

<u>Tatsächliche Ergebnisse</u>:

Der Bericht &quot;Fortschrittliche Berichterstellung&quot;zeigt keine Daten an.

<u>Zusätzliche Schritte, die nach der Patch-Installation erforderlich sind</u>:

Die folgende SQL-Abfrage muss angewendet werden, um Datensätze in der Tabelle cron_schedule zu aktualisieren:
`UPDATE core_config_data SET path = REPLACE(path, "crontab/default/jobs/analytics", "crontab/analytics/jobs/analytics") WHERE path LIKE "crontab/default/jobs/analytics%";`

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
