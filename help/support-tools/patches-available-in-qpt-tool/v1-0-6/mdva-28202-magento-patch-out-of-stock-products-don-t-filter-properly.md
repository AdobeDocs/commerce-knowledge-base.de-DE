---
title: "MDVA-28202 Patch: Nicht vorrätige Produkte filtern nicht richtig"
description: Der Patch MDVA-28202 behebt das Problem, dass nicht vorrätige Produkte nicht ordnungsgemäß mit dem **Preis*-Filter auf einem Adobe Commerce Store-Frontend gefiltert werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.6 installiert ist.
exl-id: 45976602-15f3-4fef-9d90-da2b3fe6046d
feature: Catalog Management, Categories, Orders, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-28202 Patch: Nicht vorrätige Produkte filtern nicht richtig

Der Patch MDVA-28202 behebt das Problem, dass nicht vorrätige Produkte nicht ordnungsgemäß mit gefiltert werden **Preis** nach einem Adobe Commerce Store-Frontend filtern. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.6 installiert ist.

## Betroffene Produkte und Versionen

* Der Patch wurde für Adobe Commerce in der Cloud-Infrastruktur 2.3.5-p1 entwickelt.
* Der Patch ist auch mit Adobe Commerce On-Premise und Adobe Commerce in der Cloud-Infrastruktur 2.3.4 - 2.4.1 kompatibel.

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Nicht vorrätige Produkte werden nicht ordnungsgemäß mit **Preis** in der Commerce Admin.

<u>Voraussetzung:</u>

* Satz **Nicht vorrätige Produkte anzeigen** = &quot;*Ja*&quot; unter **Stores > Konfiguration > KATALOG > Bestand > Lageroptionen**.

<u>Zu reproduzierende Schritte:</u>

1. Erstellen Sie ein konfigurierbares Produkt mit zwei einfachen Produkten (Beispiel: Satz **Preis** = *1500 $*).
1. Beide einfachen Produkte sollten beim Erstellen des konfigurierbaren Produkts &quot;nicht vorrätig&quot;sein.
1. Weisen Sie dieses konfigurierbare Produkt einer Kategorie zu.
1. Neu indizieren und überprüfen `catalog_product_index_price` -Tabelle mit der Entitäts-ID des oben konfigurierbaren Produkts.
1. Speichern Sie alle Produktpreise = *0$*.
1. Laden Sie die Kategorie und bestätigen Sie die Verfügbarkeit des Produkts.
1. Öffnen Sie die **Preis** aus der Navigation mit Ebenen.
1. Beachten Sie, dass **Preis** Filter hat die Option &quot; *0,00 $ - 9,99 $* &quot;.
1. Klicken Sie auf das oben stehende **Preis** Filteroption und legen Sie **Preis** = *1500 $* und Sie erhalten das konfigurierbare Produkt, das wir oben erstellt haben.

<u>Erwartetes Ergebnis:</u>

Das Produkt filtert erwartungsgemäß unter die richtige Preisspanne.

<u>Ergebnis:</u>

Das Produkt fällt unter den falschen Filter für die Preisspanne.

## Wenden Sie den Patch an

Um einzelne Patches anzuwenden, verwenden Sie je nach Bereitstellungsmethode die folgenden Links:

* Adobe Commerce oder Magento Open Source vor Ort: [Anwenden von Patches mithilfe des Tools &quot;Qualitätsmuster&quot;](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Weitere Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie im Abschnitt [Im QPT-Tool verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) Abschnitt.

Weitere Informationen zu konfigurierbaren Produkten finden Sie in diesem Artikel in unserer Entwicklerdokumentation: [Konfigurierbares Produkt-Tutorial erstellen](https://devdocs.magento.com/guides/v2.4/rest/tutorials/configurable-product/config-product-intro.html) in unserer Entwicklerdokumentation.
