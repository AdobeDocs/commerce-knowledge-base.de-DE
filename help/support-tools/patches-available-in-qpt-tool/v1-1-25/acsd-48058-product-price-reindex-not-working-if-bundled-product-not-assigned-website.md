---
title: 'ACSD-48058: Neuindizierung des Produktpreises funktioniert nicht, wenn das gebündelte Produkt keine Website zugewiesen hat'
description: Wenden Sie den Patch ACSD-48058 an, um das Adobe Commerce-Problem zu beheben, bei dem die Neuindizierung des Produktpreises nicht funktioniert, wenn das gebündelte Produkt keiner Website zugewiesen ist.
exl-id: 691371f1-7f10-4be6-80e4-821e7cf664a6
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-48058: Neuindizierung des Produktpreises funktioniert nicht, wenn das gebündelte Produkt keine Website zugewiesen hat

Mit dem Patch ACSD-48058 wird das Problem behoben, dass die Neuindizierung des Produktpreises nicht funktioniert, wenn das gebündelte Produkt keiner Website zugewiesen ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 installiert ist. Die Patch-ID ist ACSD-48058. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) >=2.4.5 &lt; 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Neuindizierung des Produktpreises funktioniert nicht, wenn das gebündelte Produkt keiner Website zugewiesen ist.

<u>Schritte zur Reproduktion</u>:

1. Gehen Sie zu Adobe Commerce Admin > **[!UICONTROL Catalog]** > **[!UICONTROL Products]** und erstellen Sie ein neues gebündeltes Produkt oder bearbeiten Sie ein vorhandenes gebündeltes Produkt.
   * Klicken Sie auf die Registerkarte **[!UICONTROL Product in Websites]** und deaktivieren Sie alle Kontrollkästchen (Websites)
   * Produkt speichern
1. Neuindizierung durchführen.

<u>Erwartete Ergebnisse</u>:

Die Neuindizierung wurde erfolgreich durchgeführt.

<u>Tatsächliche Ergebnisse</u>:

Beim Ausführen des Produktpreisindex wird der folgende Fehler ausgelöst:

```bash
Undefined array key <bundel product id > in vendor/magento/module-bundle/Model/ResourceModel/Indexer/Price/DisabledProductOptionPriceModifier.php on line 117
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool].
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
