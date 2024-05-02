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

Der Patch MDVA-31021 behebt das Problem, wenn Import/Export bei einer großen Anzahl von Produktoptionen länger dauert als erwartet. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 ist installiert.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce in Cloud-Infrastruktur 2.3.1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn 100.000 Datensätze oder mehr in der `catalog_product_option` angegeben ist, dauert die Überprüfung der Datei-Import/Export-Funktion länger als erwartet. Vor Import/Export zur Aktivierung der Optionsüberprüfung lädt Adobe Commerce Produktoptionen für alle vorhandenen Produkte.

<u>Voraussetzungen</u>:

Adobe Commerce Store mit 5000 Produkten mit benutzerdefinierten Optionen. Jedes Produkt sollte mindestens vier benutzerdefinierte Optionen mit zwei oder mehr Optionen zur Auswahl haben, sodass 100.000 Datensätze in `catalog_product_option` Tabelle.

<u>Zu reproduzierende Schritte</u>:

1. Für **Import** Beispiel: Erstellen Sie eine CSV-Importdatei mit einer der SKUs vom Commerce Admin.
1. Fügen Sie der CSV-Importdatei vier benutzerdefinierte Optionen hinzu.
1. Versuchen Sie, die CSV-Datei vom Commerce-Administrator zu importieren.

<u>Erwartete Ergebnisse</u>:

Die Import- oder Exportfunktion wird wie erwartet ausgeführt. Die Validierung dauert weniger als 10 Sekunden, bis sie mit einem Produkt abgeschlossen ist.

<u>Tatsächliche Ergebnisse</u>:

Die Import- oder Exportfunktion nimmt länger als erwartet in Anspruch. Die Validierung dauert mehr als 10 Sekunden, bis sie mit nur einem Produkt abgeschlossen ist.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
