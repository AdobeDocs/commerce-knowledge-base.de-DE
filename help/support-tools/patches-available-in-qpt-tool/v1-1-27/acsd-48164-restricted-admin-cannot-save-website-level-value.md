---
title: "ACSD-48164: Eingeschränkter Administrator kann Wert auf Website-Ebene nicht speichern"
description: Wenden Sie den Patch ACSD-48164 an, um das Adobe Commerce-Problem zu beheben, bei dem ein eingeschränkter Administrator keinen Wert auf Website-Ebene speichern kann.
exl-id: 6ec15163-ad30-4566-a46c-5756bfd9f8d4
feature: Admin Workspace
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-48164: Eingeschränkter Administrator kann Wert auf Website-Ebene nicht speichern

Der Patch ACSD-48164 behebt das Problem, dass ein eingeschränkter Administrator keinen Wert auf Website-Ebene speichern kann. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 ist installiert. Die Patch-ID lautet ACSD-48164. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Eingeschränkte Administratoren können keinen Wert auf Website-Ebene speichern.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine neue Website-, Store- und Store-Ansicht in [!UICONTROL Admin] > **[!UICONTROL Store]** > **[!UICONTROL All Stores]**.
1. Erstellen Sie eine neue Administratorrolle in [!UICONTROL Admin] > **[!UICONTROL System]** > **[!UICONTROL User Roles]**.

   * Navigieren Sie zu **[!UICONTROL Role Resources]** > **[!UICONTROL Role Scopes]**, wählen Sie die neue Website aus und weisen Sie diese Rolle jedem Administrator zu.

1. Wählen Sie ein beliebiges Produkt aus und weisen Sie nur die neue Website zu. Wählen Sie nicht die Standardwebsite aus.
1. Melden Sie sich als in Schritt 2 zugewiesener Admin-Benutzer an und bearbeiten Sie das Produkt unter **[!UICONTROL All Store View]** Umfang durch Änderung eines beliebigen Attributs auf Website-Ebene wie *[!UICONTROL Status]*, *[!UICONTROL Tax Class]* und legen Sie das Produkt als neu fest.
1. Speichern Sie das Produkt.

<u>Erwartete Ergebnisse</u>:

Admin-Benutzer, der mit dem Rollenbereich einer Website verknüpft ist, können Produktattribute auf Website-Ebene mithilfe der *[!UICONTROL All Store View]* Umfang.

<u>Tatsächliche Ergebnisse</u>:

Die Erfolgsmeldung, dass das Produkt gespeichert wurde, wird angezeigt, aber die Produktattributwerte bleiben unverändert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
