---
title: 'MDVA-31640 Patch: Nicht in der Lage, aufeinander folgende geplante Aktualisierungen über REST-API zu erstellen'
description: Der Patch MDVA-31640 behebt das Problem, dass eine neue geplante Aktualisierung für den Sonderpreis nicht für mehrere Stores erstellt werden kann, die die REST-API verwenden, wenn das Anfangsdatum der Aktualisierung mit dem Enddatum der zuvor vorhandenen Aktualisierung übereinstimmt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.
exl-id: 8d91db3d-7c94-4757-8087-4cf53cad81e7
feature: REST
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# MDVA-31640 Patch: Keine aufeinander folgende geplante Aktualisierung über REST API möglich

Der Patch MDVA-31640 behebt das Problem, dass eine neue geplante Aktualisierung für den Sonderpreis nicht für mehrere Stores erstellt werden kann, die die REST-API verwenden, wenn das Anfangsdatum der Aktualisierung mit dem Enddatum der zuvor vorhandenen Aktualisierung übereinstimmt. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 ist installiert. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wurde für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.3.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce für Cloud-Infrastruktur und Adobe Commerce On-Premise 2.3.1 - 2.3.5-p2, 2.4.0, 2.4.0-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Behebung des Problems, bei dem eine neue geplante Aktualisierung für den Sonderpreis nicht für mehrere Stores mit der REST-API erstellt werden kann, wenn das Anfangsdatum der Aktualisierung mit dem Enddatum der zuvor vorhandenen Aktualisierung zusammenfällt.

<u>Zu reproduzierende Schritte</u>:

1. Richten Sie eine zusätzliche Website-, Store- und Store-Ansicht ein.
1. Erstellen Sie zwei einfache Produkte: &quot;product1&quot;und &quot;product2&quot;.
1. Weisen Sie Produkt1 einer Website und Produkt2 beiden Websites zu.
1. Erstellen Sie eine geplante Aktualisierung für den Sonderpreis für &quot;product1&quot;in der Store-Ansicht für den Store mit ID 1. REST-API verwenden `POST` Anfrage an `rest/V1/products/special-price` mit der folgenden Payload:
   `{        "prices": [            {                "price": 15,                "store_id": 1,                "sku": "product1",                "price_from": "2021-11-15 04:00:00",                "price_to": "2021-11-15 04:10:00"            }        ]    }`
1. Erstellen Sie eine geplante Aktualisierung für den Sonderpreis für das Produkt2 in beiden Store-Ansichten für Stores mit ID 1 und 2 mithilfe der REST-API. `POST` Anfrage an `rest/V1/products/special-price` mit der folgenden Payload (der `price_from` date ist dasselbe wie `price_to` Datum in der vorherigen Anfrage):
   `{        "prices": [            {                "price": 14,                "store_id": 1,                "sku": "product2",                "price_from": "2021-11-15 04:10:00",                "price_to": "2021-11-15 04:15:00"            },            {                "price": 13,                "store_id": 2,                "sku": "product2",                "price_from": "2021-11-15 04:10:00",                "price_to": "2021-11-15 04:15:00"            }        ]    }`

<u>Erwartete Ergebnisse</u>:

Geplantes Update mit der speziellen Preisänderung wird für beide Store-Ansichten erstellt.

<u>Tatsächliche Ergebnisse</u>:

Adobe Commerce gibt einen Fehler aus. Geplante Aktualisierung wird nicht erstellt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
