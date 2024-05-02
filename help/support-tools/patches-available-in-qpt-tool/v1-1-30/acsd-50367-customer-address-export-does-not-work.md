---
title: "ACSD-50367: Export von Kundenadressen funktioniert nicht mit Attribut mit Mehrfachauswahl"
description: Wenden Sie den Patch ACSD-50367 an, um das Adobe Commerce-Problem zu beheben, bei dem der Export von Kundenadressen nicht funktioniert, wenn ein Attribut mit Mehrfachauswahl **"Kundenadresse"** ohne Werte erstellt wird.
exl-id: 688831d4-b49e-48fa-b4db-1328cda09a2b
feature: Admin Workspace, Attributes, Data Import/Export, Shipping/Delivery
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-50367: Export von Kundenadressen funktioniert nicht

Der Patch ACSD-50367 behebt das Problem, dass der Export von Kundenadressen bei Mehrfachauswahl nicht funktioniert **`Customer Address`** -Attribut ohne Werte erstellt. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 installiert ist. Die Patch-ID ist ACSD-50367. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Export von Kundenadressen funktioniert nicht, wenn eine Mehrfachauswahl **`Customer Address`** -Attribut ohne Werte erstellt.

<u>Voraussetzungen</u>:

Erstellen Sie einen Kunden mit einer Adresse.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen einer Mehrfachauswahl **`Customer Address`** -Attribut in **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Customer Addresses]**.
1. Navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL System]** > **[!UICONTROL Export]** und wählen Sie **`Customer Address`** Entitätstyp.
1. Exportieren Sie die Kundenadressen. Sie werden sehen, dass nichts exportiert wird.
1. Mehrfachauswahl löschen **`Customer Address`** und exportieren Sie die Kundenadressen erneut. Dieses Mal wird die CSV-Datei der Adressen generiert.

<u>Erwartete Ergebnisse</u>:

Die Kundenadressen können als CSV-Datei exportiert werden, wenn eine Mehrfachauswahl erfolgt **`Customer Address`** -Attribut erstellt.

<u>Tatsächliche Ergebnisse</u>:

Die Kundenadressen können nicht als CSV-Datei exportiert werden, wenn eine Mehrfachauswahl erfolgt **`Customer Address`** -Attribut erstellt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
