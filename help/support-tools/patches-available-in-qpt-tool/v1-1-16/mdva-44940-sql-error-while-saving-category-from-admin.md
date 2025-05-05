---
title: 'MDVA-44940: SQL-Fehler beim Speichern der Kategorie aus dem Administrator'
description: Mit dem Patch MDVA-44940 wird das Problem behoben, dass beim Speichern einer Kategorie über den Administrator ein SQL-Fehler auftritt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 installiert ist. Die Patch-ID lautet MDVA-44940. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.
exl-id: cae6f231-3b91-441f-af56-824db0fa2d32
feature: Admin Workspace, Categories, Sales Channels
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# MDVA-44940: SQL-Fehler beim Speichern der Kategorie aus dem Administrator

Mit dem Patch MDVA-44940 wird das Problem behoben, dass beim Speichern einer Kategorie über den Administrator ein SQL-Fehler auftritt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 installiert ist. Die Patch-ID lautet MDVA-44940. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.4

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Beim Speichern einer Kategorie über den Administrator tritt ein SQL-Fehler auf.

<u>Schritte zur Reproduktion</u>:

1. Installieren von Beispieldaten.
1. Erstellen Sie eine zweite Website mit einer Store-Gruppe, die der Standardkategorie zugewiesen ist.

   * Erstellen Sie eine Store-Ansicht, die der neuen Store-Gruppe zugewiesen ist.

1. Erstellen Sie ein Lager und eine zusätzliche Quelle, die diesem Lager zugewiesen ist, sowie einen Vertriebskanal, der der zweiten Website zugewiesen ist.
1. Erstellen Sie ein Testprodukt, das der zweiten Website zugewiesen ist.
1. Gehen Sie zu **Admin** > **Katalog** > **Kategorien**, wählen Sie **Umfang** = **Zweite Website** und gehen Sie zu **Produkte in Kategorie** > **Automatische Sortierung** > Verschieben Sie nicht vorrätige Produkte nach unten und klicken Sie auf **Speichern**.

<u>Erwartete Ergebnisse</u>:

Die Kategorie wird gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Folgender Fehler tritt auf: *Beim Speichern der Kategorie ist ein Fehler aufgetreten*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) in unserer Entwicklerdokumentation.
