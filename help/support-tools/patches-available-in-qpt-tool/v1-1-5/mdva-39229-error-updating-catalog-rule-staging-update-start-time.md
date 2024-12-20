---
title: 'MDVA-39229: Fehler nach Aktualisierung der Staging-Update-Startzeit der Katalogregel'
description: Der Patch MDVA-39229 behebt das Problem, bei dem Benutzer nach der Aktualisierung der Startzeit der Staging-Aktualisierung der Katalogregel einen Fehler erhalten. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.5 installiert ist. Die Patch-ID lautet MDVA-39229. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
exl-id: b9a203af-693d-4253-877b-591ae5f388d3
feature: Catalog Management, Staging
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# MDVA-39229: Fehler nach Aktualisierung der Staging-Update-Startzeit der Katalogregel

Der Patch MDVA-39229 behebt das Problem, bei dem Benutzer nach der Aktualisierung der Startzeit der Staging-Aktualisierung der Katalogregel einen Fehler erhalten. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.5 installiert ist. Die Patch-ID lautet MDVA-39229. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Benutzer erhalten nach der Aktualisierung der Startzeit der Aktualisierung der Katalogregel-Staging einen Fehler.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine Katalogpreisregel.
1. Erstellen Sie eine Staging-Aktualisierung und führen Sie sie aus.
1. Führen Sie die Abfrage aus und überprüfen Sie, ob das Staging-Flag erstellt wurde.


   `select * from flag;`


1. Erstellen Sie ein neues Staging-Update, das nach fünf Minuten gestartet werden soll.
1. Öffnen Sie **Inhalt** > **Staging** > **Dashboard** > **Neues Update** und verzögern Sie die Startzeit um eine Minute.
1. Warten Sie sechs Minuten!
1. Führen Sie cron aus.

<u>Erwartete Ergebnisse</u>:

Die Startzeit der Aktualisierung wird geändert und die Aktualisierung wird übernommen. Die alte Aktualisierung wird aus der Tabelle `staging_update` gelöscht.

<u>Tatsächliche Ergebnisse</u>:

Benutzer erhalten den folgenden Fehler:

*report.ERROR: Staging_synchronize_entity_period für Cron-Auftrag hat einen Fehler: Das aktive Update kann nicht gelöscht werden.*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) verfügbare Patches.
