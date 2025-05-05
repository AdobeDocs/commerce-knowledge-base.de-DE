---
title: 'ACSD-54060: Ein eingeschränkter Administrator kann ein Produkt nicht speichern, wenn es ein untergeordnetes Produkt eines anderen Produkts ist'
description: Wenden Sie den Patch ACSD-54060 an, um das Adobe Commerce-Problem zu beheben, bei dem ein eingeschränkter Administrator ein Produkt nicht speichern kann, wenn es sich um ein untergeordnetes Produkt eines anderen Produkts handelt, das einem anderen Umfang zugewiesen wurde.
feature: Admin Workspace, Roles/Permissions, Products
role: Admin, Developer
exl-id: 28fa3c99-f2b6-4c6d-955a-bd6638a1b077
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-54060: Ein eingeschränkter Administrator kann ein Produkt nicht speichern, wenn es ein untergeordnetes Produkt eines anderen Produkts ist

Mit dem Patch ACSD-54060 wird das Problem behoben, dass ein Admin mit Zugriffsbeschränkung ein Produkt nicht speichern kann, wenn es sich um ein untergeordnetes Produkt eines anderen Produkts handelt, das einem anderen Umfang zugewiesen wurde. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 installiert ist. Die Patch-ID ist ACSD-54060. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Ein eingeschränkter Administrator kann ein Produkt nicht speichern, wenn es ein untergeordnetes Element eines anderen Produkts ist, das einem anderen Bereich zugewiesen wurde.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine zusätzliche Website.
1. Erstellen Sie ein einfaches Produkt und weisen Sie es beiden Websites zu.
1. Erstellen Sie ein konfigurierbares Produkt mit dem einfachen Produkt als einzige Variante und weisen Sie das konfigurierbare Produkt nur der Standard-Website zu.
1. Erstellen Sie einen Benutzer mit eingeschränktem Administratorzugriff, der nur Zugriff auf die zweite Website hat.
1. Melden Sie sich als eingeschränkter Admin-Benutzer an.
1. Versuchen Sie, den einfachen Produktnamen im zweiten Website-Bereich zu ändern.

<u>Erwartete Ergebnisse</u>:

Der Administrator mit Zugriffsbeschränkung kann den Produktnamen ändern.

<u>Tatsächliche Ergebnisse</u>:

Ein Fehler tritt auf: *Weitere Berechtigungen sind erforderlich, um dieses Element anzuzeigen*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
