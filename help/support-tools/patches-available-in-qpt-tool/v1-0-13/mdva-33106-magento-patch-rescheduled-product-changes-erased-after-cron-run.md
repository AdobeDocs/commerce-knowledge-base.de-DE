---
title: "MDVA-33106 Patch: Neu geplante Produktänderungen wurden nach Cron-Ausführung gelöscht"
description: Der Patch MDVA-33106 behebt das Problem, dass die neu geplanten Produktänderungen nach dem Cron gelöscht werden
exl-id: be32982c-796c-4069-ad70-37b5124ffb56
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-33106 Patch: Neugeplante Produktänderungen wurden nach Cron-Ausführung gelöscht

Der Patch MDVA-33106 behebt das Problem, dass die neu geplanten Produktänderungen nach dem Cron gelöscht werden

```bash
bin/magento cron:run
```

ausgeführt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.3.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce über Cloud-Infrastruktur und Adobe Commerce vor Ort 2.3.0 - 2.4.1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Wechseln Sie in Commerce Admin zu **Katalog** > **Produkte** und klicken Sie auf &quot;Bearbeiten&quot;. Beachten Sie den Wert **Preis**, z. B. *9,99*.
1. Klicken Sie auf **Neues Update planen** und geben Sie Details ein:
   * Der Name der Aktualisierung ist nicht wichtig.
   * Legen Sie ein Datum in der Zukunft fest: +1 Jahr für Start- und Enddatum.
   * Setzen Sie den Preis auf *1,99*.
   * Speichern Sie die Änderungen.
1. Gehen Sie zum Dashboard Inhaltstaging und wählen Sie die Rasteransicht aus, um zu sehen, ob eine geplante Übereinstimmung oben vorliegt.
1. Wählen Sie die Bearbeitungsaktion neben der geplanten Aktualisierung aus. Die Daten sollten weiterhin mit den oben genannten übereinstimmen.
1. Ändern Sie das geplante Datum in etwas näher. Ändern Sie anstelle von +1 Jahr in + 1 Woche oder + 1 Monat.
1. Speichern Sie die Änderungen und überprüfen Sie, ob die Daten im Staging-Dashboard aktualisiert werden.
1. Warten Sie, bis ein Cron-Auftrag ausgeführt wird.
1. Klicken Sie erneut in der geplanten Änderung auf Bearbeiten und überprüfen Sie den Preis.

<u>Erwartete Ergebnisse</u>:

Der Preis ist 1,99.

<u>Tatsächliche Ergebnisse</u>:

Der Preis ist 9,99.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie in der [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
