---
title: 'MDVA-28409 Patch: Absturz des Adobe Commerce-Webservers - Nicht genügend Arbeitsspeicher'
description: Der Patch MDVA-28409 löst das Problem, dass der Cron-Auftrag zum Entfernen von Anführungszeichen aufgrund der Verarbeitung einer großen Anzahl von Artikeln angehalten wurde. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.5 installiert ist.
exl-id: 175e5f2f-2f76-42ee-83e9-c1b23ff81e96
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# MDVA-28409 Patch: Absturz des Adobe Commerce-Webservers - Nicht genügend Speicher

Der Patch MDVA-28409 löst das Problem, dass der Cron-Auftrag zum Entfernen von Anführungszeichen aufgrund der Verarbeitung einer großen Anzahl von Artikeln angehalten wurde. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.5 installiert ist.

## Betroffene Produkte und Versionen

Adobe Commerce vor Ort und Adobe Commerce über Cloud-Infrastruktur 2.3.4 - 2.3.5, 2.4.0

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das Problem besteht darin, dass dem Cron-Auftrag aufgrund der Datenmenge, die der Auftrag verarbeiten möchte, der Arbeitsspeicher ausgegangen ist. Zu den Symptomen dieses Problems gehören eine langsame Leistung aufgrund der hohen Festplattenauslastung von MySQL und des niedrigen Webserver-Speichers.

<u>Zu reproduzierende Schritte:</u>

Führen Sie die folgende Abfrage aus, um zu überprüfen, ob ein Cron-Auftrag vorhanden ist, der veraltete Anführungszeichen nicht entfernen kann:

```
select * from cron_schedule where job_code like '%sales_clean_quotes%'
```

<u>Erwartetes Ergebnis:</u>

Der Status des Cron-Auftrags `sales_clean_quotes` sollte `success` sein.

<u>Tatsächliches Ergebnis:</u>

Der Status des Cron-Auftrags `sales_clean_quotes` ist `running` oder `error`.

Eine andere Möglichkeit, zu bestätigen, dass ein Cron-Auftrag nicht in der Lage ist, veraltete Anführungszeichen zu entfernen, besteht darin, die Ausgabe aus der Abfrage von **Schritt 1** (`executed_at`) den Zeitstempeln aller Speicherfehler in `/var/log/cron.log` zuzuordnen. Wenn es einen Cron-Auftrag gibt, der nicht in der Lage ist, die Datenmenge zu verarbeiten, wird möglicherweise eine Nachricht ähnlich der folgenden angezeigt:

```
PHP Fatal error:  Allowed memory size of 1073741824 bytes exhausted (tried to allocate 4096 bytes) in /app/vendor/magento/framework/DB/Statement/Pdo/Mysql.php on line 91

Fatal error: Allowed memory size of 1073741824 bytes exhausted (tried to allocate 4096 bytes) in /app/vendor/magento/framework/DB/Statement/Pdo/Mysql.php on line 91
--
[2020-05-30 05:00:27.224718] Launching command 'php bin/magento cron:run'.
```

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) verfügbare Patches.
