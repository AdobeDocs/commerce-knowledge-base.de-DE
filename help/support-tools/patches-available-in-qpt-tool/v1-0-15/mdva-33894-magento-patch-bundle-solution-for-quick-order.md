---
title: "MDVA-33894 Patch: Bundle-Lösung für Schnellbestellung"
description: Der Patch MDVA-33894 behebt mehrere Probleme im Zusammenhang mit der Schnellbestellfunktion, einschließlich des Hinzufügens und Entfernen mehrerer Produkte und der SKU-Groß-/Kleinschreibung. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben sein soll.
exl-id: d0b18e71-5f48-441e-a8b9-c459f3d34599
feature: Cache, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# MDVA-33894 Patch: Bundle-Lösung für Schnellbestellung

Der Patch MDVA-33894 behebt mehrere Probleme im Zusammenhang mit der Schnellbestellfunktion, einschließlich des Hinzufügens und Entfernen mehrerer Produkte und der SKU-Groß-/Kleinschreibung. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce auf Cloud-Infrastruktur 2.4.0

**Kompatibel mit Adobe Commerce-Versionen:** Adobe Commerce über Cloud-Infrastruktur und Adobe Commerce vor Ort 2.4.0-2.4.1-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

MDVA-33894 Patch ist eine Bundle-Lösung mit Fehlerbehebungen für folgende Probleme:

* **Mein Konto** > **Bestellung nach SKU** Bei der Funktion wird zwischen Groß- und Kleinschreibung unterschieden: Wenn Sie eine gültige SKU eingeben, die Groß-/Kleinschreibung jedoch nicht korrekt ist (Groß-/Kleinschreibung anstatt Kleinschreibung usw.), gibt Adobe Commerce einen Fehler aus.
* Wenn ein Käufer mit der Schnellbestellung mehrere Produkte zum Warenkorb hinzufügt und versucht, ein Produkt zu entfernen, wird das Produkt nicht entfernt.
* Probleme mit der Groß-/Kleinschreibung beim Hinzufügen mehrerer SKUs zu einer Massenbestellung.
* Problem mit dem Cache der Schnellbestellseite mit zuvor eingegebenen SKUs.
* Die Menge der Schnellbestellungen wird nicht im Warenkorb angezeigt.
* Die SKU-Duplizierung wird nicht ordnungsgemäß validiert.

## Wenden Sie den Patch an

Verwenden Sie je nach Adobe Commerce-Produkt die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie im Abschnitt [Im QPT-Tool verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) Abschnitt.
