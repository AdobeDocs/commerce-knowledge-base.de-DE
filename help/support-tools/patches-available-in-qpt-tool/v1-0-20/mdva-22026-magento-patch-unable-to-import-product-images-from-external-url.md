---
title: "MDVA-22026: Kann keine Produktbilder von externen URLs importieren"
description: Der Patch MDVA-22026 behebt das Problem, dass keine Produktbilder von einer externen URL importiert werden können.
exl-id: 29043c6c-daf2-4925-85bf-49eeeee3742c
feature: Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# MDVA-22026: Kann keine Produktbilder von externen URLs importieren

Der Patch MDVA-22026 behebt das Problem, dass keine Produktbilder von einer externen URL importiert werden können.

Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 ist installiert. Die Patch-ID lautet MDVA-22026. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.3.4 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce auf Cloud-Infrastruktur 2.3.2-p2

**Kompatibel mit Adobe Commerce-Versionen:** Adobe Commerce vor Ort und Adobe Commerce über Cloud-Infrastruktur 2.3.2-2.3.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie in Admin zu **System** > **Import**.
1. Satz **Entitätstyp** = *Produkte*.
1. Satz **Importverhalten** = *Hinzufügen/Aktualisieren*.
1. Satz **Anzahl zulässiger Fehler** = *10000*.
1. Wählen Sie die zu importierende Datei aus.
1. Klicken Sie auf **Daten überprüfen** -Schaltfläche (die die Datei validieren soll).
1. Klicken Sie auf **Import** Schaltfläche.

<u>Erwartete Ergebnisse</u>:

Erfolgreicher Import von Produkten aus CSV-Dateien, einschließlich Bildern aus externen URLs, wie erwartet.

<u>Tatsächliche Ergebnisse</u>:

Fehlgeschlagener Import von Produkten aus CSV-Dateien, einschließlich Bildern von externen URLs, und ähnlicher Fehler:

```php
1. Imported resource (image) could not be downloaded from external resource due to timeout or access permissions in row(s): 4, 5, 8, 9, 16, 18, 20, 21, 22, 23, 26, 27, 28, 52, 53, 55, 58, 63, 70, 71, 77, 78, 83, 84, 91
```

## Wenden Sie den Patch an

Um einzelne Patches anzuwenden, verwenden Sie je nach Bereitstellungsmethode die folgenden Links:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html).
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html).

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Überprüfen Sie den Patch auf Adobe Commerce-Problem mit dem Tool für Qualitätsmuster .](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Weitere Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie im Abschnitt [Im QPT-Tool verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) Abschnitt.
