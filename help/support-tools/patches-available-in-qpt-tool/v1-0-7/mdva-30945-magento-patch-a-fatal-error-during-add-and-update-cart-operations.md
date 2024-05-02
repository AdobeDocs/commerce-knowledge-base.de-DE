---
title: "MDVA-30945: ein schwerwiegender Fehler beim Hinzufügen und Aktualisieren von Warenkorboperationen"
description: Der Patch MDVA-30945 behebt das Problem, dass Sie einen schwerwiegenden Fehler erhalten, *Aufruf an eine Mitgliederfunktion getValue() auf null im Modul-konfigurierbaren Produkt CartItemProcessor.php* bei der Aktualisierung von Warenkörben. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 installiert ist. Das Problem wurde in Adobe Commerce 2.4.2 behoben.
exl-id: 0950e91b-900b-421d-91e7-abbfca4f30be
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# MDVA-30945: ein schwerwiegender Fehler beim Hinzufügen und Aktualisieren von Warenkorboperationen

Der Patch MDVA-30945 behebt das Problem, dass Sie einen schwerwiegenden Fehler erhalten *Rufen Sie eine Mitgliederfunktion getValue() auf null in module-configuring-product CartItemProcessor.php auf.* beim Aktualisieren von Warenkörben. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 ist installiert. Das Problem wurde in Adobe Commerce 2.4.2 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Ein schwerwiegender PHP-Fehler, nachdem Produkte im Warenkorb im Admin aktualisiert wurden.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie in Commerce Admin ein konfigurierbares Produkt ohne Optionen.
1. Fügen Sie ihn dem Warenkorb auf der Storefront hinzu.
1. Kehren Sie zu Admin zurück, fügen Sie dem Produkt konfigurierbare Optionen hinzu und speichern Sie die Änderungen.
1. Aktualisieren Sie die Warenkorbseite im Storefront.

<u>Erwartete Ergebnisse</u>:

Auf der Warenkorbseite wird die folgende Validierungsmeldung angezeigt: *Einige der unten aufgeführten Produkte verfügen nicht über alle erforderlichen Optionen*.

<u>Tatsächliche Ergebnisse</u>:

Die Seite &quot;Warenkorb&quot;ist leer. Im PHP `error.log`, wird der folgende Fehler protokolliert: *Uncaught exception &#39;Error&#39; with message &#39;Call to a member function getValue() on null&#39; in vendor/magento/module-configurable-product/Model/Quote/Item/CartItemProcessor.php:76*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
