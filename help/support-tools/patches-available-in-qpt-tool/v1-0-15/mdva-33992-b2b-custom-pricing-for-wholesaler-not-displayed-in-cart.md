---
title: "MDVA-33992: B2B benutzerdefinierte Preise für Großhändler, die nicht im Warenkorb angezeigt werden"
description: Der Patch MDVA-33992 behebt das Problem, dass die benutzerdefinierten Preise für einen B2B-Kunden nicht berücksichtigt werden, wenn ein Produkt einem Warenkorb hinzugefügt wird. Dieser Patch ist verfügbar, wenn das Quality Patches Tool (QPT) 1.0.15 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben sein soll.
exl-id: 6018fae6-762c-46c6-9497-ecf090115b7f
feature: B2B, Catalog Management, Orders, Shopping Cart
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# MDVA-33992: B2B-Sonderpreise für Großhändler, die nicht im Warenkorb angezeigt werden

Der Patch MDVA-33992 behebt das Problem, dass die benutzerdefinierten Preise für einen B2B-Kunden nicht berücksichtigt werden, wenn ein Produkt einem Warenkorb hinzugefügt wird. Dieser Patch ist verfügbar, wenn das Quality Patches Tool (QPT) 1.0.15 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce für Cloud-Infrastruktur 2.4.1 mit B2B

**Kompatibel mit Adobe Commerce-Versionen:** Adobe Commerce über Cloud-Infrastruktur und Adobe Commerce On-Premise 2.3.0-2.4.1-p1 mit B2B

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die benutzerspezifischen Preise für einen B2B-Kunden werden nicht berücksichtigt, wenn einem Warenkorb ein Produkt hinzugefügt wird.

<u>Zu reproduzierende Schritte</u>:

Das Problem ist reproduzierbar für die B2B-Version mit aktiviertem freigegebenen Katalog.

1. Erstellen Sie ein B2B-Unternehmen mit einem benutzerdefinierten freigegebenen Katalog.
1. Erstellen Sie ein Produkt im benutzerdefinierten Katalog des Unternehmens mit einem benutzerdefinierten Preis (Tier-Preis).
1. Als B2B-Kunde überprüfen Sie, ob der benutzerdefinierte Produktpreis im Katalog angezeigt wird.
1. Als B2B-Kunde fügen Sie das Produkt zum Warenkorb hinzu.

<u>Erwartetes Ergebnis</u>:

Der richtige Preis wird im Warenkorb angezeigt und entspricht dem Preis im Katalog.

<u>Tatsächliches Ergebnis</u>:

Der benutzerdefinierte Preis verschwindet und der reguläre Preis aus dem Standardkatalog wird angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Adobe Commerce-Produkt die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie im Abschnitt [Im QPT-Tool verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) Abschnitt.
