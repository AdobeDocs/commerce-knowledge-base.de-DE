---
title: "MDVA-34847: customer_grid_flach table slow queries"
description: Der Patch MDVA-34847 löst das Problem, dass langsame Abfragen in der Tabelle "customer_grid_flach"auftreten. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.3 behoben wurde.
exl-id: e91cb86d-83cd-4267-a132-64465a57da7f
feature: Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# MDVA-34847: customer_grid_flache Tabelle für langsame Abfragen

Der Patch MDVA-34847 behebt das Problem, bei dem langsame Abfragen in der Tabelle `customer_grid_flat` auftreten. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.3.3

**Kompatibel mit Adobe-Versionen:**

Adobe Commerce über Cloud-Infrastruktur und Adobe Commerce vor Ort 2.3.0 - 2.4.2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Langsame Abfragen treten in der Tabelle `customer_grid_flat` auf.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie einen Admin-Benutzer mit einem benutzerdefinierten Bereich (Beispiel: Legen Sie **GWS** = *0,* fest und wählen Sie die vorhandene Standardwebsite mit **ID** = *1* aus.)
1. Erstellen Sie alle Produkt- und Kategorieelemente.
1. Platzieren Sie eine Bestellung vom Frontend aus.
1. Melden Sie sich bei Admin als neuer Benutzer an.
1. Gehen Sie zum Raster Verkauf (**Verkauf > Bestellungen**).
1. Überprüfen Sie, ob die SQL-Abfrage an DB (Datenbank) gesendet wurde.

<u>Erwartete Ergebnisse</u>:

Die Admin GWS-Erweiterung sollte

```sql
int
```

Werte von

```sql
website_id
```

in SQL-Bedingungen, wie erwartet:

```sql
main_table.website_id IN (1)
```

<u>Tatsächliche Ergebnisse</u>:

Die Admin GWS-Erweiterung hat eine Bedingung mit

```sql
website_id
```

Wert als

```sql
string
```

, wie:

```sql
main_table.website_id IN ('1')
```

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) verfügbare Patches.
