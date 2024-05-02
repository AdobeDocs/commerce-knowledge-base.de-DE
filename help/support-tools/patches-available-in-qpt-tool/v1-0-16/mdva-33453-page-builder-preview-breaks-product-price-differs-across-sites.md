---
title: "MDVA-33453: Page Builder-Vorschau bricht den Produktpreis je nach Site ab."
description: Der Patch MDVA-33453 behebt das Problem, bei dem die Seitenaufbau-Vorschau fehlerhaft ist, wenn übereinstimmende Produkte für jede Website einen anderen Preis haben. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben sein soll.
exl-id: 78a7f7d4-8691-4b5d-a900-1c9a6ec73486
feature: CMS, Orders, Page Builder, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-33453: Page Builder-Vorschau unterbricht Produktpreise zwischen Sites unterschiedlich

Der Patch MDVA-33453 behebt das Problem, bei dem die Seitenaufbau-Vorschau fehlerhaft ist, wenn übereinstimmende Produkte für jede Website einen anderen Preis haben. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce in Cloud-Infrastruktur 2.4.1

**Kompatibel mit Adobe Commerce-Versionen:** Adobe Commerce über Cloud-Infrastruktur und Adobe Commerce vor Ort 2.3.6 - 2.4.1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Produktvorschau von Page Builder bricht ab, wenn ein Produkt auf verschiedenen Websites unterschiedliche Preise aufweist.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich beim Commerce Admin-Bedienfeld an.
1. Erstellen Sie zwei Websites.
1. Erstellen Sie ein einfaches Produkt.
1. Legen Sie auf jeder Website einen anderen Preis für das Produkt fest.
1. Führen Sie cron und reindex aus.
1. Erstellen oder bearbeiten Sie eine CMS-Seite und verwenden Sie den Produktblock, um das Produkt hinzuzufügen.

<u>Tatsächliches Ergebnis</u>:<br>

Der folgende Fehler tritt auf:

*Filtervorlage für Fehler: Das Element (Magento\\Catalog\\Model\\Product\\Interceptor) mit der gleichen ID &quot;2&quot;ist bereits vorhanden.*

<u>Erwartetes Ergebnis</u>:<br>

Es werden keine Fehler angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
