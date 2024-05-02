---
title: "MDVA-33975 Patch: GraphQL-Preisberechnungen"
description: "Der Patch MDVA-33975 behebt Probleme bei der GraphQL-Preisberechnung. Dazu gehören:"
exl-id: a8266334-72cb-4b50-9ff5-9a977d762e5c
feature: GraphQL, Customer Service, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Patch MDVA-33975: GraphQL-Preisberechnungen

Der Patch MDVA-33975 behebt Probleme bei der GraphQL-Preisberechnung. Zu diesen Problemen gehören:

* Wenn eine Katalogpreisregel auf eine bestimmte Kundengruppe angewendet wird, werden die Artikelpreise im Warenkorb und die Bestellsumme in GraphQL nicht korrekt berechnet.
* Katalogpreisregeln sind nicht in `CartItemPrices` in der -API.
* Der Kundengruppenpreis für den allgemeinen Kunden wird in der GraphQL-Produktabfrageantwort nicht hinzugefügt.
* Die Neuberechnung der Anführungssummen vor der Abgabe einer Antwort zu Anführungspreisen führt dazu, dass angewandte Regeln verloren gehen.
* Der Rabatt für den Versandbetrag wurde beim letzten Abrechnungsschritt nicht abgerufen und die Gesamtsumme wurde falsch angezeigt.
* Der Rabatt wird in GraphQL nicht angewendet, wenn das Kundensegment in der Preisregel des Warenkorbs verwendet wird.

Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.14 ist installiert.

## Betroffene Produkte und Versionen

* Das Patch wurde für Adobe Commerce vor Ort 2.4.1 entwickelt.
* Der Patch ist auch mit den folgenden Adobe Commerce-Versionen kompatibel: Adobe Commerce On-Premise und Adobe Commerce in der Cloud-Infrastruktur 2.3.4 - 2.4.1.

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Wenden Sie den Patch an

Verwenden Sie je nach Adobe Commerce-Produkt die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie im Abschnitt [Im QPT-Tool verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) Abschnitt.
