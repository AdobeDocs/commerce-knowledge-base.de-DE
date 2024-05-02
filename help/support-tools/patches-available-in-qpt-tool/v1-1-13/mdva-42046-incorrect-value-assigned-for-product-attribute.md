---
title: "MDVA-42046: Falscher Wert für Produktattribut zugewiesen"
description: Der Patch MDVA-42046 behebt das Problem, dass für das Produktattribut ein falscher Wert zugewiesen wird, während ein Produkt mit einem Datumseingabefeld aktualisiert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-42046. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: 837f5582-849c-43a3-ae02-87f71fb96061
feature: Attributes, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%

---

# MDVA-42046: Falscher Wert für das Produktattribut zugewiesen

Der Patch MDVA-42046 behebt das Problem, dass für das Produktattribut ein falscher Wert zugewiesen wird, während ein Produkt mit einem Datumseingabefeld aktualisiert wird. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-42046. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4 - 2.3.5-p2 und 2.4.0 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Nach dem Speichern eines Produkts mit `news_from_date` und/oder `news_to_date` -Felder, werden die Werte aus diesen Feldern auf den Standardwert zurückgesetzt.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein einfaches Produkt.
1. Exportieren Sie das in Schritt 1 erstellte Produkt.
1. Fügen Sie in der exportierten CSV-Datei einige Werte in die `news_from_date` und `news_to_date` -Felder. Beispiel: 15.05.2021 und 2021-06-18.
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

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
