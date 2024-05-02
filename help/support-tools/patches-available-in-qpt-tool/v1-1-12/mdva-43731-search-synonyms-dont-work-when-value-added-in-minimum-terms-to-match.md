---
title: '"MDVA-43731: Suchsynonyme funktionieren nicht, wenn unter "Mindestbegriffe für Übereinstimmung"ein Wert hinzugefügt wird."'
description: Der Patch MDVA-43731 behebt das Problem, dass Suchsynonyme nicht mehr funktionieren, wenn ein Wert unter "Mindestbegriffe"hinzugefügt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-43731. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: b795989c-d10b-443e-aebe-f3859930396a
feature: Cache, Marketing Tools, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 0%

---

# MDVA-43731: Suchsynonyme funktionieren nicht, wenn unter &quot;Mindestbegriffe&quot;ein Wert hinzugefügt wird.

Der Patch MDVA-43731 behebt das Problem, dass Suchsynonyme nicht mehr funktionieren, wenn ein Wert unter &quot;Mindestbegriffe&quot;hinzugefügt wird. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-43731. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Suchsynonyme funktionieren nicht mehr, wenn unter &quot;Mindestbegriffe&quot;ein Wert hinzugefügt wird.

<u>Zu reproduzierende Schritte</u>:

1. Installieren Sie Adobe Commerce mit Beispieldaten.
1. Konfigurieren Sie Elasticsearch7 als Suchmaschine.
1. Suchen Sie nach &quot;Jacket&quot;. Eine Liste der Produkte wird angezeigt.
1. Parameter hinzufügen [4&lt;60%] in **Konfiguration** > **Katalog** > **Katalogsuche** > **Mindestens passende Begriffe**.
1. Löschen Sie den Konfigurationscache und führen Sie eine Neuindizierung durch.
1. Suchen Sie erneut nach dem Wort &quot;Jacket&quot; und beachten Sie, dass eine Liste von Produkten angezeigt wird.
1. Navigieren Sie zu **Marketing** > **SEO und Suche** > **Synonyme suchen**.
1. Erstellen Sie Synonyme für die Suche, indem Sie die folgenden Synonyme hinzufügen: Jacke, Bagtecs, Express plus.
1. Führen Sie eine Neuindizierung durch.
1. Führen Sie eine Produktsuche mit einem der Synonyme durch. Beispiel: Jacke.

<u>Erwartete Ergebnisse</u>:

Sie erhalten dieselbe Produktliste wie zuvor in den Suchergebnissen.

<u>Tatsächliche Ergebnisse</u>:

In den Suchergebnissen wird kein Produkt angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
