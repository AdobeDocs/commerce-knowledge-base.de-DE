---
title: "MDVA-42689: Benutzer erhalten beim Aktualisieren von Produktkategorien während des Imports einen Fehler wegen Integrationsbegrenzung."
description: Der Patch MDVA-42689 behebt das Problem, dass Benutzer beim Aktualisieren von Produktkategorien während des Imports einen Fehler wegen Integrity Constraint Violation erhalten. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-42689. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: 7beff3bb-9313-43dc-be96-e33eff52a38e
feature: Categories, Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-42689: Benutzer erhalten beim Aktualisieren von Produktkategorien während des Imports einen Fehler wegen Integrationsbegrenzung.

Der Patch MDVA-42689 behebt das Problem, dass Benutzer beim Aktualisieren von Produktkategorien während des Imports einen Fehler wegen Integrity Constraint Violation erhalten. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-42689. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.3 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Adobe Commerce gibt beim Aktualisieren von Produktkategorien während des Imports einen Fehler wegen Integrationsbegrenzung aus.

<u>Zu reproduzierende Schritte</u>:

1. Richten Sie zwei Websites ein.
1. Erstellen Sie Unterkategorien unter der Stammkategorie bis zu zwei Ebenen auf der Kategorieseite. Beispiel: Stammkategorie > **Fanggerät** > **Uhren**.
1. Erstellen Sie zwei einfache Produkte und weisen Sie beide Produkte demselben zu. **Fanggerät** > **Uhren** Kategorie.
1. Weisen Sie beiden Websites ein einfaches Produkt zu.
1. Speichern Sie das Produkt.
1. Bereiten Sie eine CSV-Datei für den Import vor. Es sollte zwei Produktdatensätze mit unterschiedlichen Store-Ansichten geben. Eines der Produkte sollte zu beiden Store-Ansichten gehören.
1. Importieren Sie jetzt die CSV-Datei, indem Sie zu **System** > **Import** > **Entitätstyp** (Produkte).

<u>Erwartete Ergebnisse</u>:

CSV-Dateien werden ohne Fehler importiert.

<u>Tatsächliche Ergebnisse</u>:

Adobe Commerce gibt den folgenden Fehler aus:

```SQL
SQLSTATE[23000]: Integrity constraint violation: 1062 Duplicate entry '1302' for key 'PRIMARY', query was: INSERT INTO `catalog_url_rewrite_product_category` (`url_rewrite_id`,`category_id`,`product_id`) VALUES (?, ?, ?), (?, ?, ?), (?, ?, ?)
```

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
