---
title: '"ACSD-50234: Falscher Kundenname in der Bestätigungs-E-Mail für Bestellungen, die mit [!DNL PayPal]'''
description: Wenden Sie den Patch ACSD-50234 an, um das Adobe Commerce-Problem zu beheben, bei dem der Kundenname in der Bestätigungs-E-Mail für Bestellungen, die mit [!DNL PayPal].
exl-id: b2e9c25a-5dd5-4b37-81e3-ca960078da77
feature: Admin Workspace, Communications, Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-50234: Falscher Kundenname in der Bestätigungs-E-Mail für Bestellungen mit [!DNL PayPal]

Der Patch ACSD-50234 behebt das Problem, dass der Kundenname in der Bestätigungs-E-Mail für Bestellungen, die mit [!DNL PayPal]. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 ist installiert. Die Patch-ID ist ACSD-50234. Beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.4-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Bestätigungs-E-Mail für Bestellungen mit [!DNL PayPal] zeigt den falschen Kundennamen an.

<u>Zu reproduzierende Schritte</u>

1. Aktivieren **[!UICONTROL PayPal Express Checkout]**.
1. Navigieren Sie als Gast zum Frontend.
1. Produkte zum Warenkorb hinzufügen.
1. Checkout mit **[!UICONTROL PayPal Express Checkout]** als Zahlungsmethode.
1. Überprüfen Sie die E-Mail zur Bestellbestätigung.

<u>Erwartete Ergebnisse</u>

Die Bestätigungs-E-Mail, die Rechnungsemail und alle versandbezogenen E-Mails werden an den Namen des Kunden adressiert.

<u>Tatsächliche Ergebnisse</u>

Die Bestellbestätigungs-E-Mail, die Rechnungsemail und alle versandbezogenen E-Mails sind an *Gastgeber*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
