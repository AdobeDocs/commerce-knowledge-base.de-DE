---
title: 'ACSD-55566: [!UICONTROL mergeCart]-Mutation schlägt fehl, wobei ein interner Server-Fehler  [!DNL GraphQL]  wird'
description: Wenden Sie den Patch ACSD-55566 an, um das Adobe Commerce-Problem zu beheben, bei dem die Mutation „mergeCart“ mit einem internen Server-Fehler in der Antwort fehlschlägt [!DNL GraphQL]  wenn die Quell- und die Zielkarten zusammengeführt werden, die dieselben Bundle-Elemente aufweisen.
feature: GraphQL, Shopping Cart
role: Admin, Developer
exl-id: 84a9b861-351e-4fcc-bb91-3e31c7ae24e6
source-git-commit: 6b8eecb3df0bb32344a5861a604a40402bb4d392
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-55566: `mergeCart`-Mutation schlägt mit internem Server-Fehler in [!DNL GraphQL] Antwort fehl

Der Patch ACSD-55566 behebt das Problem, dass die `mergeCart`-Mutation mit einem internen Server-Fehler in [!DNL GraphQL] Antwort fehlschlägt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48 installiert ist. Die Patch-ID ist ACSD-55566. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.5.0 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

`mergeCart` Mutation schlägt mit einem internen Server-Fehler in [!DNL GraphQL] Antwort fehl, wenn die Quell- und Zielkarten zusammengeführt werden, die dieselben Bundle-Elemente enthalten.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine benutzerdefinierte Quelle und ein benutzerdefiniertes Lager.
1. Weisen Sie den erstellten Bestand der Haupt-Website zu.
1. Erstellen Sie ein einfaches Produkt und weisen Sie ihm die erstellte Quelle zu (qty=2).
1. Erstellen Sie ein Bundle-Produkt mit einer Option und einem untergeordneten Produkt (Produkt erstellt in Schritt 3).
1. Erstellen Sie einen Gästekorb über [!DNL GraphQL].
1. Fügen Sie ein Produktpaket hinzu, für das beide Optionen ausgewählt sind.
1. Speichern Sie die *cartID*.
1. Erstellen Sie einen Kunden und generieren Sie ein Kunden-Token.
1. Erstellen Sie einen Kundenwagen.
1. Fügen Sie dasselbe Produktpaket mit derselben Konfiguration zum Warenkorb hinzu.
1. Versuchen Sie, den Gästekorb mit dem Kundenwagen zusammenzuführen.

<u>Erwartete Ergebnisse</u>:

Der Warenkorb des Kunden enthält Produkte aus beiden Warenkörben.

<u>Tatsächliche Ergebnisse</u>:

Es wird ein interner Fehler angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
