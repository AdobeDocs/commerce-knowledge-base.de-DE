---
title: 'MDVA-42046: Falscher Wert für das Produktattribut zugewiesen'
description: Der Patch MDVA-42046 behebt das Problem, dass für das Produktattribut ein falscher Wert zugewiesen wird, während ein Produkt mit einem Datumseingabefeld aktualisiert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-42046. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: 837f5582-849c-43a3-ae02-87f71fb96061
feature: Attributes, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%

---

# MDVA-42046: Falscher Wert für das Produktattribut zugewiesen

Der Patch MDVA-42046 behebt das Problem, dass für das Produktattribut ein falscher Wert zugewiesen wird, während ein Produkt mit einem Datumseingabefeld aktualisiert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-42046. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4 - 2.3.5-p2 und 2.4.0 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Nach dem Speichern eines Produkts mit den Feldern `news_from_date` und/oder `news_to_date` werden die Werte aus diesen Feldern auf den Standardwert zurückgesetzt.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein einfaches Produkt.
1. Exportieren Sie das in Schritt 1 erstellte Produkt.
1. Fügen Sie in der exportierten CSV-Datei einige Werte in die Felder `news_from_date` und `news_to_date` ein. Beispiel: 15.05.2021 und 2021-06-18.
1. Importieren Sie das Produkt mit der modifizierten CSV-Datei.
1. Fügen Sie dem Produktraster zusätzliche Spalten &quot;Produkt als neu vom Datum festlegen&quot;und &quot;Produkt als neu auf Datum festlegen&quot;hinzu.
1. Öffnen Sie die Bearbeitungsseite für das Produkt und klicken Sie ohne Änderungen auf **Speichern**.
1. Gehen Sie zurück zum Produktraster und überprüfen Sie die Daten für das Produkt.

<u>Erwartete Ergebnisse</u>:

Sowohl &quot;Produkt vom Datum als neu festlegen&quot;als auch &quot;Produkt als neu auf Datum festlegen&quot;sind dieselben wie vor dem Speichern.

<u>Tatsächliche Ergebnisse</u>:

* Die Werte in den Spalten &quot;Produkt als neu vom Datum festlegen&quot;und &quot;Produkt als neu auf Datum festlegen&quot;werden geändert.

* Die Spalte &quot;Produkt als neu vom Datum festlegen&quot;zeigt das aktuelle Datum und die Spalte &quot;Produkt als neu auf Datum festlegen&quot;ist leer.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) verfügbar sind, in unserer Entwicklerdokumentation.
