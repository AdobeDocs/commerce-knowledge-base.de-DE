---
title: "MDVA-44100: Alle FPTs werden dem letzten Produkt im Warenkorb zugewiesen."
description: Der Patch MDVA-44100 behebt das Problem, dass alle FPTs dem letzten Produkt im Warenkorb zugewiesen werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 installiert ist. Die Patch-ID lautet MDVA-44100. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: ab0f195c-fcc6-41ac-932d-d2603d068aa6
feature: Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-44100: Alle FPTs werden dem letzten Produkt im Warenkorb zugewiesen

Der Patch MDVA-44100 behebt das Problem, dass alle FPTs dem letzten Produkt im Warenkorb zugewiesen werden. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 ist installiert. Die Patch-ID lautet MDVA-44100. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Alle FPTs werden dem letzten Produkt im Warenkorb zugewiesen und die FPT-Werte für die übrigen Produkte werden zurückgesetzt.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zu **Stores** > **Konfiguration** > **Vertrieb** > **Steuern** und festlegen:
   * FPT aktivieren = Ja
   * Steuern auf FPT anwenden = Ja
   * FPT in Zwischensumme einschließen = Ja
1. Navigieren Sie zu **Stores** > **Attribut** > **Produkt** und erstellen Sie ein neues Attribut mit dem Typ = Feste Produktsteuer.
1. Fügen Sie das Attribut einem Attributsatz hinzu.
1. Erstellen Sie zwei Produkte aus dem Attributsatz und konfigurieren Sie das FPT-Attribut für Ihr Land und Ihren Staat.
1. Fügen Sie beide Elemente zur Bestellung hinzu.
1. Geben Sie eine Adresse ein, für die FPT bezahlt werden muss.
1. Platzieren Sie die Bestellung.
1. Überprüfen Sie die Elementliste in der Bestellung.

<u>Erwartete Ergebnisse</u>:

Die FPTs werden unter jedem Produkt angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Die FPT-Werte aus beiden Elementen werden unter dem zweiten Element angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
