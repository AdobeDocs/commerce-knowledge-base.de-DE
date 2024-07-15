---
title: "MDVA-32714 Patch: Kundengruppenpreis funktioniert nicht über GraphQL"
description: Der Patch MDVA-32714 behebt das Problem, dass с Kundengruppenpreis in der GraphQL-Produktabfrageantwort nicht hinzugefügt wird. Dieser Patch ist verfügbar, wenn das Quality Patches Tool (QPT) 1.0.13 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben sein soll.
exl-id: a4fc92ad-68dc-437d-8577-303007ef8a92
feature: GraphQL, Customer Service, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# MDVA-32714 Patch: Kundengruppenpreis funktioniert nicht über GraphQL

>[!WARNING]
>
>Ein neuer Patch namens MDVA-33975 behebt Probleme bei der GraphQL-Preisberechnung. MDVA-32714 wird abgeschrieben und es wird empfohlen, den Patch MDVA-33975 anzuwenden. Informationen zum Zugriff auf diesen Patch finden Sie im Patch [MDVA-33975: GraphQL-Preisberechnungen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/mdva-33975-magento-patch-graphql-price-calculations.html) in unserer Support-Wissensdatenbank.

Der Patch MDVA-32714 behebt das Problem, dass с Kundengruppenpreis in der GraphQL-Produktabfrageantwort nicht hinzugefügt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.4.0

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce über Cloud-Infrastruktur und Adobe Commerce vor Ort 2.3.4 - 2.4.0-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Kundengruppenpreis für den allgemeinen Kunden wird in der GraphQL-Produktabfrageantwort nicht hinzugefügt.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren und legen Sie für jedes Produkt einen Sonderpreis für eine beliebige Kundengruppe fest.
1. Verwenden Sie die Produktabfrage in GraphQL, um Preise für dieses Produkt abzurufen, wie in der Entwicklerdokumentation unter [Produktanfrage > Beispielabfrage](https://devdocs.magento.com/guides/v2.4/graphql/queries/products.html#sample-queries) beschrieben.

<u>Erwartete Ergebnisse</u>:

```api
price_range
```

zeigt den ermäßigten Preis für allgemeine Kunden entsprechend der Definition im Admin Panel an.

<u>Tatsächliche Ergebnisse</u>:

```api
price_range
```

zeigt den ermäßigten Preis nicht für allgemeine Kunden an.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie in der [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
