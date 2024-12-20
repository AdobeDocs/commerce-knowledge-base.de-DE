---
title: 'ACSD-57941: Produktoptionen werden fälschlicherweise dem Admin Store zugewiesen'
description: Wenden Sie den Patch ACSD-57941 an, um das Adobe Commerce-Problem zu beheben, bei dem Produktoptionen fälschlicherweise dem Admin Store und nicht den entsprechenden Stores zugewiesen wurden.
feature: Products
role: Admin, Developer
exl-id: 7aa6f5c0-b718-4c3a-be0f-d86ae15e31a2
source-git-commit: 06f751e43ef825c0eb29cb9b42eb41f07c308625
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---

# ACSD-57941: Produktoptionen werden fälschlicherweise dem Admin Store zugewiesen

Der Patch ACSD-57941 behebt das Problem, dass die Produktoptionen fälschlicherweise dem Admin Store und nicht den entsprechenden Stores zugewiesen wurden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49 installiert ist. Die Patch-ID ist ACSD-57941. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Produktoptionen werden fälschlicherweise dem Admin Store und nicht den entsprechenden Stores zugewiesen.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein einfaches Produkt.
1. Importieren Sie dasselbe Produkt mit einigen benutzerdefinierten Optionen.
1. Gehen Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]** und öffnen Sie das erstellte Produkt. Klicken Sie auf &quot;**[!UICONTROL Customizable options]**&quot;und stellen Sie sicher, dass die importierten Optionen sichtbar sind.
1. Importieren Sie dieselbe Datei mehrmals.

<u>Erwartete Ergebnisse</u>:

Benutzerdefinierte Optionen werden aktualisiert.

<u>Tatsächliche Ergebnisse</u>:

Benutzerdefinierte Produktoptionen werden dupliziert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
