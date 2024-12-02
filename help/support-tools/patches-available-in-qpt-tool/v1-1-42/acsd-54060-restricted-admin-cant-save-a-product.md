---
title: 'ACSD-54060: Eingeschränkte Administratoren können ein Produkt nicht speichern, wenn es einem anderen Produkt untergeordnet ist'
description: Wenden Sie den Patch ACSD-54060 an, um das Adobe Commerce-Problem zu beheben, bei dem ein eingeschränkter Administrator ein Produkt nicht speichern kann, wenn es ein untergeordnetes Element eines anderen Produkts ist, das einem anderen Bereich zugewiesen ist.
feature: Admin Workspace, Roles/Permissions, Products
role: Admin, Developer
exl-id: 28fa3c99-f2b6-4c6d-955a-bd6638a1b077
source-git-commit: 8b6bf1cdada7edb0cdb0bb3e90ed15ee8cebf77e
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-54060: Eingeschränkte Administratoren können ein Produkt nicht speichern, wenn es einem anderen Produkt untergeordnet ist

Der Patch ACSD-54060 behebt das Problem, dass ein eingeschränkter Administrator ein Produkt nicht speichern kann, wenn es ein untergeordnetes Element eines anderen Produkts ist, das einem anderen Bereich zugewiesen ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 installiert ist. Die Patch-ID ist ACSD-54060. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Ein eingeschränkter Administrator kann ein Produkt nicht speichern, wenn es ein untergeordnetes Element eines anderen Produkts ist, das einem anderen Bereich zugewiesen ist.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine zusätzliche Website.
1. Erstellen Sie ein einfaches Produkt und weisen Sie es beiden Websites zu.
1. Erstellen Sie ein konfigurierbares Produkt mit dem einfachen Produkt als einzige Variante und weisen Sie das konfigurierbare Produkt nur der Standardwebsite zu.
1. Erstellen Sie einen Benutzer mit eingeschränktem Administratorstatus, der nur Zugriff auf die zweite Website hat.
1. Melden Sie sich als eingeschränkter Administrator an.
1. Versuchen Sie, den einfachen Produktnamen im zweiten Website-Bereich zu ändern.

<u>Erwartete Ergebnisse</u>:

Der eingeschränkte Administrator kann den Produktnamen ändern.

<u>Tatsächliche Ergebnisse</u>:

Es tritt ein Fehler auf: *Mehr Berechtigungen sind erforderlich, um dieses Element anzuzeigen*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
