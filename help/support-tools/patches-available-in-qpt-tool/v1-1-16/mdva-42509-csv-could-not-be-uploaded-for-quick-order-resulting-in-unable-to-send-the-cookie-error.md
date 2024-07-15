---
title: '"MDVA-42509: CSV konnte nicht für schnelle Bestellung hochgeladen werden, was zu dem Fehler "Cookie kann nicht gesendet werden"führte.'
description: Der MDVA-42509-Patch behebt das Problem, dass eine CSV-Datei nicht für eine schnelle Bestellung hochgeladen werden konnte, was dazu führte, dass der Cookie-Fehler nicht gesendet werden konnte. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 installiert ist. Die Patch-ID lautet MDVA-42509. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: 7aa0e710-9a28-4531-b9cb-c82f654487f4
feature: B2B, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# MDVA-42509: CSV konnte nicht für schnelle Bestellung hochgeladen werden, was zu dem Fehler &quot;Cookie kann nicht gesendet werden&quot;führte

Der Patch MDVA-42509 behebt das Problem, dass eine CSV-Datei nicht für eine schnelle Bestellung hochgeladen werden konnte, was dazu führte, dass der Fehler *Cookie konnte nicht gesendet werden* angezeigt wurde. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 installiert ist. Die Patch-ID lautet MDVA-42509. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.3 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn Sie mithilfe einer CSV-Datei eine schnelle Bestellung mit einer großen Anzahl von Produkten erstellen, wird ein Cookie-Fehler angezeigt: *Cookie kann nicht gesendet werden*

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie die Schnellreihenfolge, indem Sie zu **Stores** > **Einstellungen** > **Konfigurationen** > **Allgemein** > **B2B-Funktionen** navigieren.
1. Erstellen Sie ein Kundenkonto und gehen Sie zu **Quick Order** am oberen Link.
1. Versuchen Sie, eine schnelle Bestellung mithilfe einer CSV-Datei mit mehr als 100 SKUs zu erstellen.

<u>Erwartete Ergebnisse</u>:

Sie können eine schnelle Bestellung mit einer großen Anzahl von SKUs erstellen.

<u>Tatsächliche Ergebnisse</u>:

Eine Fehlermeldung wird in Bezug auf die Cookie-Größe angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
