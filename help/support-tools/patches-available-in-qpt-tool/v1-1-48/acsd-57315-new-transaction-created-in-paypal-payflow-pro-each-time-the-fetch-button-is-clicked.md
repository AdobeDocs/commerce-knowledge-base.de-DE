---
title: "ACSD-57315: Neue Transaktion wird erstellt in [!DNL PayPal Payflow Pro] jedes Mal, wenn auf die Schaltfläche zum Abrufen geklickt wird."
description: Wenden Sie den Patch ACSD-57315 an, um das Adobe Commerce-Problem zu beheben, bei dem eine neue Transaktion in [!DNL PayPal Payflow Pro] jedes Mal, wenn auf die Schaltfläche "Abruf"im Bildschirm "Transaktionen anzeigen"im [!UICONTROL Admin].
feature: Payments
role: Admin, Developer
source-git-commit: b7f85e4fdb7ef4a6328a1a411dac765dd8da083e
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-57315: Neue Transaktion wird in erstellt [!DNL PayPal Payflow Pro] jedes Mal, wenn auf die Schaltfläche zum Abrufen geklickt wird

Der Patch ACSD-57315 behebt das Problem, dass eine neue Transaktion in erstellt wird. [!DNL PayPal Payflow Pro] jedes Mal, wenn auf die Schaltfläche &quot;Abruf&quot;im Bildschirm &quot;Transaktionen anzeigen&quot;im [!UICONTROL Admin]. Dieser Patch ist verfügbar, wenn die Variable [!DNL Quality Patches Tool (QPT)] 1.1.48 ist installiert. Die Patch-ID ist ACSD-57315. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.5.0 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6 - p4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Eine neue Transaktion wird in [!DNL PayPal Payflow Pro] jedes Mal, wenn auf die Schaltfläche &quot;Abruf&quot;im Bildschirm &quot;Transaktionen anzeigen&quot;im [!UICONTROL Admin].

<u>Zu reproduzierende Schritte</u>:

1. Konfigurieren [!DNL PayPal Payflow Pro].
1. Setzen Sie die Transaktionsmethode auf *[!UICONTROL Sale]*.
1. Platzieren Sie eine Bestellung mithilfe von *Kreditkarte*.
1. Öffnen Sie die Transaktion von [!UICONTROL Admin].
1. Klicken Sie auf **[!UICONTROL Fetch]** Schaltfläche.
1. Überprüfen [!DNL PayPal] für Transaktionen im Zusammenhang mit der aufgegebenen Bestellung.

<u>Erwartete Ergebnisse</u>:

Es wird kein neuer Zahlungsvorgang erstellt.

<u>Tatsächliche Ergebnisse</u>:

Ein neuer Zahlungsvorgang wird für eine bereits bezahlte Bestellung erstellt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
