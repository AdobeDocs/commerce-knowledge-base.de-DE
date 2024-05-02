---
title: "MDVA-35197: GraphQL erhöht den Warenkorbfehler, wenn Produkte nicht mehr vorrätig hinzugefügt werden"
description: Der Patch MDVA-35197 behebt das Problem, bei dem beim Hinzufügen zum Warenkorb mit GraphQL ein Fehler auftritt, wenn zuvor hinzugefügte Produkte nicht mehr vorrätig sind. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 installiert ist.
exl-id: 189312f7-a505-4ba4-b12d-662987e69374
feature: GraphQL, Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# MDVA-35197: GraphQL erhöht den Warenkorbfehler, wenn Produkte nicht mehr vorrätig hinzugefügt werden

Der Patch MDVA-35197 behebt das Problem, bei dem beim Hinzufügen zum Warenkorb mit GraphQL ein Fehler auftritt, wenn zuvor hinzugefügte Produkte nicht mehr vorrätig sind. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 ist installiert.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce in Cloud-Infrastruktur 2.3.6

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.5 - 2.3.6-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Fehler beim Versuch, ein Produkt über GraphQL zum Warenkorb hinzuzufügen, wenn das andere Produkt, das bereits im Warenkorb liegt (ebenfalls über GraphQL hinzugefügt), nicht mehr vorrätig ist.

<u>Zu reproduzierende Schritte</u>:

1. Fügen Sie mit GraphQL dem Warenkorb beliebige Produkte hinzu.
1. Melden Sie sich beim Commerce Admin-Bedienfeld an und legen Sie dieses Produkt als nicht vorrätig fest.
1. Versuchen Sie, über GraphQL ein anderes Produkt zum Warenkorb hinzuzufügen.

<u>Erwartete Ergebnisse</u>:

In Lager befindliche Produkte können dem Warenkorb hinzugefügt werden.

<u>Tatsächliche Ergebnisse</u>:

GraphQL-Fehlermeldung: *Einige der Produkte sind nicht vorrätig*. Ein neues &quot;vorrätiges&quot;Produkt kann nicht hinzugefügt werden.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
