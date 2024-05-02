---
title: "ACSD-50815: Dezimalmenge für einfache Produkte kann nicht für neue gebündelte Produktoptionen verwendet werden"
description: Wenden Sie den Patch ACSD-50815 an, um das Adobe Commerce-Problem zu beheben, bei dem die Dezimalzahl für ein einfaches Produkt nicht für eine neue gebündelte Produktoption verwendet werden kann.
feature: Products
role: Admin
exl-id: f4aa417c-b0eb-4a68-bf1e-fd86770cc72d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# ACSD-50815: Dezimalmenge für einfache Produkte kann nicht für neue gebündelte Produktoptionen verwendet werden

Der Patch ACSD-50815 behebt das Problem, dass die Dezimalzahl für ein einfaches Produkt nicht für eine neue gebündelte Produktoption verwendet werden kann. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35 installiert ist. Die Patch-ID lautet ACSD-50815. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Dezimalzahl für ein einfaches Produkt kann nicht für eine neue gebündelte Produktoption verwendet werden.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich als Administrator an.
1. Erstellen Sie ein neues einfaches Produkt.
   * Im **[!UICONTROL Advanced Inventory]** Fenster, festlegen [!UICONTROL Qty Uses Decimal] = [!UICONTROL Yes].
   * Speichern Sie das einfache Produkt.
1. Erstellen Sie ein neues gebündeltes Produkt.
1. Fügen Sie eine beliebige Option hinzu.
1. Fügen Sie das einfache Produkt in diese Option ein.
1. Legen Sie in der gebündelten Produktoption eine Dezimalzahl für das einfache Produkt fest. Beispiel: 1.5.

<u>Erwartete Ergebnisse</u>:

Es ist möglich, die Dezimalzahl festzulegen. Es werden keine Fehler angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Fehler, *Bitte geben Sie in dieses Feld eine gültige Zahl ein* angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
