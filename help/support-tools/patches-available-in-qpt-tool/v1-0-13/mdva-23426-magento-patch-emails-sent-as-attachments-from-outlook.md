---
title: 'MDVA-23426 Magento Patch: E-Mails, die als Anhänge von Outlook gesendet werden'
description: Der Magento-Patch MDVA-23426 behebt das Problem, dass E-Mails als Anhänge von MS Outlook als Magento gesendet werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13 installiert ist. Bitte beachten Sie, dass das Problem in Magento 2.3.5 behoben wurde.
exl-id: 0b4c3e33-76c5-48b0-b1a8-a967cea11b98
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# MDVA-23426 Magento Patch: E-Mails, die als Anhänge von Outlook gesendet werden

Der Magento-Patch MDVA-23426 behebt das Problem, dass E-Mails als Anhänge von MS Outlook als Magento gesendet werden. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13 installiert ist. Bitte beachten Sie, dass das Problem in Magento 2.3.5 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Magento-Version erstellt:** Magento Commerce Cloud 2.3.3.

**Kompatibel mit Magento-Versionen:** Magento Commerce und Magento Commerce Cloud 2.3.3 - 2.3.4-p2.

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

E-Mails werden mit einem leeren Textkörper empfangen und der Inhalt wird als Anhang eingefügt.

<u>Voraussetzungen:</u> Outlook/Exchange wird als Client/Server-Kombination verwendet.

<u>Zu reproduzierende Schritte:</u> 1. Senden Sie eine Bestellung, die Bestellbenachrichtigung oder die Versandbenachrichtigung.2. Die E-Mail wird empfangen.

<u>Ergebnis:</u> Die E-Mail wird mit einem leeren Text und dem Inhalt als ATT\*-gekennzeichneter Anhang an die E-Mail angezeigt. <u>Erwartetes Ergebnis:</u>

Die E-Mail wird ohne Anhang empfangen und der Hauptteil der E-Mail enthält den Inhalt.

## Wenden Sie den Patch an

Anweisungen zum Anwenden eines QPT-Patches finden Sie unter den folgenden Links je nach Magento-Produkt:

* Magento Commerce: DevDocs [Anwenden von Patches mithilfe des Tools &quot;Qualitätsmuster&quot;](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) .
* Magento Commerce Cloud: DevDocs [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) .

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) .
* [Überprüfen Sie den Patch auf ein Magento-Problem mit dem Quality Patches Tool.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) .

Weitere Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie im Abschnitt [Im QPT-Tool verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) Abschnitt.
