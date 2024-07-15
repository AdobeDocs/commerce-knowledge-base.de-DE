---
title: "MDVA-28300: Problem bei der Preisberechnung mit Katalogpreisregel in GraphQL"
description: Der Patch MDVA-28300 behebt das Problem, dass die GraphQL-Anfrage nicht die Preisänderungen aus Katalogpreisregeln widerspiegelt. Dieser Patch ist verfügbar, wenn das Quality Patches Tool (QPT) Version 1.0.6 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.3.6 behoben wurde.
exl-id: 86079d29-db69-4758-a159-aeed8e0ea21f
feature: Catalog Management, GraphQL, Customer Service, Marketing Tools, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 0%

---

# MDVA-28300: Preiskalkulation mit Katalogpreisregel in GraphQL

>[!WARNING]
>
>Ein neuer Patch namens MDVA-33975 behebt Probleme bei der GraphQL-Preisberechnung. MDVA-28300 wird abgeschrieben und es wird empfohlen, den Patch MDVA-33975 anzuwenden. Informationen zum Zugriff auf diesen Patch finden Sie unter [MDVA-33975: GraphQL-Preisberechnungen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/mdva-33975-magento-patch-graphql-price-calculations.html).

Der Patch MDVA-28300 behebt das Problem, dass die GraphQL-Anfrage nicht die Preisänderungen aus Katalogpreisregeln widerspiegelt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.3.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce lokal 2.3.5-p1

**Kompatibel mit Adobe Commerce-Versionen:** Adobe Commerce On-Premises und Adobe Commerce in der Cloud-Infrastruktur 2.3.0 - 2.3.5-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn eine Katalogpreisregel auf eine bestimmte Kundengruppe angewendet wird, werden die Artikelpreise im Warenkorb und die Bestellsumme in GraphQL nicht korrekt berechnet.

<u>Zu reproduzierende Schritte:</u>

1. Erstellen Sie ein neues Kundenkonto und ändern Sie seine Kundengruppe in Großhandel.
1. Erstellen Sie eine neue Katalogregel in **Marketing** > **Promotions** > **Katalogpreisregeln** mit den folgenden Parametern:
   * Kundengruppen: WholesaleActions:
   * Anwenden: *Anwenden als Prozentsatz des Originals*
   * Rabatt: *50*


1. Erstellen Sie ein neues Produkt mit Preis = 100.
1. Melden Sie sich mit dem zuvor erstellten Kundenkonto bei der Frontend-Anwendung an (wenn Sie bereits angemeldet waren, melden Sie sich ab und wieder an).
1. Fügen Sie das Produkt zum Warenkorb hinzu. Der Preis des Produkts beträgt 50 (regulärer Preis 100) und die Bestellsumme 55 (50 + 5 der Versandkosten).
1. Führen Sie den GraphQL-API-Aufruf aus, der in der [customerCart-Abfrage](https://devdocs.magento.com/guides/v2.3/graphql/queries/customer-cart.html) in unserer Entwicklerdokumentation beschrieben ist.

<u>Erwartetes Ergebnis:</u>

Sowohl die API als auch das Frontend weisen dieselbe Bestellsumme auf, wobei der von der Katalogregel eingeführte Rabatt angewendet wird.

<u>Tatsächliches Ergebnis:</u>

Die Gesamtbestellung wendet keinen Rabatt auf die Katalogregel an.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Wenden Sie Patches mithilfe des Tools für Qualitätsmuster an](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* Adobe Commerce in der Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html).

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt Verfügbare Patches in QPT .
