---
title: "MDVA-29446: Nicht relevante Versandmethode zum Checkout verfügbar"
description: Der Patch MDVA-29446 behebt das Problem, dass eine Versandmethode, die nicht anwendbar ist, bei den Optionen für die Checkout-Versandmethode angezeigt wird und, falls ausgewählt, eine Fehlermeldung "*Carrier mit dieser Methode hat nicht null, Pauschalrate*"angezeigt wird. angezeigt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 installiert ist. Das Problem soll in späteren Adobe Commerce-Versionen behoben werden.
exl-id: 74de5ec4-1f57-4d63-8fbc-614b23783ee3
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# MDVA-29446: Nicht relevante Versandmethode zum Checkout verfügbar

Der Patch MDVA-29446 behebt das Problem, dass eine Versandmethode, die nicht anwendbar ist, in den Optionen für die Checkout-Versandmethode angezeigt wird und, falls ausgewählt, eine Fehlermeldung &quot;*Carrier mit einer solchen Methode nicht null gefunden, Pauschalsatz*.&quot; angezeigt. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 installiert ist. Das Problem soll in späteren Adobe Commerce-Versionen behoben werden.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce in Cloud-Infrastruktur 2.3.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.3-2.4.0.

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Probleme

Sie verfügen über eine Versandmethode, die nicht anwendbar ist, aber bei den Optionen für die Checkout-Versandmethode angezeigt wird. Sie können diese nicht relevante Versandmethode auswählen.

<u>Zu reproduzierende Schritte</u>:

1. Installieren Sie clean 2.3-develop.
1. Einfache Rate aktivieren und festlegen:

   * Schiff in die betreffenden Länder = *Bestimmte Länder*
   * Schiff in bestimmte Länder = *Antarktika*
   * Methode anzeigen, falls nicht zutreffend = *Ja*

1. Deaktivieren Sie alle anderen Versandmethoden.
1. Erstellen Sie im Frontend einen Kunden mit einer US-Adresse.
1. Element auswählen und auf **Zum Warenkorb hinzufügen**.
1. Klicken Sie auf den Warenkorb und klicken Sie auf **Zur Kasse gehen**.

<u>Tatsächliche Ergebnisse</u>:

1. Im **Versand** -Seite sehen Sie Folgendes:

   * Einfache Rate ist sichtbar
   * Pauschalpreis beträgt 0 USD
1. Nachdem der Benutzer auf **Nächste**, erhält der Benutzer den folgenden Fehler:

*&quot;Carrier with such method not found: null, flatrate&quot;*

<u>Erwartete Ergebnisse</u>:

* Der Preis der Versandmethode ist nicht sichtbar, wenn die Versandmethode nicht anwendbar ist.
* Die **Nächste** -Schaltfläche nicht aktiv sein.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
