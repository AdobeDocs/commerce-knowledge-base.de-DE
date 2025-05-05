---
title: 'ACSD-56741: Fehlerbehebung bei Datenbanksetup-Fehlern mit benutzerdefinierten MySQL-Triggern'
description: Wenden Sie den Patch ACSD-56741 an, um das Adobe Commerce-Problem zu beheben, bei dem während „setup:upgrade“ eine Fehlermeldung „Zugriff auf Array-Offset mit dem Wert null“ angezeigt wird, da ein benutzerdefinierter MySQL-Trigger in der Datenbank nicht mit der Indizierung und  [!DNL MView] in Zusammenhang steht.
feature: Install
role: Admin, Developer
exl-id: 97839140-03c5-44f0-ba75-935d62f5bf90
source-git-commit: 7cd830d9ba4af6350a14e0cdb50439d2d07084dc
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-56741: Fehlerbehebung bei Datenbanksetup-Fehlern mit benutzerdefinierten MySQL-Triggern

Der Patch ACSD-56741 behebt das Problem, dass *Fehlermeldung „Zugriff auf Array-Offset bei Wert vom Typ null“* der `setup:upgrade` angezeigt wird, da ein benutzerdefinierter MySQL-Trigger in der Datenbank nicht mit der Indizierung und [!DNL MView] in Zusammenhang steht. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48 installiert ist. Die Patch-ID ist ACSD-56741. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.5.0 behoben wird

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Bei der `setup:upgrade` wird *Fehlermeldung „Zugriff auf den Array-Offset bei einem Wert vom Typ null* angezeigt, da ein benutzerdefinierter MySQL-Trigger in der Datenbank nicht mit der Indizierung und der [!DNL MView] in Zusammenhang steht.

<u>Schritte zur Reproduktion</u>:

1. `php bin/magento indexer:set-mode schedule` ausführen.

   ```
   DELIMITER //
   CREATE TRIGGER trg_catalog_category_entity_before_delete_umis BEFORE DELETE ON catalog_category_entity FOR EACH ROW
       -> BEGIN
       -> UPDATE ewave_navigation_menu_item_info as nit INNER JOIN ewave_navigation_menu_category_type as ncmi ON nit.id = ncmi.menu_item_id AND ncmi.category_id = OLD.entity_id SET nit.status = 0;
       -> END //
   ```

1. `php bin/magento c:f` ausführen.
1. `php bin/magento setup:upgrade` ausführen.

<u>Erwartete Ergebnisse</u>:

Das Setup-Upgrade wird fehlerfrei abgeschlossen.

<u>Tatsächliche Ergebnisse</u>:

Das Setup-Upgrade wird mit einer Fehlermeldung beendet:

*Warnung: Versuch, auf den Array-Offset für einen Wert vom Typ null zuzugreifen*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
