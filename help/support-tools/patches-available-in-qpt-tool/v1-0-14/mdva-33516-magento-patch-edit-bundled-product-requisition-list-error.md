---
title: "MDVA-33516 Patch: edit bundled product Requisition List error"
description: Der Patch MDVA-33516 behebt das Problem, dass Sie beim Bearbeiten des Bundle-Produkttyps aus der Anforderungsliste zu einer Fehlerseite für das Anforderungslistenelement weitergeleitet werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.14 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben sein soll.
exl-id: 76a16982-f977-4674-b05e-23f4ac355d52
feature: B2B, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# MDVA-33516 Patch: Fehler bei gebündelter Produktanforderungsliste bearbeiten

Der Patch MDVA-33516 behebt das Problem, dass Sie beim Bearbeiten des Bundle-Produkttyps aus der Anforderungsliste zu einer Fehlerseite für das Anforderungslistenelement weitergeleitet werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.14 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce in Cloud-Infrastruktur 2.3.4

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce auf Cloud-Infrastruktur 2.3.0 - 2.3.5 - p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Fehler beim Bearbeiten von gebündelten Produkten auf der Anforderungsliste.

<u>Voraussetzungen</u>:

* B2B wird installiert.
* Die Anforderungsliste ist aktiviert.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein gebündeltes Produkt mit zwei einfachen Produkten.
1. Klicken Sie auf der gebündelten Produktseite auf die Schaltfläche **Anpassen und Zum Warenkorb hinzufügen** .
1. Wählen Sie eine der Optionen aus der Dropdown-Liste aus und klicken Sie auf **Zur Anforderungsliste hinzufügen** , um eine neue Anforderungsliste zu erstellen. Detaillierte Anweisungen finden Sie im Abschnitt zum [Magento-Benutzerhandbuch > Meine Anforderungslisten > Erstellen einer Anforderungsliste](https://docs.magento.com/user-guide/customers/account-dashboard-requisition-lists.html#create-a-requisition-list) in unserem Benutzerhandbuch.
1. Gehen Sie zur neu erstellten Anforderungsliste (Mein Konto > **Meine Anforderungslisten**).
1. Klicken Sie in der Spalte *Aktionen* auf die Schaltfläche **Anzeigen** .
1. Klicken Sie auf die Schaltfläche **Bearbeiten** .

<u>Erwartete Ergebnisse</u>:<br>

Keine Fehler.

<u>Tatsächliche Ergebnisse</u>:

Seite &quot;Ihre Anpassung&quot;, die ein Bild des gebündelten Produkts, des Preises und der folgenden Fehlermeldung enthält:

```
Fatal error: Uncaught Error: Call to a member function isAvailableForCompare() on null in /var/www/html/var/view_preprocessed/pub/static/vendor/magento/module-catalog/view/frontend/templates/product/view/addto/compare.phtml:1 Stack trace: #0 /var/www/html/vendor/magento/framework/View/TemplateEngine/Php.php(59): include() #1 /var/www/html/vendor/magento/framework/View/Element/Template.php(271): Magento\Framework\View\TemplateEngine\Php->render(Object(Magento\Catalog\Block\Product\View\AddTo\Compare), '/var/www/html/v...', Array) #2 /var/www/html/vendor/magento/framework/View/Element/Template.php(301): Magento\Framework\View\Element\Template->fetchView('/var/www/html/v...') #3 /var/www/html/vendor/magento/framework/View/Element/AbstractBlock.php(1099): Magento\Framework\View\Element\Template->_toHtml() #4 /var/www/html/vendor/magento/framework/View/Element/AbstractBlock.php(1103): Magento\Framework\View\Element\AbstractBlock->Magento\Framework\View\Element   {closure} () #5 /var/www/html/vendor/magento/framework/View/Element/ in /var/www/html/var/view_preprocessed/pub/static/vendor/magento/module-catalog/view/frontend/templates/product/view/addto/compare.phtml
  on line 1
```

## Wenden Sie den Patch an

Verwenden Sie je nach Adobe Commerce-Produkt die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie im Abschnitt [Im QPT-Tool verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
