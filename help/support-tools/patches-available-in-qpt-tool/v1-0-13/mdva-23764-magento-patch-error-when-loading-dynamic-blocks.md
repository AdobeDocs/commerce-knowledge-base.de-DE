---
title: 'MDVA-23764 Magento Patch: error when loading dynamic blocks'
description: Der MDVA-23764 Magento Patch behebt den Fehler in
exl-id: b884ade6-f88d-4c79-8e84-5a59252abb75
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# MDVA-23764 Magento Patch: Fehler beim Laden von dynamischen Bausteinen

Der MDVA-23764 Magento Patch behebt den Fehler in

```php
JsFooterPlugin.php
```

die sich auf die Anzeige dynamischer Blöcke auswirkt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13 installiert ist. Bitte beachten Sie, dass das Problem in Magento 2.3.5 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Magento-Version erstellt:** Magento Commerce Cloud 2.3.3.

**Kompatibel mit Magento-Versionen:** Magento Commerce und Magento Commerce Cloud 2.3.2 - 2.3.4-p2.

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Zu reproduzierende Schritte:</u>

Versuchen Sie, eine URL zu laden, die wie folgt aussieht: https://\[magento domain\]/banner/ajax/load/.

<u>Tatsächliches Ergebnis:</u>

Ein Fehler ähnlich dem folgenden wird ausgegeben: *Uncaught TypeError: strpos() erwartet, dass der Parameter 1 eine Zeichenfolge ist, null, angegeben in..(Codezeile)* .

<u>Erwartetes Ergebnis:</u>

URL wird ohne Fehler geladen.

## Wenden Sie den Patch an

Anweisungen zum Anwenden eines QPT-Patches finden Sie unter den folgenden Links je nach Magento-Produkt:

* Magento Commerce: DevDocs [Anwenden von Patches mithilfe des Tools &quot;Qualitätsmuster&quot;](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) .
* Magento Commerce Cloud: DevDocs [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) .

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) .
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md), ob für Ihr Magento-Problem ein Patch verfügbar ist.

Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie im Abschnitt [Im QPT-Tool verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
