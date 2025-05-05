---
title: 'MDVA-39229: Fehler nach der Aktualisierung der Startzeit der Staging-Aktualisierung der Katalogregel'
description: Mit dem Patch MDVA-39229 wird das Problem behoben, dass Benutzende nach der Aktualisierung der Startzeit der Staging-Aktualisierung der Katalogregel einen Fehler erhalten. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.5 installiert ist. Die Patch-ID lautet MDVA-39229. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
exl-id: b9a203af-693d-4253-877b-591ae5f388d3
feature: Catalog Management, Staging
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# MDVA-39229: Fehler nach der Aktualisierung der Startzeit der Staging-Aktualisierung der Katalogregel

Mit dem Patch MDVA-39229 wird das Problem behoben, dass Benutzende nach der Aktualisierung der Startzeit der Staging-Aktualisierung der Katalogregel einen Fehler erhalten. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.5 installiert ist. Die Patch-ID lautet MDVA-39229. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Benutzende erhalten eine Fehlermeldung, nachdem sie die Startzeit der Staging-Aktualisierung der Katalogregel aktualisiert haben.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine Katalogpreisregel.
1. Erstellen Sie eine beliebige Staging-Aktualisierung und führen Sie sie aus.
1. Führen Sie die Abfrage aus und überprüfen Sie, ob das Staging-Flag erstellt wurde.


   `select * from flag;`


1. Erstellen Sie ein neues Staging-Update, das nach fünf Minuten gestartet wird.
1. Öffnen Sie **Inhalt** > **Staging** > **Dashboard** > **Neues Update** und verzögern Sie die Startzeit um eine Minute.
1. Warte sechs Minuten.
1. Cron ausführen.

<u>Erwartete Ergebnisse</u>:

Die Startzeit der Aktualisierung wird geändert und die Aktualisierung wird angewendet. Die alte Aktualisierung wird aus der `staging_update` gelöscht.

<u>Tatsächliche Ergebnisse</u>:

Benutzende erhalten die folgende Fehlermeldung:

*report.ERROR: Cron Job staging_synchronize_entities_period hat einen Fehler: Die aktive Aktualisierung kann nicht gelöscht werden.*

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [Patches in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
