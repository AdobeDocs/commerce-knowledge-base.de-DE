---
title: "MDVA-31791 Patch: Verbesserung der Produktseite mit verwandten Produkten und Zielregeln"
description: Der Patch MDVA-31791 verbessert die Leistung von Produktseiten, wenn [Related products](https://docs.magento.com/user-guide/catalog/settings-advanced-related-products.html) oder [Related products rules](https://docs.magento.com/user-guide/marketing/product-related-rules.html) (Zielregeln) verwendet werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.4.1 behoben wurde.
exl-id: e737bccb-d9eb-4794-9d6b-2c22fa8edaa2
feature: Marketing Tools, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# MDVA-31791 Patch: Verbesserung der Produktseite mit verwandten Produkten und Zielregeln

Der Patch MDVA-31791 verbessert die Leistung von Produktseiten, wenn [Verwandte Produkte](https://docs.magento.com/user-guide/catalog/settings-advanced-related-products.html) oder [Verwandte Produktregeln](https://docs.magento.com/user-guide/marketing/product-related-rules.html) (Zielregeln) verwendet. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 ist installiert. Beachten Sie, dass das Problem in Adobe Commerce 2.4.1 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wurde für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.4.0

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce für Cloud-Infrastruktur und Adobe Commerce vor Ort 2.3.4, 2.3.4-p1, 2.3.4-p2, 2.4.0, 2.4.0-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Geringe Leistung von Produktseiten, wenn verwandte Produkte oder Target-Regeln verwendet werden.

Erwägen Sie die Anwendung des MDVA-31791 Patches, wenn Sie [Verwandtes Produkt](https://docs.magento.com/user-guide/catalog/settings-advanced-related-products.html) oder [Verwandte Produktregeln](https://docs.magento.com/user-guide/marketing/product-related-rules.html) Funktionalität.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
