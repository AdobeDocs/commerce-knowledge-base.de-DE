---
title: "MDVA-31021: Langsamer Import und Export bei vielen Produktoptionen"
description: Der Patch MDVA-31021 behebt das Problem, wenn Import/Export bei einer großen Anzahl von Produktoptionen länger dauert als erwartet. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 installiert ist.
exl-id: d294b30d-b734-4bd6-bf1a-c116b789a63c
feature: Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# MDVA-31021: Langsamer Import und Export bei vielen Produktoptionen

Der Patch MDVA-31021 behebt das Problem, wenn Import/Export bei einer großen Anzahl von Produktoptionen länger dauert als erwartet. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 installiert ist.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce in Cloud-Infrastruktur 2.3.1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn die Tabelle `catalog_product_option` mindestens 100.000 Datensätze enthält, dauert die Validierung der Datei für die Import/Export-Funktion länger als erwartet. Vor Import/Export zur Aktivierung der Optionsüberprüfung lädt Adobe Commerce Produktoptionen für alle vorhandenen Produkte.

<u>Voraussetzungen</u>:

Adobe Commerce Store mit 5000 Produkten mit benutzerdefinierten Optionen. Jedes Produkt sollte mindestens vier benutzerdefinierte Optionen mit zwei oder mehr Optionen zur Auswahl haben, sodass in der Tabelle `catalog_product_option` 100.000 Datensätze enthalten sind.

<u>Zu reproduzierende Schritte</u>:

1. Beispiel für einen **Import**: Erstellen Sie eine CSV-Importdatei mit einer der SKUs aus dem Commerce-Administrator.
1. Fügen Sie der CSV-Importdatei vier benutzerdefinierte Optionen hinzu.
1. Versuchen Sie, die CSV-Datei vom Commerce-Administrator zu importieren.

<u>Erwartete Ergebnisse</u>:

Die Import- oder Exportfunktion wird wie erwartet ausgeführt. Die Validierung dauert weniger als 10 Sekunden, bis sie mit einem Produkt abgeschlossen ist.

<u>Tatsächliche Ergebnisse</u>:

Die Import- oder Exportfunktion nimmt länger als erwartet in Anspruch. Die Validierung dauert mehr als 10 Sekunden, bis sie mit nur einem Produkt abgeschlossen ist.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
