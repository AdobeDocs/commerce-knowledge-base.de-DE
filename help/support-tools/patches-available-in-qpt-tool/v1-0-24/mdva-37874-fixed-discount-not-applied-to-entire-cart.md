---
title: "MDVA-37874: Fester Rabatt nicht auf den gesamten Warenkorb angewendet"
description: Der Patch MDVA-37874 behebt das Problem, dass der **feste Rabattbetrag** für den gesamten Warenkorb fälschlicherweise auf ein Bundle-Produkt mit mehr als einer Option angewendet wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.24 installiert ist. Die Patch-ID lautet MDVA-37874. Bitte beachten Sie, dass das Problem in Adobe Commerce-Version 2.4.3 behoben werden soll.
exl-id: a1c414f0-b654-4b18-b502-47351513ddfa
feature: Orders, Personalization, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# MDVA-37874: Fester Rabatt wird nicht auf den gesamten Warenkorb angewendet

Der Patch MDVA-37874 behebt das Problem, wenn die **Festbetrag** für den gesamten Warenkorb nicht korrekt auf ein Bundle-Produkt angewendet wird, das mehr als eine Option enthält. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.24 ist installiert. Die Patch-ID lautet MDVA-37874. Bitte beachten Sie, dass das Problem in Adobe Commerce-Version 2.4.3 behoben werden soll.

## Betroffene Produkte und Versionen

* Der Patch wurde für Adobe Commerce in der Cloud-Infrastruktur 2.4.2 entwickelt.
* Der Patch ist auch mit Adobe Commerce vor Ort und Adobe Commerce in der Cloud-Infrastruktur 2.3.6-2.3.7 und 2.4.1-2.4.2-p1 kompatibel.

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem


<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine Warenkorbregel mit einer **Festbetrag** für den gesamten Warenkorb.
1. Fügen Sie ein Bundle-Produkt zum Warenkorb hinzu (das Bundle-Produkt sollte mehrere ausgewählte Optionen enthalten.)
1. Gehen Sie zur Warenkorbseite und überprüfen Sie den Rabatt.


<u>Erwartete Ergebnisse</u>:

Der feste Rabattbetrag wird wie erwartet auf den gesamten Warenkorb angewendet.

<u>Tatsächliche Ergebnisse</u>:

Der feste Rabattbetrag wird nur auf einen Teil des Warenkorbs angewendet.


## Wenden Sie den Patch an

Verwenden Sie je nach Adobe Commerce-Produkt die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie im Abschnitt [Im QPT-Tool verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) Abschnitt.
