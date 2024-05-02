---
title: "MDVA-28763: Probleme mit der Verwaltung von Produktbildern über REST API"
description: Der Patch MDVA-28763 behebt mehrere Probleme im Zusammenhang mit der Verwaltung der Mediengalerie mithilfe der REST-API. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 installiert ist. Die Probleme sollen in späteren Adobe Commerce-Versionen behoben werden.
exl-id: 736fbfa8-b6a3-413c-a220-fd772d87ed04
feature: REST, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# MDVA-28763: Probleme mit der Verwaltung von Produktbildern über die REST-API

Der Patch MDVA-28763 behebt mehrere Probleme im Zusammenhang mit der Verwaltung der Mediengalerie mithilfe der REST-API. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 ist installiert. Die Probleme sollen in späteren Adobe Commerce-Versionen behoben werden (siehe Problembeschreibungen unter [Probleme](#issues).

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce vor Ort 2.3.2 - 2.3.3.x
* Adobe Commerce auf Cloud-Infrastruktur 2.3.2 - 2.3.3.x

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Probleme {#issues}

Der Patch MDVA-28763 enthält Fehlerbehebungen für die folgenden Probleme im Zusammenhang mit der Mediengalerie:

* Bei Verwendung der REST-API zur Aktualisierung von YouTube-Videos (`PUT rest/V1/products/ {SKU}`, zeigt Adobe Commerce eine Miniaturansicht für das Video an, der Videoplayer wird jedoch nicht geladen, wenn Sie auf die Schaltfläche &quot;Abspielen&quot;klicken. Geplant für die Korrektur in Adobe Commerce 2.3.6.
* `PUT /V1/products/:sku/media/:entryId` -Aufruf erstellt einen neuen Eintrag, anstatt den vorhandenen zu ersetzen. In Adobe Commerce 2.3.5 behoben.
* Probleme beim Löschen von Produktbildern, wenn Produkte mehreren Store-Ansichten zugewiesen werden. In Adobe Commerce 2.3.4 behoben.
* Merchants mit mehreren Websites können jetzt REST verwenden, um Produkte zu erstellen und zu aktualisieren, während die Vererbung von Bildern und Bildrollen beibehalten wird. Wenn zuvor ein Händler REST zum Erstellen und Aktualisieren von Produkten verwendete und ein Produkt für die Store-Ansicht aktualisiert wurde, wurden die standardmäßigen Bildrollen für diese Store-Ansicht geladen und gespeichert. Daher erben die Bildrollen der Store-Ansicht nach nach der Aktualisierung nicht mehr vom Standardbereich. Geplant für die Korrektur in Adobe Commerce 2.3.6.
* Medienattribute (Bild, Miniatur, ...) Werte in Store-Ansichten, die auf entfernte Bilder verweisen, werden nicht automatisch bereinigt. Geplant für die Korrektur in Adobe Commerce 2.4.2.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
