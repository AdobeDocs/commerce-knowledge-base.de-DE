---
title: 'ACSD-48417: SQL-Fehler nach der Erstellung einer Zeitplanänderung'
description: Wenden Sie den Patch ACSD-48417 an, um das Adobe Commerce-Problem zu beheben, bei dem nach dem Erstellen einer Produktplanänderung und dem Speichern eines anderen Produkts ein SQL-Fehler angezeigt wird.
exl-id: 2bbf3bb5-dec8-43b3-81f1-be0dc53d1f46
feature: Storage
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# ACSD-48417: SQL-Fehler nach der Erstellung einer Zeitplanänderung

Der Patch ACSD-48417 behebt das Problem, dass nach dem Erstellen einer Zeitplanänderung für ein Produkt und dem Speichern eines anderen Produkts ein SQL-Fehler angezeigt wird. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 installiert ist. Die Patch-ID lautet ACSD-48417. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Nach dem Erstellen einer Planungsänderung für ein Produkt und dem Speichern eines anderen Produkts wird ein SQL-Fehler angezeigt.

<u>Zu reproduzierende Schritte</u>:

1. Installieren Sie Magento 2.4-develop EE + Sample Data.
1. Navigieren Sie zum Admin-Bedienfeld > **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Bearbeiten von beliebigen Produkten (z. B. Joust Duffle Bag) [SKU: 24-MB01]).
1. Planen Sie eine neue Aktualisierung:
   * Auswählen **[!UICONTROL Save as a New Update]**
   * Aktualisierungsname: &quot;Update 1&quot;
   * Startdatum: aktuelle Zeit +1 Min.
   * Enddatum: aktuelle Zeit: +1 Stunde
   * Ändern Sie den Produktnamen in &quot;Joust Duffle Bag 2&quot;.
   * Speichern Sie das Produkt.
1. Gehen Sie zur CLI und führen Sie cron aus und warten Sie, bis der Zeitplan angewendet wird.

   ```
   bin/magento cron:run && bin/magento cron:run
   ```

1. Gehen Sie erneut zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]** und bearbeiten Sie jedes konfigurierbare Produkt (z. B. Chaz Kangeroo Hoodie [SKU: MH01]).

   * Deaktivieren Sie alle Varianten. Navigieren Sie zur Spalte Aktionen > **[!UICONTROL Select]** > **[!UICONTROL Disable Product]**.
   * Speichern Sie den konfigurierbaren.

<u>Erwartete Ergebnisse</u>:

Kein Fehler beim Speichern des Produkts.

<u>Tatsächliche Ergebnisse</u>:

Der folgende Fehler tritt auf:

```SQL
SQLSTATE[23000]: Integrity constraint violation: 1048 Column 'sku' cannot be null, query was: INSERT INTO `catalog_product_entity` (`entity_id`, `sku`, `row_id`, `created_in`, `updated_in`) VALUES (?, ?, ?, ?, ?)
```

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
