---
title: "MDVA-29389: Cron-Auftrag für erweiterte Berichterstellung schlägt fehl"
description: 'Der Patch "MDVA-29389"behebt das Problem, bei dem mit der erweiterten Berichterstellung der Cronjob "analytics_collect_data"Folgendes besagt: "Port muss innerhalb des Hostparameters konfiguriert werden (wie localhost:3306)*". Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 installiert ist. Die Patch-ID lautet MDVA-29389. Das Problem wurde in Adobe Commerce 2.4.2 behoben."'
exl-id: eee909d5-9d0d-46b6-846a-665f89db0eee
feature: Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# MDVA-29389: Cron-Auftrag für erweiterte Berichterstellung schlägt fehl

Der Patch MDVA-29389 behebt das Problem, bei dem bei der erweiterten Berichterstellung die Variable `analytics_collect_data` Cronjob sagt: &quot;*Der Port muss innerhalb des Host-Parameters konfiguriert werden (z. B. localhost:3306).*&quot;. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 ist installiert. Die Patch-ID lautet MDVA-29389. Das Problem wurde in Adobe Commerce 2.4.2 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4.

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.1.

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie in Ihrer Adobe Commerce-Instanz die Option Erweiterte Berichterstellung .
1. Führen Sie die folgende Abfrage aus, um den Wert analytics/general/token in die DB einzufügen:

   ```sql
   INSERT INTO core_config_data VALUES(NULL,'default',0,'analytics/general/token','ABCDE',now());
   ```

1. Öffnen Sie die Datei env.php und fügen Sie Port zum Host-Parameter in der DB-Konfiguration im folgenden Format hinzu: `'host' => 'hostname:port',`
1. Löschen Sie den Cache.
1. Führen Sie die `analytics_collect_data` Cron-Auftrag.

<u>Erwartete Ergebnisse</u>:

Die `analytics_collect_data` Auftrag wird erfolgreich ausgeführt, wenn der standardmäßige oder nicht standardmäßige Port in env.php verwendet wird, um eine Verbindung zu MySQL herzustellen.

<u>Tatsächliche Ergebnisse</u>:

Die `analytics_collect_data` Auftrag gibt einen Fehler aus *Der Port muss innerhalb des Host-Parameters konfiguriert werden (z. B. localhost:3306).*&quot;, wenn in env.php eine Verbindung mit MySQL über einen nicht standardmäßigen Port hergestellt wird.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
