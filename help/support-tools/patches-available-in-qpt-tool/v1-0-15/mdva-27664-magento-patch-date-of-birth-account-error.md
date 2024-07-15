---
title: "MDVA-27664 Patch: Geburtsdatum des Fehlers des Kontos"
description: Der Patch MDVA-27664 behebt das Problem, dass das Geburtsdatum eines Kundenkontos höher sein könnte als heute.
exl-id: c669764e-b4a5-4031-92ac-1156755e9a0a
feature: Customer Service
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# MDVA-27664 Patch: Geburtskontenfehler

Der Patch MDVA-27664 behebt das Problem, dass das Geburtsdatum eines Kundenkontos höher sein könnte als heute.

Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.3.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce für die Cloud-Infrastruktur 2.3.4-p2

**Kompatibel mit Adobe Commerce-Versionen:** Adobe Commerce für Cloud-Infrastruktur und Adobe Commerce On-Premise 2.3.4 - 2.3.5-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich beim Administrator an.
1. Legen Sie **Locale** = *en\_GB* (UK) für einen Benutzer fest.
1. Bearbeiten Sie einen Kunden.
1. Wählen Sie ein Geburtsdatum nach dem 12. eines Monats in diesem Jahr aus.

<u>Erwartete Ergebnisse</u>:

Das Geburtsdatum ist gültig, sodass die Kundeninformationen wie erwartet gespeichert werden können.

<u>Tatsächliche Ergebnisse</u>:

Die Kundeninformationen können nicht gespeichert werden, da ein Validierungsfehler auftritt:

```php
The Date of Birth should not be greater than today.
```

wobei anstelle des Datumsformats TT/MM/JJJJ das Datum als Datumsformat MM/TT/JJJJ behandelt wird.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) verfügbare Patches.
