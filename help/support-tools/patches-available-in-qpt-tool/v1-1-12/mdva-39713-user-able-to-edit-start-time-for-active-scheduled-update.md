---
title: "MDVA-39713: Benutzer kann die Startzeit einer geplanten aktiven Aktualisierung bearbeiten"
description: Der Patch MDVA-39713 behebt das Problem, dass ein Benutzer die Startzeit eines aktiven geplanten Updates bearbeiten kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-39713. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: c7221fdb-5fc0-4179-8d4c-c9e1f0d00692
feature: CMS
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# MDVA-39713: Benutzer kann die Startzeit einer geplanten aktiven Aktualisierung bearbeiten

Der Patch MDVA-39713 behebt das Problem, dass ein Benutzer die Startzeit eines aktiven geplanten Updates bearbeiten kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-39713. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.3.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Benutzer kann die Startzeit für eine aktive geplante Aktualisierung bearbeiten.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie neue CMS-Seiten.
1. Wählen Sie **Neues Update planen** und setzen Sie das **Startdatum** auf die aktuelle +1-Minute-Zeit.
1. Aktivieren Sie das geplante Update, indem Sie den Befehl `bin/magento cron:run --group=staging` in der lokalen Umgebung ausführen. Warten Sie einige Minuten und überprüfen Sie, ob der Zeitplan aktiv ist.
1. Sobald der Zeitplan aktiv ist, aktualisieren Sie die Seite.
1. Klicken Sie im Abschnitt &quot;Geplante Änderungen&quot;auf **Anzeigen/Bearbeiten** .
1. Bearbeiten Sie die Zeit, indem Sie +2 Minuten hinzufügen und speichern Sie die Änderung.
1. Speichern Sie die CMS-Seite.
1. Führen Sie erneut den folgenden Befehl aus: `bin/magento cron:run --group=staging`.
1. Klicken Sie auf **Anzeigen/Bearbeiten** des geplanten Updates.

<u>Erwartete Ergebnisse</u>:

Der Benutzer kann die Startzeit für eine aktive geplante Aktualisierung nicht bearbeiten.

<u>Tatsächliche Ergebnisse</u>:

Der Benutzer erhält einen Fehler wie *Element (Magento\Cms\Model\Page) mit der gleichen ID &quot;11&quot;bereits vorhanden.*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
