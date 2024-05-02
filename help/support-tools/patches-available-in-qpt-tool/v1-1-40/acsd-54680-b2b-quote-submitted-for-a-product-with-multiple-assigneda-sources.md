---
title: "ACSD-54680: B2B-Anführungszeichen für ein Produkt mit mehreren zugewiesenen Quellen kann nicht verarbeitet werden"
description: Wenden Sie den Patch ACSD-54680 an, um das Adobe Commerce-Problem zu beheben, bei dem das B2B-Angebot für ein Produkt mit mehreren zugewiesenen Quellen nicht verarbeitet werden kann.
feature: B2B
role: Admin, Developer
exl-id: 4d05714c-d32d-46f3-b857-81704c9e96cd
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# ACSD-54680: B2B-Zitat für ein Produkt mit mehreren zugewiesenen Quellen kann nicht verarbeitet werden.

Der Patch ACSD-54680 behebt das Problem, dass das B2B-Zitat für ein Produkt mit mehreren zugewiesenen Quellen nicht verarbeitet werden kann. Dieser Patch ist verfügbar, wenn die Variable [!DNL Quality Patches Tool (QPT)] 1.1.40 ist installiert. Die Patch-ID ist ACSD-54680. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

B2B-Anführungszeichen für ein Produkt mit mehreren zugewiesenen Quellen kann nicht verarbeitet werden.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Sources]** und erstellen Sie zwei neue Quellen: **Quelle 1** und **Quelle 2**.
1. Navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Stocks]** und erstellen Sie einen neuen Stock: **Lager A**, weisen Sie sie der Haupt-Website zu und weisen Sie sie zu **Quelle 1** und **Quelle 2** zu.
1. Erstellen eines einfachen Produkts, zuweisen **Quelle 1** und **Quelle 2**, setzen Sie Qty = *2* für jede Quelle. (die Verkaufsmenge des Erzeugnisses sollte *4* als Ergebnis).
1. Erstellen Sie ein Unternehmenskonto.
1. Navigieren Sie zu **[!UICONTROL Storefront]** und melden Sie sich beim Unternehmenskonto an.
1. Fügen Sie das einfache Produkt mit qty = zum Warenkorb hinzu. *4*.
1. Öffnen Sie die *[!UICONTROL Shopping cart]* und klicken **[!UICONTROL Request a quote]** Schaltfläche.
1. Fügen Sie einen Kommentar- und Anführungsnamen hinzu und klicken Sie auf **[!UICONTROL Send a Request]** Schaltfläche.
1. Navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**.
1. Vor Kurzem veröffentlichte Zitat öffnen.

<u>Erwartete Ergebnisse</u>:

Die zitierten Artikel enthalten das bestellte Produkt.

<u>Tatsächliche Ergebnisse</u>:

Die im Abschnitt &quot;Seite&quot;aufgeführten Elemente sind leer, und das Anführungszeichen kann nicht verarbeitet werden.
`var/log/system.log` contains

```
report.CRITICAL: TypeError: number_format() expects parameter 1 to be float, null given in .../vendor/magento/module-negotiable-quote/Model/QuoteUpdatesInfo.php:232
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
