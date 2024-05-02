---
title: "MDVA-30845: Checkout-Verbindung zum Reedereien schlägt fehl."
description: Der Patch MDVA-30845 behebt das Problem, dass der * leider keine Anführungszeichen für diese Bestellung zu diesem Zeitpunkt*-Fehler angezeigt wird, wenn beim Checkout keine Verbindung mit UPS XML/USPS/DHL hergestellt wird und keine andere Versandmethode verfügbar ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben sein soll.
exl-id: 7be54213-1762-431b-bd3b-080c3d45f492
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# MDVA-30845: Checkout-Verbindung zum Versandunternehmen schlägt fehl

Der Patch MDVA-30845 behebt das Problem, bei dem die *Für diese Bestellung sind derzeit leider keine Angebote verfügbar* wird angezeigt, wenn beim Checkout keine Verbindung zu UPS XML/USPS/DHL hergestellt werden konnte und keine andere Versandmethode verfügbar ist. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce auf Cloud-Infrastruktur 2.3.5-p2.

**Kompatibel mit Adobe Commerce-Versionen:** Adobe Commerce vor Ort und Adobe Commerce über Cloud-Infrastruktur 2.3.5-2.3.6.

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Während des Checkout wird die *Für diese Bestellung sind derzeit leider keine Angebote verfügbar* wird ein Fehler angezeigt, wenn keine Verbindung zu UPS XML/USPS/DHL hergestellt werden kann und keine andere Versandmethode verfügbar ist.

<u>Zu reproduzierende Schritte:</u>

1. Erstellen Sie ein Produkt.
1. Aktivieren und konfigurieren Sie die UPS XML-Versandmethode.
1. Fügen Sie das Produkt auf der Vorderseite des Stores zum Warenkorb hinzu.
1. Vergewissern Sie sich, dass UPS Versandmethoden und der pauschale Versand verfügbar sind.
1. Bearbeiten Sie die Datei hosts , um zu verhindern, dass USP eine Verbindung zu seinem Gateway herstellt.
1. Versuchen Sie auf der Storefront, die Preise zu erhalten und fahren Sie mit dem Checkout erneut fort.

<u>Ergebnis:</u>

*Für diese Bestellung sind derzeit leider keine Angebote verfügbar* -Fehler angezeigt wird und kein Pauschalversand verfügbar ist.

<u>Erwartetes Ergebnis:</u>

Es wird keine Fehlermeldung angezeigt und es ist ein Pauschalversand verfügbar.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.


## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) Abschnitt.
