---
title: "MDVA-38132: Unendliche Umleitung, wenn sich die Backend-URL von der Standard-Website-URL unterscheidet"
description: Der Patch MDVA-38132 behebt das Problem der unendlichen Umleitung, wenn sich die Backend-URL von der standardmäßigen Website-URL unterscheidet. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25 installiert ist. Die Patch-ID lautet MDVA-38132. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben sein soll.
exl-id: 122145d7-0961-47f8-8ab6-a15d62996e49
feature: Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# MDVA-38132: Unendliche Umleitung, wenn sich die Backend-URL von der Standard-Website-URL unterscheidet

Der Patch MDVA-38132 behebt das Problem der unendlichen Umleitung, wenn sich die Backend-URL von der standardmäßigen Website-URL unterscheidet. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25 ist installiert. Die Patch-ID lautet MDVA-38132. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
Adobe Commerce auf Cloud-Infrastruktur 2.3.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**
Adobe Commerce (alle Bereitstellungsmethoden) 2.3.3-2.4.2-p1
>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das Commerce Admin-Bedienfeld verfügt über eine unendliche Umleitung, wenn sich die Backend-URL von der standardmäßigen Website-URL unterscheidet.

<u>Voraussetzungen</u>:

* Die Basis-URL wird sowohl für das Backend als auch für die Storefront verwendet. Sichere Basis-URL wird nicht verwendet.
* Der Webserver ist so konfiguriert, dass der Zugriff auf Adobe Commerce über zwei verschiedene URLs erfolgt. URL1 wird für die Installation von Adobe Commerce verwendet.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zum Admin Panel > **Stores** > **Konfiguration** > **Web**.
1. Lassen Sie die ursprüngliche Basis-URL in der globalen Konfiguration. Es ist Ihre URL1.
1. Wechseln Sie zum Bereich Haupt-Website .
1. Ändern Sie die Basis-URL in eine andere URL (siehe Voraussetzungen für die korrekte Einrichtung des Webservers). Dies ist Ihre URL2.
1. Löschen Sie den Cache (falls erforderlich und möglich).
1. Öffnen Sie das Admin-Bedienfeld.

<u>Erwartete Ergebnisse</u>:

Das Admin Panel wurde erfolgreich geöffnet und kann navigiert werden. Der Speicher der Hauptwebsite wurde erfolgreich geöffnet und kann navigiert werden.

<u>Tatsächliche Ergebnisse</u>:

Eine unendliche Umleitung erfolgt. Adobe Commerce leitet von URL1 zu URL2 um und fährt zurück und her.

## Wenden Sie den Patch an

Um einzelne Patches anzuwenden, verwenden Sie je nach Adobe Commerce-Produkt die folgenden Links:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie im Abschnitt [Im QPT-Tool verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) Abschnitt.
