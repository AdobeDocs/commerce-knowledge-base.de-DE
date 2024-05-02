---
title: '"MDVA-34886: keine Suchergebnisse bei Verwendung des Attributs "Gewichtung"'
description: Der Patch MDVA-34886 löst das Problem, dass die Suche Ergebnisse zurückgibt, wenn das Gewichtungsattribut als durchsuchbar konfiguriert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.3 behoben wurde.
exl-id: e6f33772-0167-4a54-9d62-0ab89edb5d1d
feature: Attributes, Cache, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# MDVA-34886: keine Suchergebnisse bei Verwendung des Attributs &quot;Gewichtung&quot;

Der Patch MDVA-34886 löst das Problem, dass die Suche Ergebnisse zurückgibt, wenn das Gewichtungsattribut als durchsuchbar konfiguriert ist. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.3.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce über Cloud-Infrastruktur und Adobe Commerce vor Ort 2.3.2 - 2.4.2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Suche gibt Ergebnisse zurück, wenn das Gewichtungsattribut als durchsuchbar konfiguriert ist.

<u>Zu reproduzierende Schritte</u>:

1. Konfigurieren Sie Elasticsearch.
1. Navigieren Sie zu **Admin** > **Stores** > **Attribute** > **Produkt**. Bearbeiten Sie die **Gewichtung** -Attribut und legen Sie sein -Attribut fest. **Durchsuchbar** = *Ja*.
1. Speichern Sie das Attribut und leeren Sie den Konfigurations-Cache.
1. Suchen Sie auf der Vorderseite nach einem Textwert (Beispiel: *bag*).
1. Beachten Sie, dass die Suche keine Ergebnisse zurückgibt.
1. Das Ausnahmeprotokoll enthält eine Fehlermeldung wie die folgende:

```php
{"type":"number_format_exception","reason":"For input string: \"bag\""}
```

<u>Erwartete Ergebnisse</u>:

Die Suche gibt Ergebnisse zurück, selbst wenn das Gewichtungsattribut wie erwartet als durchsuchbar konfiguriert ist.

<u>Tatsächliche Ergebnisse</u>:

Die Suche gibt keine Ergebnisse zurück, wenn das Gewichtungsattribut als durchsuchbar konfiguriert ist.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) Abschnitt.
