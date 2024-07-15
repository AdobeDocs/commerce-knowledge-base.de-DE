---
title: "MDVA-24201: Katalogpreisregeln funktionieren nicht"
description: Der Patch MDVA-24201 löst das Problem, dass die aktiven Katalogpreisregeln in der Datenbank nicht auf der Vorderseite gelten.
exl-id: ae541c40-403a-46e9-a486-2a1e8991f05a
feature: Catalog Management, Categories, Marketing Tools, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# MDVA-24201: Katalogpreisregeln funktionieren nicht

Der Patch MDVA-24201 löst das Problem, dass die aktiven Katalogpreisregeln in der Datenbank nicht auf der Vorderseite gelten.

Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.14 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.3.5 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce in der Cloud-Infrastruktur 2.3.3

**Kompatibel mit Adobe Commerce-Versionen:** Adobe Commerce für Cloud-Infrastruktur und Adobe Commerce On-Premise 2.3.0 - 2.3.4-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Voraussetzung</u>:

Installieren Sie eine neue Magento-Instanz mit Beispieldaten.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich bei **Admin panel** > **Marketing** > **Katalogpreisregel** > **Neue Regel hinzufügen** an und nehmen Sie die folgenden Einstellungen vor:
   1. Legen Sie den **Regelnamen** fest.
   1. Legen Sie **Aktiv** = *Nein* fest.
   1. Bedingungen festlegen: **Kategorie** = *4*. (Beispiel: Tags)
   1. Aktionen festlegen:
      1. Legen Sie **Anwenden auf** fest.   **Prozentsatz des Originals**.
      1. Legen Sie **Discount Amount** = *10* fest.
      1. Speichern Sie und fahren Sie mit der Bearbeitung fort.
   1. Klicken Sie auf **Neues Update planen**:
      * Legen Sie den **Regelnamen** fest.
      * Setzen Sie **aktiv** = *Ja*.
      * Speichern Sie.
1. Wechseln Sie zum Backend und führen Sie Folgendes aus:

   `php    bin/magento cron:run`

<u>Erwartete Ergebnisse</u>:

Die Preise der Erzeugnisse der Kategorie 4 &quot;Taschen&quot; sollten um 10 % des ursprünglichen Preises gesenkt werden, wie dies in der Katalogpreisregel vorgesehen ist.

<u>Tatsächliche Ergebnisse</u>:

Preisänderungen treten auch dann nicht auf, wenn die Katalogpreisregel aktiv ist.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) verfügbare Patches.
