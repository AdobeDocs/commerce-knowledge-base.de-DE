---
title: Das Upgrade auf B2B 1.5.2 schlägt aufgrund einer fehlenden REGEXP_LIKE-Funktion mit einem SQL-Syntaxfehler fehl
description: Dieser Artikel enthält einen Hotfix für das Problem, dass ein SQL-Syntaxfehler aufgrund der fehlenden REGEXP_LIKE-Funktion auftritt, wenn versucht wird, die Tabelle company_structure zu aktualisieren.
feature: B2B, Upgrade
role: Admin, Developer
exl-id: c5fe316c-99e3-482e-80b5-25aaae371230
source-git-commit: 04e17dfdf143e233eb2767064c1328990c899eda
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# Das Upgrade auf B2B 1.5.2 schlägt aufgrund einer fehlenden REGEXP_LIKE-Funktion mit einem SQL-Syntaxfehler fehl

>[!INFO]
>
>Wenn beim Aktualisieren des `Magento_Company`-Moduls nach der Aktualisierung auf B2B 1.5.2 ein Leistungsproblem auftritt, wenden Sie den beigefügten [ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.patch](assets/ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.patch.zip) an.
>
>Weitere Informationen finden Sie unter [Leistungsproblem im Magento_Company-Modul-Upgrade nach dem B2B-Update 1.5.2](/help/troubleshooting/installation-and-upgrade/magento-company-module-upgrade-performance-issue.md) in der Adobe Commerce-Wissensdatenbank.

Dieser Artikel enthält einen Hotfix für den SQL-Syntaxfehler, der aufgrund der fehlenden `REGEXP_LIKE` beim Versuch auftritt, die `company_structure` zu aktualisieren.

## Betroffene Produkte und Versionen

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-px + B2B 1.5.2 mit [!DNL MariaDB] 10.6
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-px + B2B 1.5.2 mit [!DNL MariaDB] 10.6

## Problem

Die Aktualisierung auf B2B-Version 1.5.2 schlägt aufgrund der fehlenden `REGEXP_LIKE` beim Versuch, die `company_structure` zu aktualisieren, mit einem SQL-Syntaxfehler fehl.

<u>Voraussetzungen</u>:

* MariaDB 10.6
* Adobe Commerce 2.4.6x oder 2.4.7x
* B2B-Version 1.5.0 oder 1.5.1

<u>Schritte zur Reproduktion</u>:

1. Weisen Sie einer übergeordneten Firma eine Firma zu, um die Unternehmenshierarchie festzulegen. Weitere Informationen finden [ unter „Verwalten ](https://experienceleague.adobe.com/de/docs/commerce-admin/b2b/company-management/manage-company-hierarchy) Unternehmenshierarchie“ im Adobe Commerce B2B-Handbuch.
1. Aktualisieren Sie B2B auf Version 1.5.2.

<u>Erwartete Ergebnisse</u>:

Upgrade wurde erfolgreich abgeschlossen.

<u>Tatsächliche Ergebnisse</u>:

`bin/magento setup:upgrade` schlägt mit dem folgenden Fehler fehl:

```
Unable to apply data patch Magento\Company\Setup\Patch\Data\SetCompanyForStructure for module Magento_Company. Original exception message: SQLSTATE[42000]: Syntax error or access violation: 1305 FUNCTION REGEXP_LIKE does not exist, query was: UPDATE `company_structure` SET `company_id` = ? WHERE (REGEXP_LIKE(path, '^123(/.+)?$'))
```

## Lösung

Um das Problem zu beheben, führen Sie die folgenden Schritte aus:

1. Aktualisieren Sie das B2B-Modul auf Version 1.5.2:

   ```
   composer require magento/module-b2b:1.5.2 --no-update
   composer update magento/module-b2b
   ```

1. Wenden Sie den beigefügten [ACSD-65540_B2B_1.5.2.zip](assets/ACSD-65540_B2B_1.5.2.zip) an. Anweisungen finden Sie [So wenden Sie einen von Adobe bereitgestellten Composer](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)Patch in unserer Support-Wissensdatenbank an.
1. `bin/magento setup:upgrade` ausführen.

### Anwenden eines Patches mithilfe von Cloud-Patches

Gehen Sie für Adobe Commerce auf Cloud-Infrastruktur wie folgt vor:

1. Aktualisieren Sie die Version des `cloud-patches`-Moduls auf 1.1.5:

   ```
   composer require magento/magento-cloud-patches:1.1.5 --no-update
   composer update magento/magento-cloud-patches
   ```

1. Übergeben Sie die Änderungen und übertragen Sie sie, um eine erneute Bereitstellung zu starten. Anweisungen finden [ unter „Anwenden ](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) Patches“ in unserem Handbuch zu Adobe Commerce on Cloud.
