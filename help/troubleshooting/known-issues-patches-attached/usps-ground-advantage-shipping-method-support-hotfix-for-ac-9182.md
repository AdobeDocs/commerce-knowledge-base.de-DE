---
title: '[!DNL USPS] Ground Advantage Versandmethode Support Hotfix für AC-9182'
promoted: true
description: Wenden Sie einen Patch an, um das Problem AC-9182 mit der Versandmethode „Ground [!DNL USPS] Advantage“ für Adobe Commerce 2.4.4 - 2.4.6-p2 zu beheben.
feature: Shipping/Delivery
role: Developer
exl-id: b6871d19-3d02-4026-82e6-3545f4ab7159
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# [!DNL USPS] Ground Advantage Versandmethode Support Hotfix für AC-9182

Dieser Artikel enthält einen Patch zum Beheben des Problems AC-9182 für die neue Versandmethode **[!DNL USPS]Ground Advantage** in Adobe Commerce 2.4.4 - 2.4.6-p2.

Am 9. Juli 2023 veröffentlichte der United States Postal Service ([!DNL USPS]) eine neue Versandmethode, [[!DNL USPS] Ground Advantage](https://www.usps.com/ship/ground-advantage.htm).

Diese neue Versandmethode ersetzt die drei wichtigsten aktuellen Versandmethoden:

* [!DNL USPS]
* [!DNL USPS] erstklassiger Paketdienst
* [!DNL USPS]

[[!DNL USPS] angekündigt](https://faq.usps.com/s/article/USPS-Ground-Advantage#how_it_works) dass diese drei Versandmethoden ab dem 30. September 2023 eingestellt werden und alle Kunden stattdessen die neue **[!DNL USPS]Ground Advantage**-Methode verwenden müssen.

Nach dem 30. September 2023 können also alle Adobe Commerce-Händler, die die USPS-Versandmethode verwenden, keine Versandraten mehr von [!DNL USPS] erhalten, indem sie diese drei alten Versandmethoden verwenden.

Dieses Problem wird im Oktober 2023 im Rahmen der kommenden reinen Sicherheits-Patch-Versionen in den Versionen 2.4.6-p3, 2.4.5-p5 und 2.4.4-p6 behoben.

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur und On-Premise und Magento Open Source:

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

Der [!DNL USPS] hat ein [!DNL API] Update durchgeführt.

## Lösung

Um das Problem in den Versionen 2.4.4, 2.4.5 und 2.4.6 zu beheben, müssen Sie den unten stehenden AC-9182-Patch anwenden.

## Fleck

Der Patch ist diesem Artikel beigefügt. Um ihn herunterzuladen, klicken Sie auf den folgenden Link:

[AC-9182_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.zip](assets/AC-9182_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.zip)

## Anbringen des Pflasters

Entpacken Sie die Datei und [ Sie in unserer Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html)Wissensdatenbank die Anleitung „So wenden Sie einen Composer-Patch von Adobe an“.

## Wie man feststellt, ob die Patches angewendet wurden

Da es nicht einfach möglich ist, zu überprüfen, ob das Problem behoben wurde, sollten Sie überprüfen, ob der AC-9182-Patch erfolgreich angewendet wurde.

<u>Sie können dies tun, indem Sie die folgenden Schritte ausführen</u>:

1. [Installieren Sie  [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Führen Sie den Befehl aus:

   ```bash
   vendor/bin/magento-patches -n status |grep "9182|Status"
   ```

1. Es sollte eine ähnliche Ausgabe angezeigt werden, bei der AC-9182 den Status *Angewendet* zurückgibt:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/AC-9182_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```
