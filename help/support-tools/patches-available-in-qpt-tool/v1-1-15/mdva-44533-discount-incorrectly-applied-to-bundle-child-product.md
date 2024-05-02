---
title: "MDVA-44533: Unrichtig angewendeter Rabatt auf gebündelte untergeordnete Produkte"
description: Der Patch MDVA-44533 behebt das Problem, dass ein Rabatt fälschlicherweise auf ein gebündeltes Kindprodukt angewendet wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 installiert ist. Die Patch-ID lautet MDVA-44533. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: 84302ed4-d850-45e4-8b5b-44495f9df820
feature: Orders, Personalization, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# MDVA-44533: Rabatt wurde fälschlicherweise auf gebündelte untergeordnete Produkte angewendet

Der Patch MDVA-44533 behebt das Problem, dass ein Rabatt fälschlicherweise auf ein gebündeltes Kindprodukt angewendet wird. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 installiert ist. Die Patch-ID lautet MDVA-44533. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.1 - 2.4.3-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Rabatt wird fälschlicherweise auf ein gebündeltes untergeordnetes Produkt angewendet.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein einfaches Produkt mit einem Preis von 50$.
1. Erstellen Sie ein gebündeltes Produkt und weisen Sie das einfache Produkt als einzige Option für das gebündelte Produkt zu.
1. Erstellen Sie eine Warenkorbpreisregel mit:

   * Bedingung: Wenn der Gesamtbetrag größer als 130$ ist
   * Aktion: Es wird ein Festbetrag von 10$ angewendet

1. Gehen Sie zur Storefront und fügen Sie das Paket-Produkt zum Warenkorb mit qty = 1 hinzu.
1. Gehen Sie zum Warenkorb und vergewissern Sie sich, dass die Gesamtkosten des Bundle-Produkts 50$ betragen und der Rabatt nicht gilt.
1. Ändern Sie die Menge auf 2 und aktualisieren Sie den Warenkorb. Die Gesamtkosten des gebündelten Produkts sollten jetzt 100$ betragen.

<u>Erwartete Ergebnisse</u>:

Der Rabatt wird nicht angewendet, da die Zwischensumme 100\$ beträgt, was in der Regelbedingung weniger als 130\$ beträgt.

<u>Tatsächliche Ergebnisse</u>:

Der Rabatt wird angewendet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
