---
title: "ACSD-49849: Kunden-E-Mail wurde durch PayPal-E-Mail ersetzt."
description: Wenden Sie den Patch ACSD-49849 an, um das Adobe Commerce-Problem zu beheben, bei dem die E-Mail des Kunden bei der Bestellung mit PayPal Express über GraphQL durch PayPal-E-Mails ersetzt wurde.
exl-id: 826ea90a-ac10-43e8-aa88-bd69b152ded8
feature: Admin Workspace, Communications, Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-49849: Kunden-E-Mail wird ersetzt durch [!DNL PayPal] email

Der Patch ACSD-49849 behebt das Problem, dass die E-Mail eines Kunden durch eine [!DNL PayPal's] E-Mail beim Einfügen einer Bestellung mit [!DNL PayPal Express] über GraphQL. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 ist installiert. Die Patch-ID lautet ACSD-49849. Beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.5-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die E-Mail eines Kunden wird durch eine [!DNL PayPal's] E-Mail beim Einfügen einer Bestellung mit [!DNL PayPal Express] über GraphQL.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zu **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Payments]**.
1. Aktivieren und Konfigurieren [!DNL PayPal Express] und **[!UICONTROL Payment Action]** = **[!UICONTROL Sale]**.
1. Navigieren Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]** und erstellen Sie ein einfaches Produkt.
1. Schließen Sie den Gast-Checkout mit GraphQL ab. Weitere Informationen finden Sie im Abschnitt [Tutorial zu GraphQL Checkout](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/) in der Adobe Commerce-Entwicklerdokumentation.
1. Verwendung [!DNL PayPal Express] als Zahlungsmethode.
1. Notieren Sie die E-Mail, die Sie in dem Schritt verwendet haben, in dem Sie [E-Mail für den Warenkorb einrichten](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/set-email-address/) in der Adobe Commerce-Entwicklerdokumentation.
1. Nachdem die Bestellung aufgegeben wurde, gehen Sie zum Adobe Commerce-Administrator und überprüfen Sie die E-Mail in der erstellten Reihenfolge.

<u>Erwartete Ergebnisse</u>:

Die E-Mail entspricht der beim Checkout festgelegten.

<u>Tatsächliche Ergebnisse</u>:

Die E-Mail-Adresse, die während des Auscheckens eingestellt wird, wird durch den E-Mail-Satz im [!DNL PayPal] -Konto.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
