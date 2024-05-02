---
title: '"MDVA-32655: "quoteItemCleaner" consumer führt pro Ausführung eine Nachricht aus."'
description: Der Patch MDVA-32655 behebt den falschen Nachrichtenstatus "Gestartet"auf die richtige "vollständige"Nachricht für den Verbraucher "quoteItemCleaner", nachdem mehrere Produkte gelöscht wurden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 installiert ist. Die Patch-ID ist 32655. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben sein soll.
exl-id: 07213430-f779-4a53-89fd-bc3905e13675
feature: Quotes
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-32655: &quot;quoteItemCleaner&quot; Consumer führt pro Ausführung eine Nachricht aus

Der Patch MDVA-32655 behebt den falschen Status der &quot;In Bearbeitung&quot;-Nachricht auf die richtige &quot;vollständige&quot; Nachricht für den Verbraucher `quoteItemCleaner` nach dem Löschen mehrerer Produkte. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 installiert ist. Die Patch-ID ist 32655. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.3.3

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce über Cloud-Infrastruktur und Adobe Commerce vor Ort 2.3.0 - 2.4.2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die `quoteItemCleaner` Der Benutzer führt bei jeder Ausführung nur eine Nachricht aus.

<u>Zu reproduzierende Schritte</u>:

1. Überprüfen Sie die `queue_message_status` Datenbanktabelle und stellen Sie sicher, dass alle vorhandenen Warteschlangennachrichten den Status &quot;Abgeschlossen&quot; aufweisen (Status-ID 4).
1. Beenden Sie die automatische Ausführung des Adobe Commerce-Crons.
1. Erstellen Sie zwei oder drei einfache Produkte.
1. Führen Sie eine Massenlöschung für diese drei einfachen Produkte durch.
1. Im `queue_message_status` -Tabelle sehen, dass es drei neue Datensätze für die `catalog_product_removed_queue` Thema mit Status-ID 2 (neuer Datensatz).
1. Führen Sie den folgenden Befehl aus, um diese ausstehenden Elemente zu verarbeiten `catalog_product_removed_queue` messages:

   ```bash
   bin/magento queue:consumers:start quoteItemCleaner --single-thread --max-messages=100
   ```

<u>Erwartete Ergebnisse</u>:

```sql
select * from queue_message_status s join queue q on s.queue_id = q.id where q.name = "catalog_product_removed_queue";
```

Alle `catalog_product_removed_queue` -Nachrichtenstatus aktualisiert und abgeschlossen (ID = 4).

<u>Tatsächliche Ergebnisse</u>:

Nur ein Datensatz von drei wird auf den Status &quot;Abgeschlossen&quot;aktualisiert (ID = 4). Der Status der beiden anderen Nachrichten lautet Status-ID = 3 (in Bearbeitung). Ein Rückstand wird mit nicht verarbeiteten Warteschlangennachrichten generiert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
