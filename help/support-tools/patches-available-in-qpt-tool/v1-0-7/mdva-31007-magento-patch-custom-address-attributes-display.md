---
title: "MDVA-31007: Anzeige von benutzerdefinierten Adressattributen"
description: Der Patch MDVA-31007 behebt das Problem, dass benutzerdefinierte Adressattribute nicht korrekt auf der Seite mit Bestelldetails im Bereich Mein Konto und im Backend angezeigt werden (im Standort **Sales & amp;gt; Bestellungen**). Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.
exl-id: 43c82b66-395f-4e33-8312-9a1994862f5f
feature: Attributes, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---

# MDVA-31007: Benutzerdefinierte Adressattribute werden angezeigt

Der Patch MDVA-31007 behebt das Problem, dass benutzerdefinierte Adressattribute nicht korrekt auf der Seite mit Bestelldetails im Bereich Mein Konto und im Backend angezeigt werden (am Standort **Verkauf > Bestellungen** ). Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce auf Cloud-Infrastruktur 2.4.0

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich beim Admin-Backend an.
1. Navigieren Sie zu **Stores** > **Attribute** > **Kundenadressen**.
1. Erstellen Sie zwei Attribute:

   * Festlegen des Eingabetyps: *Dropdown*.
   * Festlegen des Eingabetyps: *Text*.

1. Navigieren Sie zu **Stores** > **Konfigurationen** > **Kunde** > **Kundenkonfigurationen**.
1. Wählen Sie *Umfang* als Ansicht **Standardspeicher** aus.
1. Erweitern Sie den Abschnitt **Adressenvorlage** . Aktualisieren Sie *Text*, *Text One Line* und *HTML*, um die beiden oben genannten benutzerdefinierten Attribute einzuschließen:

   ```php
   {{depend testdropdown}}Dropdown: {{var testdropdown}}{{/depend}}    {{depend testtext}}Text: {{var testtext}}{{/depend}}
   ```

1. Öffnen Sie die Storefront.
1. Erstellen Sie und melden Sie sich mit einem Benutzer an.
1. Gehen Sie zu **Mein Konto** > **Adressbuch** und fügen Sie eine neue Adresse hinzu (füllen Sie die beiden benutzerdefinierten Attribute aus).
1. Fügen Sie ein Produkt zum Warenkorb hinzu und geben Sie eine Bestellung auf.
1. Klicken Sie auf der Erfolgsseite der Bestellung auf den Link **Bestellnummer** .
1. Beachten Sie auf der Bestelldetailseite den Abschnitt **Bestellinformationen** .
1. Wechseln Sie zu **Backend** > **Verkauf** > **Bestellungen**, klicken Sie auf die oben aufgeführte Bestellung und beachten Sie den Abschnitt **Adressinformationen** .

<u>Erwartete Ergebnisse</u>:

Sowohl im Frontend- als auch im Backend werden die Abrechnungs- und Lieferadresse wie erwartet angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Sowohl im Frontend- als auch im Backend wird die Rechnungsadresse nicht korrekt angezeigt. Die ausgewählte Option des Dropdown-Attributs fehlt und der Wert des Eingabeattributs enthält den Attributcode.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
