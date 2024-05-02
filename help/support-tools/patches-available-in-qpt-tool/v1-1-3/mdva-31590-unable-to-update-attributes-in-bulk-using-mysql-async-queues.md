---
title: "MDVA-31590: Attribute können nicht stapelweise mithilfe asynchroner MySQL-Warteschlangen aktualisiert werden"
description: Der Patch MDVA-31590 behebt das Problem, dass die Benutzer keine Attribute stapelweise mit asynchronen MySQL-Warteschlangen aktualisieren können. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.3 installiert ist. Die Patch-ID lautet MDVA-31590. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.
exl-id: 57db28dd-a739-4a77-927d-6339af4fa4a6
feature: Attributes, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 0%

---

# MDVA-31590: Attribute können nicht stapelweise mithilfe asynchroner MySQL-Warteschlangen aktualisiert werden

Der Patch MDVA-31590 behebt das Problem, dass die Benutzer keine Attribute stapelweise mit asynchronen MySQL-Warteschlangen aktualisieren können. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.3 installiert ist. Die Patch-ID lautet MDVA-31590. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0-2.4.1-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Benutzer können Attribute nicht stapelweise mit MySQL async aktualisieren.

<u>Zu reproduzierende Schritte</u>:

1. Führen Sie im Produktraster im Backend eine Massenaktion durch, um Attributwerte für einige Produkte zu aktualisieren.
   * Produkte überprüfen und auswählen **Attribute aktualisieren** aus dem Dropdown-Menü Aktionen .
1. Legen Sie Werte für die erforderlichen Attribute fest, weisen Sie den Websites Produkte zu und speichern Sie sie.
1. Sobald die Seite neu geladen wird, wird eine Meldung wie die folgende angezeigt:
   *Aufgabe &quot;Attribute für N ausgewählte Produkte aktualisieren&quot;: 1 Element(e) wurde für eine Aktualisierung geplant.*
1. Warten Sie einige Sekunden und laden Sie die Backend-Seite neu.

<u>Erwartete Ergebnisse</u>:

1. Auf der Seite wird eine erfolgreiche Aktualisierungsmeldung angezeigt, z. B.: *1 Elemente wurden erfolgreich aktualisiert.*
1. Attributwerte für verwandte Produkte werden aktualisiert.
1. In DB werden neue Datensätze in beiden erstellt `magento_bulk` Tabelle und `magento_operation` -Tabelle (Vorgänge im Zusammenhang mit der Masse).
1. Neue Datensätze werden im `queue_message` -Tabelle (bezogen auf die Warteschlangen) `product_action_attribute.update` und/oder `product_action_attribute.website.update`).
1. `queue_message_status` -Tabelle enthält Datensätze mit dem Status &quot;4&quot;.
1. Es gibt KEINE Fehler in `system.log`.

<u>Tatsächliche Ergebnisse</u>:

1. Auf der Seite wird weiterhin eine Meldung wie die folgende angezeigt:
   *Aufgabe &quot;Attribute für N ausgewählte Produkte aktualisieren&quot;: 1 Element(e) wurde für eine Aktualisierung geplant.*
1. Attributwerte für die Produkte werden aktualisiert.
1. Ein neuer Datensatz wird erstellt in `message_bulk` -Tabelle, aber es gibt keine zugehörigen Datensätze in `magento_operation` Tabelle.
1. Neue Datensätze werden in `queue_message` und `queue_message_status` -Tabellen.
1. `queue_message_status` -Tabelle enthält Datensätze mit Fehlerstatus (Statuswert &quot;6&quot;).
1. `system.log` enthält einen Fehler ähnlich dem folgenden:
   *main.CRITICAL: Nachricht wurde zurückgewiesen: SQLSTATE[23000]: Integrity constraint verletzungen: 1048 Spalte &#39;operation_key&#39; kann nicht null sein, Abfrage war: INSERT INTO {{magento_operation}} ({{id}}, {{bulk_uuid}}, {{topic_name}}, {{serialized_data}}, {{result_serialized_data}}, {{status}}, {{error_code}}, {{result_message}}, {{operation_key}}) WERTE (?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?) [][]*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) Abschnitt.
