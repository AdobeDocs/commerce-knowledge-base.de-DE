---
title: 'MDVA-37592: Sortierung nach Preis, die nicht für Produkte mit Preis Null funktioniert'
description: Der MDVA-37592 Adobe Commerce-Patch behebt das Problem, dass eine Sortierung nach Preis für Produkte mit einem gemeinsamen Katalog ohne Preis nicht ordnungsgemäß funktioniert. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.0 installiert ist. Die Patch-ID lautet MDVA-37592. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
exl-id: 30ac1e87-c32d-4e79-9ed9-d1861061d760
feature: B2B, Catalog Management, Categories, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# MDVA-37592: Sortierung nach Preis, die nicht für Produkte mit Preis Null funktioniert

Der MDVA-37592 Adobe Commerce-Patch behebt das Problem, dass eine Sortierung nach Preis für Produkte mit einem gemeinsamen Katalog ohne Preis nicht ordnungsgemäß funktioniert. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.0 installiert ist. Die Patch-ID lautet MDVA-37592. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce in unserer Cloud-Architektur 2.4.0-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungstypen) 2.3.6-2.4.2-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Sortierung nach Preis funktioniert nicht ordnungsgemäß für Produkte, deren Preis Null einem freigegebenen Katalog zugeordnet ist.

<u>Voraussetzungen</u>:

B2B wird installiert.

<u>Zu reproduzierende Schritte</u>:

1. Freigegebenen Katalog aktivieren.
1. Erstellen Sie vier Produkte mit den folgenden Preisen und weisen Sie sie einer Kategorie zu: 50, 60, 70 und 80 USD.
1. Erstellen Sie einen freigegebenen Katalog mit den oben genannten Produkten.
1. Legen Sie den benutzerspezifischen Preis für das Produkt mit einem Preis von 70 USD auf null fest.
1. Erstellen Sie nun einen Unternehmensbenutzer und weisen Sie ihn dem soeben erstellten freigegebenen Katalog zu.
1. Melden Sie sich mit dem Unternehmenskonto an und navigieren Sie zu der Kategorie, der die Produkte zugewiesen sind.
1. Sortieren Sie nach Preis.

<u>Erwartete Ergebnisse</u>:

Das Produkt mit dem Preis Null wird korrekt sortiert.

<u>Tatsächliche Ergebnisse</u>:

Das Produkt mit dem Preis Null wird NICHT korrekt sortiert. Stattdessen wird er nach dem ursprünglichen Preis sortiert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungstyp die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce On-Premise: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce in unserer Cloud-Architektur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitätspatches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Überprüfen Sie mithilfe des Qualitätssicherungswerkzeugs](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md), ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie im Abschnitt [Im QPT-Tool verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
