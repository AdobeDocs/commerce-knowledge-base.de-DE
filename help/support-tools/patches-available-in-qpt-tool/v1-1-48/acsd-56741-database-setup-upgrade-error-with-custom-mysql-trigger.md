---
title: '"ACSD-56741: Fehlerbehebung bei Datenbanksetup-Fehlern mit benutzerdefinierten MySQL-Triggern'
description: Wenden Sie den Patch ACSD-56741 an, um das Adobe Commerce-Problem zu beheben, bei dem während des "setup:upgrade"eine Fehlermeldung angezeigt wird *Versuchen, auf den Array-Offset vom Typ null zuzugreifen* aufgrund eines benutzerspezifischen MySQL-Triggers in der Datenbank, der nicht mit der Indizierung in Zusammenhang steht, und [!DNL MView].
feature: Install
role: Admin, Developer
source-git-commit: 216ce1035584e4c049029073ee0017d3616cdbd6
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-56741: Fehlerbehebung bei Datenbanksetup-Fehlern mit benutzerdefinierten MySQL-Triggern

Der Patch ACSD-56741 behebt das Problem, dass eine Fehlermeldung angezeigt wird. *Versuch, auf den Array-Versatz für den Wert des Typs null zuzugreifen* erscheint während `setup:upgrade` aufgrund eines benutzerdefinierten MySQL-Triggers in der Datenbank, der nicht mit der Indexierung in Zusammenhang steht, und [!DNL MView]. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48 ist installiert. Die Patch-ID ist ACSD-56741. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.5.0 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6 - p4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Eine Fehlermeldung *Versuch, auf den Array-Versatz für den Wert des Typs null zuzugreifen* erscheint während `setup:upgrade` aufgrund eines benutzerdefinierten MySQL-Triggers in der Datenbank, der nicht mit der Indexierung in Zusammenhang steht, und [!DNL MView].

<u>Zu reproduzierende Schritte</u>:

1. Ausführen `php bin/magento indexer:set-mode schedule`.

   ```
   DELIMITER //
   CREATE TRIGGER trg_catalog_category_entity_before_delete_umis BEFORE DELETE ON catalog_category_entity FOR EACH ROW
       -> BEGIN
       -> UPDATE ewave_navigation_menu_item_info as nit INNER JOIN ewave_navigation_menu_category_type as ncmi ON nit.id = ncmi.menu_item_id AND ncmi.category_id = OLD.entity_id SET nit.status = 0;
       -> END //
   ```

1. Ausführen `php bin/magento c:f`.
1. Ausführen `php bin/magento setup:upgrade`.

<u>Erwartete Ergebnisse</u>:

Das Setup-Upgrade wird ohne Fehler beendet.

<u>Tatsächliche Ergebnisse</u>:

Das Setup-Upgrade wird mit einer Fehlermeldung beendet:

*Warnung: Versuch, auf den Array-Offset für Wert des Typs null zuzugreifen*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
