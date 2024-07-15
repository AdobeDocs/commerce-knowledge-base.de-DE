---
title: "MDVA-41350: Ausnahme, wenn der Administrator Produkte außerhalb seines Zugriffs hinzufügt"
description: Der Patch MDVA-41350 behebt das Problem, bei dem anstelle einer eingeschränkten Zugriffsbenachrichtigung ein Ausnahmefehler ausgegeben wird, wenn ein Administrator ein Produkt in der Bestellung durch die SKU hinzufügt, das sich außerhalb seines Zugriffs befindet. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 installiert ist. Die Patch-ID lautet MDVA-41350. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: 3a96d029-5350-4dd6-aad3-2f2cdd5e65ac
feature: Admin Workspace, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-41350: Ausnahme, wenn der Administrator Produkte außerhalb seines Zugriffs hinzufügt

Der Patch MDVA-41350 behebt das Problem, bei dem anstelle einer eingeschränkten Zugriffsbenachrichtigung ein Ausnahmefehler ausgegeben wird, wenn ein Administrator ein Produkt in der Bestellung durch die SKU hinzufügt, das sich außerhalb seines Zugriffs befindet. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 installiert ist. Die Patch-ID lautet MDVA-41350. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.3 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn ein Admin-Benutzer mit eingeschränktem Zugriff ein Produkt von SKU außerhalb seines Zugriffs in der Bestellung hinzufügt, tritt eine Ausnahme auf, anstatt dass der Benutzer über den eingeschränkten Zugriff benachrichtigt wird.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich bei Admin als Benutzer mit Zugriff auf nur eine bestimmte Website an.
1. Wechseln Sie zu **Verkauf** > **Bestellungen** und klicken Sie auf **Neue Bestellung erstellen**.
1. Wählen Sie einen Kunden und eine Store-Ansicht aus.
1. Klicken Sie auf **Produkte von SKU hinzufügen**.
1. Suchen Sie nach einer SKU, die keiner Website zugewiesen ist oder der Website nicht zugewiesen ist, auf die Sie Zugriff haben.
1. Klicken Sie auf **Zur Bestellung hinzufügen**.

<u>Erwartete Ergebnisse</u>:

Eine entsprechende Fehlermeldung wird angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Eine Ausnahme tritt auf.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
