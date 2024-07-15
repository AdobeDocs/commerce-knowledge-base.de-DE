---
title: "MDVA-30102: Redis-Cache wird voll"
description: Der Patch MDVA-30102 behebt das Problem, dass der Redis-Cache voll ist und Fehler generiert, was zu Problemen mit Produktlistingpages (PLP) und Produktdetailseiten (PDP) führt, z. B. fehlende Produkte. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.6 installiert ist.
exl-id: 34772296-8c93-471c-b5ad-6815adb78ca6
feature: Cache, Categories, Services
role: Admin
source-git-commit: 324cce66df1e4ab7ec4ef8fb6512c3acbabdf3ab
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 0%

---

# MDVA-30102: Redis-Cache wird vollständig

Der Patch MDVA-30102 behebt das Problem, dass der Redis-Cache voll ist und Fehler generiert, was zu Problemen mit Produktlistingpages (PLP) und Produktdetailseiten (PDP) führt, z. B. fehlende Produkte. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.6 installiert ist.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce auf Cloud-Infrastruktur 2.3.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.2 - 2.4.1-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Redis-Cache wird voll, und die zugewiesene `maxmemory` scheint nicht ausreichend zu sein. Der Layout-Cache verfügte nicht über TTL und wurde nicht entfernt, was zu Cache-Wachstum und Entfernung anderer Schlüssel in Redis führte. Daher wurde der gesamte Redis-Speicher für den Layout-Cache zugewiesen.

<u>Voraussetzungen</u>:

* Der Benutzer muss über Adobe Commerce 2.4 verfügen und über einfache 100.000 Produkte (Produkttyp spielt keine Rolle) und 50 Kategorien verfügen.
* Der Redis-Cache muss entsprechend den Schritten konfiguriert werden, die im [Adobe Commerce-Konfigurationshandbuch > Redis für die Adobe Commerce-Seite und im Standard-Cache](https://devdocs.magento.com/guides/v2.4/config-guide/redis/redis-pg-cache.html#example-command) in unserer Entwicklerdokumentation beschrieben werden.

<u>Zu reproduzierende Schritte</u>:

1. Durchsuchen Sie alle Produktdetailseiten und Produktdetailseiten. Sie können [OWASP ZAP](https://www.zaproxy.org/) verwenden, um die Site zu durchsuchen.
1. Beachten Sie die Redis-Speicherbelegung.
1. Überprüfen Sie auch die aktuelle Konfiguration und den verwendeten Speicher. Führen Sie den folgenden Befehl in der CLI aus. Es wird nach verwendetem Speicher, Maxmemory, entfernten Schlüsseln und Redist up-Zeit in Tagen überprüft:

```
redis-cli -p REDIS_PORT -h REDIS_HOST info | egrep --color "(role|used_memory_peak|maxmemory|evicted_keys|uptime_in_days)"
```

<u>Erwartete Ergebnisse</u>:

Der Redis-Cache sollte nicht schnell wachsen.

<u>Tatsächliche Ergebnisse</u>:

Der Redis-Cache wächst auf ca. 5 GB. Es gibt eine maximale Speicherkapazität von 8 GB Redis-Speicher. Wenn Sie also 1M-Produkte haben, wird Ihnen der Speicher sehr schnell ausgehen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
