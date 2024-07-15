---
title: "MDVA-34474: Aktualisierung der API-Anforderungsliste führt zu Fehlern"
description: Der Patch MDVA-34474 behebt das Problem, bei dem das Hinzufügen eines Produkts zur Anforderungsliste mit API zu einem Fehler führt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 installiert ist. Die Patch-ID lautet MDVA-34474. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.
exl-id: dc39c4f7-417c-45ea-914c-32f7305527da
feature: REST, B2B
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# MDVA-34474: Aktualisierung der API-Anforderungsliste führt zu Fehlern

Der Patch MDVA-34474 behebt das Problem, bei dem das Hinzufügen eines Produkts zur Anforderungsliste mit API zu einem Fehler führt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 installiert ist. Die Patch-ID lautet MDVA-34474. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.4.0

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce vor Ort und Adobe Commerce über Cloud-Infrastruktur 2.3.0 - 2.4.2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das Hinzufügen eines Produkts zur Anforderungsliste mithilfe der API führt zu Fehlern.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie die Anforderungsliste in Admin (**Geschäfte** > **Konfiguration** > **Allgemein** > **B2B-Funktionen** > **Anforderungsliste aktivieren** = *Ja*).
1. Erstellen Sie einen Kunden.
1. Erstellen Sie eine neue Anforderungsliste für diesen Kunden-Versandaufruf ```json    POST rest/all/V1/requisition_lists``` mit der angehängten JSON-Payload.

<u>Erwartete Ergebnisse</u>:

Kein Fehler und die Liste wird erstellt.

<u>Tatsächliche Ergebnisse</u>:

400-Fehler.

```json
{"message":"Could not save Requisition List"}
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
