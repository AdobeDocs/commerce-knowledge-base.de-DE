---
title: 'ACSD-48694: Fehler wegen ungültiger Statusänderung angefordert verhindert, dass der Kunde eine Bestellung aufgibt'
description: Wenden Sie den Patch ACSD-48694 an, um das Adobe Commerce-Problem zu beheben, bei dem der Fehler „Ungültige Statusänderung angefordert“ einen Kunden daran hindert, eine Bestellung aufzugeben.
exl-id: edf79424-6c4f-4cfd-ab7e-19f95b9bc685
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# ACSD-48694: *Ungültige Statusänderung angefordert* Fehler verhindert, dass der Kunde eine Bestellung aufgibt

Der Patch ACSD-48694 behebt das Problem, dass der Fehler *Ungültige Statusänderung angefordert* einen Kunden daran hindert, eine Bestellung aufzugeben. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 installiert ist. Die Patch-ID ist ACSD-48694. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.37-p4, 2.4.1 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Fehler *Ungültige Statusänderung angefordert* verhindert, dass ein Kunde eine Bestellung aufgibt.

<u>Schritte zur Reproduktion</u>:

1. Fügen Sie eine leichte Verzögerung während der `/estimate-shipping-methods` hinzu, indem Sie eine `sleep()` bei `app/code/Magento/Quote/Model/GuestCart/GuestShippingMethodManagement.php::estimateByExtendedAddress()` Funktion einbeziehen, sodass die `/estimate-shipping-methods` Anfrage nach der `/shipping-information` abgeschlossen wird, wenn Sie während des Checkouts vom Versandschritt zum Zahlungsschritt wechseln.
1. Konfigurieren Sie die Sitzung so, dass [!DNL Redis] mit der Einstellung *disable_locking: 1* verwendet wird.
1. Öffnen Sie **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** und aktivieren Sie *[!UICONTROL Persistent Shopping Cart]*.
1. Melden Sie sich als Kunde an und fügen Sie dem Warenkorb ein Produkt hinzu.
1. Lassen Sie die Kundensitzung ablaufen. Das persistente Cookie und der Warenkorb bleiben bestehen.
1. Gehen Sie nun zur Kasse, fügen Sie die Lieferadresse hinzu und navigieren Sie zum Abschnitt Zahlung .
1. Gehen Sie zurück zur Startseite oder zu einer anderen Seite und melden Sie sich mit dem Kundenkonto an.
1. Die Sitzung soll erneut ablaufen.
1. Gehen Sie nun direkt zur Kasse und navigieren Sie zum Schritt Zahlung .
1. Versuchen Sie, die Bestellung aufzugeben.

<u>Erwartete Ergebnisse</u>:

* Es liegt kein Fehler vor.
* Die Bestellung wurde erfolgreich aufgegeben und *Seite „Vielen*&quot; wird angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Der Fehler *Ungültige Statusänderung angefordert* wird angezeigt, aber die Bestellung wird aufgegeben.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
