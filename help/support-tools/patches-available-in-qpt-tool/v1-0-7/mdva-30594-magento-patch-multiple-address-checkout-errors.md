---
title: "MDVA-30594: Multiple address checkout errors"
description: Der Patch MDVA-30594 behebt das Problem, dass der Kunde die Auftragserfolgsseite nicht sieht, nachdem er eine Bestellung mit mehreren Adressen aufgegeben hat. Wenn Sie die Bestellungen beim Commerce-Administrator überprüfen, werden zwei Bestellungen mit denselben Produkten anstelle der richtigen Produkte angezeigt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 installiert ist. Das Problem wurde in Adobe Commerce 2.4.2 behoben.
exl-id: 7560cc39-ff0d-4313-979e-5cd588554c1d
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 0%

---

# MDVA-30594: Fehler beim Auschecken mehrerer Adressen

Der Patch MDVA-30594 behebt das Problem, dass der Kunde die Auftragserfolgsseite nicht sieht, nachdem er eine Bestellung mit mehreren Adressen aufgegeben hat. Wenn Sie die Bestellungen beim Commerce-Administrator überprüfen, werden zwei Bestellungen mit denselben Produkten anstelle der richtigen Produkte angezeigt. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 ist installiert. Das Problem wurde in Adobe Commerce 2.4.2 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce auf Cloud-Infrastruktur 2.3.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Mehrere Adressbestellungen werden nicht mit der Auftragserfolgsseite abgeschlossen und zeigen zwei Bestellungen mit denselben Produkten anstelle der richtigen an.

<u>Voraussetzungen</u>:

Erstellen Sie zwei Websites mit Stores und Store-Ansichten.

<u>Zu reproduzierende Schritte</u>:

1. Satz **Katalogpreisumfang** für den Website-Katalog (**Stores** > **Einstellungen** > **Konfiguration** > **Katalog** > **Katalog** > **Preis** > **Anwendungsbereich**).
1. Konfigurieren **Feste Produktsteuern (FPT)** (**Stores** > **Konfiguration** > **Vertrieb** > **Steuern** > **Feste Produktsteuern**):

   * **FPT aktivieren** = *Ja*
   * **Anzeigepreise in der Produktliste** = *Ausschließen von FPT*
   * **Anzeigepreise auf der Produktansichtsseite** = *Ausschließen von FPT*
   * **Anzeigepreise in Verkaufsmodulen** = *Ausschließen von FPT* (einschließlich **FPT** Beschreibung und Endpreis).
   * **Anzeigepreise in E-Mails** = *Ausschließen von FPT* (einschließlich **FPT** Beschreibung und Endpreis).
   * **Steuern auf FPT anwenden** = *Ja*
   * **FPT in Zwischensumme einschließen** = *Nein*

1. Erstellen Sie eine **FPT-Attribut** und weisen Sie ihn dem standardmäßigen Attributsatz zu. (Siehe [Konfigurieren von FPT: Erstellen eines FPT-Attributs](https://docs.magento.com/user-guide/tax/fixed-product-tax-configuration.html#step-2-create-an-fpt-attribute) in unserem Benutzerhandbuch).

1. Erstellen Sie vier einfache Produkte und legen Sie die **FPT** **Attributwert** (Beispiel: Legen Sie die **FPT**   **Attributwert** = *Australien*).

1. Erstellen Sie zwei gebündelte Produkte mit der folgenden Konfiguration:

   * Definieren **FPT**.
   * Satz **Dynamischer Preis** = *Nein*.
   * Satz **Preis** = *100*.
   * Bundle-Optionen, die zusammen geliefert werden, alle als Standard markiert mit **Preistyp** = *Fest*.
   * Fügen Sie zwei der einfachen Produkte hinzu, die in Schritt 4 erstellt wurden.

1. Erstellen Sie ein Benutzerkonto im Frontend. Aktualisieren Sie die Adresse mit der Adresse Australiens (legen Sie das Land auf Australien fest oder welches Land in der **FPT** Setup).

1. Fügen Sie die beiden gebündelten Produkte zum Warenkorb hinzu.

1. Gehen Sie zur Warenkorbseite und überprüfen Sie, ob die Variable **FPT** korrekt angezeigt wird.

1. Klicks **Checkout mit mehreren Adressen**.

1. Fügen Sie eine zweite Adresse hinzu.

1. Weisen Sie jedes Produkt einer anderen Adresse zu.

1. Fahren Sie mit dem Checkout-Prozess fort bis **Bestellung platzieren**.

1. Klicken Sie auf **Bestellung platzieren** Schaltfläche.

<u>Erwartete Ergebnisse</u>:

Die Bestellung mit mehreren Adressen wurde erfolgreich platziert.

<u>Tatsächliche Ergebnisse</u>:

Eine Nachricht wie: &quot;*Es ist ein Fehler aufgetreten.* angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
