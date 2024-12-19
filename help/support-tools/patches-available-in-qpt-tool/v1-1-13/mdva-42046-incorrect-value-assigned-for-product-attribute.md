---
title: 'MDVA-42046: Falscher Wert für Produktattribut zugewiesen'
description: Der Patch MDVA-42046 behebt das Problem, dass beim Aktualisieren eines Produkts mit einem Datumseingabefeld für das Produktattribut ein falscher Wert zugewiesen wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-42046. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
exl-id: 837f5582-849c-43a3-ae02-87f71fb96061
feature: Attributes, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%

---

# MDVA-42046: Falscher Wert für Produktattribut zugewiesen

Der Patch MDVA-42046 behebt das Problem, dass beim Aktualisieren eines Produkts mit einem Datumseingabefeld für das Produktattribut ein falscher Wert zugewiesen wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-42046. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4 - 2.3.5-p2 und 2.4.0 - 2.4.4

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Nach dem Speichern eines Produkts mit `news_from_date`- und/oder `news_to_date` Feldern werden die Werte in diesen Feldern auf den Standardwert zurückgesetzt.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein einfaches Produkt.
1. Exportieren Sie das in Schritt 1 erstellte Produkt.
1. Fügen Sie in die exportierte CSV-Datei einige Werte in die Felder `news_from_date` und `news_to_date` ein. Beispiel: 15. Februar 2021 und 18. Juni 2021.
1. Importieren Sie das Produkt mit der geänderten CSV-Datei.
1. Fügen Sie zusätzliche Spalten „Produkt als neues Startdatum festlegen“ und „Produkt als neues Startdatum festlegen“ zum Produktraster hinzu.
1. Öffnen Sie die Bearbeitungsseite für das Produkt und klicken Sie ohne Änderungen auf **Speichern**.
1. Kehren Sie zum Produktraster zurück und überprüfen Sie die Daten für das Produkt.

<u>Erwartete Ergebnisse</u>:

„Produkt als neues Startdatum festlegen“ und „Produkt als neues Datum festlegen“ sind dieselben wie vor dem Speichern.

<u>Tatsächliche Ergebnisse</u>:

* Die Werte in den Spalten „Produkt als neues Startdatum festlegen“ und „Produkt als neues Datum festlegen“ werden geändert.

* Die Spalte „Produkt als neues Startdatum festlegen“ zeigt das aktuelle Datum an, und die Spalte „Produkt als neues Startdatum festlegen“ ist leer.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in unserer Entwicklerdokumentation.
