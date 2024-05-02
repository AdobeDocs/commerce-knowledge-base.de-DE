---
title: "MDVA-31007: Anzeige von benutzerdefinierten Adressattributen"
description: Der Patch MDVA-31007 behebt das Problem, dass benutzerdefinierte Adressattribute auf der Seite mit Bestelldetails im Bereich Mein Konto und im Backend (im Standort **Verkauf & gt; Bestellungen**) nicht korrekt angezeigt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.
exl-id: 43c82b66-395f-4e33-8312-9a1994862f5f
feature: Attributes, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---

# MDVA-31007: Benutzerdefinierte Adressattribute werden angezeigt

Der Patch MDVA-31007 behebt das Problem, dass benutzerdefinierte Adressattribute auf der Bestelldetailseite im Bereich Mein Konto und im Backend (im **Vertrieb > Bestellungen** Speicherort). Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 ist installiert. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce auf Cloud-Infrastruktur 2.4.0

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich beim Admin-Backend an.
1. Navigieren Sie zu **Stores** > **Attribute** > **Kundenadressen**.
1. Erstellen Sie zwei Attribute:

   * Eingabetyp festlegen: *Dropdown*.
   * Eingabetyp festlegen: *Text*.

1. Navigieren Sie zu **Stores** > **Konfigurationen** > **Kunde** > **Kundenkonfigurationen**.
1. Auswählen *Anwendungsbereich* as **Standardspeicher** anzeigen.
1. Erweitern Sie die **Adressenvorlage** Abschnitt. Aktualisieren *Text*, *Text One Line*, und *HTML* , um die beiden oben genannten benutzerdefinierten Attribute einzuschließen:

   ```php
   {{depend testdropdown}}Dropdown: {{var testdropdown}}{{/depend}}    {{depend testtext}}Text: {{var testtext}}{{/depend}}
   ```

1. Öffnen Sie die Storefront.
1. Erstellen Sie und melden Sie sich mit einem Benutzer an.
1. Navigieren Sie zu **Mein Konto** > **Adressbuch** und fügen Sie eine neue Adresse hinzu (füllen Sie die beiden benutzerdefinierten Attribute aus).
1. Fügen Sie ein Produkt zum Warenkorb hinzu und geben Sie eine Bestellung auf.
1. Klicken Sie auf der Seite mit dem Bestellerfolg auf die **Bestellnummer** -Link.
1. Beachten Sie auf der Bestelldetailseite den Abschnitt **Bestellinformationen** Abschnitt.
1. Navigieren Sie zu **Backend** > **Vertrieb** > **Bestellungen**, klicken Sie auf die obige Reihenfolge und beobachten Sie die **Adressinformationen** Abschnitt.

<u>Erwartete Ergebnisse</u>:

Sowohl im Frontend- als auch im Backend werden die Abrechnungs- und Lieferadresse wie erwartet angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Sowohl im Frontend- als auch im Backend wird die Rechnungsadresse nicht korrekt angezeigt. Die ausgewählte Option des Dropdown-Attributs fehlt und der Wert des Eingabeattributs enthält den Attributcode.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
