---
title: Leistungsproblem im Magento_Company-Modul-Upgrade nach der Aktualisierung auf B2B 1.5.2
description: Dieser Artikel enthält einen Hotfix für das Leistungsproblem im Magento_Company-Modul-Upgrade nach dem B2B-Update 1.5.2, in dem die übermäßig lange Verarbeitungszeit für große Datensätze in der Tabelle company_structure behandelt wird.
feature: B2B, Upgrade
role: Admin, Developer
source-git-commit: d06f0045b4c4c1615bd3abec963eb17fdee93860
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# Leistungsproblem im Magento_Company-Modul-Upgrade nach der Aktualisierung auf B2B 1.5.2

Dieser Artikel bietet einen Hotfix für das Leistungsproblem beim Upgrade des `Magento_Company`-Moduls nach der Aktualisierung von B2B 1.5.2, wobei die übermäßig lange Verarbeitungszeit für große Datensätze (~100.000+ Datensätze) in der `company_structure` behandelt wird.

## Betroffene Produkte und Versionen

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-px + B2B 1.5.2
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-px + B2B 1.5.2
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.8 + B2B 1.5.2

## Problem

Das Upgrade des `Magento_Company`-Moduls nach der Aktualisierung auf B2B 1.5.2 dauert bei der Verarbeitung einer großen Anzahl von Datensätzen (~100.000+) in der `company_structure`-Tabelle übermäßig lange.

<u>Voraussetzungen</u>:

* ACSD-65540_B2B_1.5.2.patch sollte installiert werden.
* Adobe Commerce 2.4.6 - 2.4.8
* B2B-Version 1.5.0, 1.5.1 oder B2B 1.5.2 mit aufgetragenem ACSD-65540-Patch

<u>Schritte zur Reproduktion</u>:

1. Weisen Sie einer übergeordneten Firma eine Firma zu, um die Unternehmenshierarchie festzulegen. Weitere Informationen finden [&#x200B; unter „Verwalten &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-admin/b2b/company-management/manage-company-hierarchy) Unternehmenshierarchie“ im Adobe Commerce B2B-Handbuch.
1. Aktualisieren Sie B2B auf Version 1.5.2.

<u>Erwartete Ergebnisse</u>:

Upgrade wurde erfolgreich abgeschlossen.

<u>Tatsächliche Ergebnisse</u>:

Die Aktualisierung des `Magento_Company`-Moduls dauert sehr lange, wenn die `company_structure` viele Datensätze enthält.

## Lösung

Um das Problem zu beheben, führen Sie die folgenden Schritte aus:

1. Aktualisieren Sie das B2B-Modul auf Version 1.5.2:

   ```
   composer require magento/module-b2b:1.5.2 --no-update
   composer update magento/module-b2b
   ```

1. Wenden Sie den [ACSD-65540_B2B_1.5.2.patch](/help/troubleshooting/installation-and-upgrade/assets/ACSD-65540_B2B_1.5.2.zip) an.

1. Wenden Sie den beigefügten [ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.patch](/help/troubleshooting/installation-and-upgrade/assets/ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.patch.zip) an.
1. Führen Sie `bin/magento setup:upgrade` nach dem Anwenden des Patches aus.

### Anbringen des Pflasters

Entpacken Sie die Datei und [&#x200B; Sie in unserer Support](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento)Wissensdatenbank die Anleitung „So wenden Sie einen von Adobe bereitgestellten Composer-Patch an“.

### Anwenden eines Patches mithilfe von Cloud-Patches

Gehen Sie für Adobe Commerce on Cloud-Händler wie folgt vor:

1. Aktualisieren Sie die Version des Moduls cloud-patches auf 1.1.5, um den als MCLOUD-13605 verteilten ACSD-65540_B2B_1.5.2.patch zu installieren.

   >[!NOTE]
   >
   >So überprüfen Sie, ob der Patch bereits installiert ist:
   > `./vendor/bin/magento-patches -n status | grep MCLOUD-13605`

   ```
   composer require magento/magento-cloud-patches:1.1.5 --no-update
   composer update magento/magento-cloud-patches
   ```

1. Fügen Sie den ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.patch zum Verzeichnis `m2-hotfixes` hinzu.
1. Übertragen Sie die Änderungen und übertragen Sie sie, um die erneute Bereitstellung und `bin/magento setup:upgrade` zu starten. Anweisungen finden [&#x200B; unter „Anwenden &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) Patches“ in unserem Handbuch zu Adobe Commerce on Cloud.

## Verwandtes Lesen

* [Die Aktualisierung auf B2B 1.5.2 schlägt aufgrund einer fehlenden REGEXP_LIKE-Funktion mit einem SQL-Syntaxfehler fehl](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/sql-syntax-error-due-to-missing-regexp-like-function)
