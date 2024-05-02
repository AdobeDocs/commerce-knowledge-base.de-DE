---
title: '[!DNL USPS] Support-Hotfix für die Bodenvorteile-Versandmethode für AC-9182'
promoted: true
description: Wenden Sie einen Patch an, um die [!DNL USPS] Problem mit der Bodenvorschau-Versandmethode AC-9182 für Adobe Commerce 2.4.4 - 2.4.6-p2.
feature: Shipping/Delivery
role: Developer
exl-id: b6871d19-3d02-4026-82e6-3545f4ab7159
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# [!DNL USPS] Support-Hotfix für die Ground Advantage-Versandmethode für AC-9182

Dieser Artikel enthält einen Patch zur Lösung des Problems AC-9182 für die neue **[!DNL USPS]Bodenvorteil** Versandmethode in Adobe Commerce 2.4.4 - 2.4.6-p2.

Am 9. Juli 2023 hat der US-Postdienst ([!DNL USPS]) eine neue Versandmethode veröffentlicht, [[!DNL USPS] Bodenvorteil](https://www.usps.com/ship/ground-advantage.htm).

Diese neue Versandmethode ersetzt die drei aktuellen Versandmethoden:

* [!DNL USPS] Einzelhandelsgrundstück
* [!DNL USPS] erstklassiger Paketdienst
* [!DNL USPS] Parzellen-Auswahl-Boden

[[!DNL USPS] verkündet](https://faq.usps.com/s/article/USPS-Ground-Advantage#how_it_works) ab dem 30. September 2023 werden diese drei Versandmethoden eingestellt und alle Kunden müssen die neue **[!DNL USPS]Bodenvorteil** -Methode.

Ab dem 30. September 2023 können alle Adobe Commerce-Händler, die die USPS-Versandmethode verwenden, keine Versandtarife von erhalten [!DNL USPS] , indem Sie diese drei alten Versandmethoden noch verwenden.

Dieses Problem wird im Rahmen bevorstehender Sicherheits-Patch-Versionen im Oktober 2023 in den Versionen 2.4.6-p3, 2.4.5-p5 und 2.4.4-p6 behoben.

## Betroffene Produkte und Versionen

Adobe Commerce über Cloud-Infrastruktur und On-Premise und Magento Open Source:

* 2,4,4
* 2.4.4-p1
* 2.4.4-p2
* 2.4.4-p3
* 2.4.4-p4
* 2.4.4-p5
* 2,4,5
* 2.4.5-p1
* 2.4.5-p2
* 2.4.5-p3
* 2.4.5-p4
* 2,4,6
* 2.4.6-p1
* 2.4.6-p2

## Ursache

Die [!DNL USPS] erstellt [!DNL API] aktualisieren.

## Lösung

Um das Problem in den Versionen 2.4.4, 2.4.5 und 2.4.6 zu beheben, müssen Sie den unten stehenden Patch AC-9182 anwenden.

## Patch

Der Patch ist an diesen Artikel angehängt. Um es herunterzuladen, klicken Sie auf den folgenden Link:

[AC-9182_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.zip](assets/AC-9182_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.zip)

## Anwenden des Pflasters

Entpacken Sie die Datei und lesen Sie [Anwenden eines von Adobe bereitgestellten Composer-Patches](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) in unserer Support-Wissensdatenbank für Anleitungen.

## Ermitteln, ob die Patches angewendet wurden

Da es nicht einfach zu überprüfen ist, ob das Problem gepatcht wurde, sollten Sie überprüfen, ob der Patch AC-9182 erfolgreich angewendet wurde.

<u>Gehen Sie dazu wie folgt vor:</u>:

1. [Installieren Sie die [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Führen Sie den Befehl aus:

   ```bash
   vendor/bin/magento-patches -n status |grep "9182|Status"
   ```

1. Sie sollten die Ausgabe ähnlich wie hier sehen, wobei AC-9182 die *Angewandt* status:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/AC-9182_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```
