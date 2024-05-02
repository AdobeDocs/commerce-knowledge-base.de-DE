---
title: "ACSD-50478: JS-Problem für Rollback-Aktionen im Sicherungs-Raster und Datenbank-Rollback-Befehl"
description: Wenden Sie den Patch ACSD-50478 an, um das JS-Problem für die Rollback-Aktion im Sicherungsraster und den Datenbank-Rollback-Befehl zu beheben, wenn der DB-Dump Trigger und einen SQL-Befehl *delimiter* enthält.
exl-id: 8b516705-29be-462e-b3ec-3a339b6e8006
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-50478: JS-Problem für Rollback-Aktionen im Sicherungsraster und Datenbank-Rollback-Befehl

Der Patch ACSD-50478 behebt das JS-Problem für die Rollback-Aktion im Sicherungsraster und den Datenbank-Rollback-Befehl für einen Fall, in dem der DB-Dump Trigger und einen *delimiter* SQL-Befehl. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 installiert ist. Die Patch-ID ist ACSD-50478. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.4 - p4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

JS-Problem für die Rollback-Aktion im Sicherungsraster und im Datenbank-Rollback-Befehl für einen Fall, wenn der DB-Dump Trigger und eine *delimiter* SQL-Befehl.

<u>Zu reproduzierende Schritte</u>:

1. Indexer auf [!UICONTROL Update on Schedule] -Modus, damit Trigger in der Datenbank erstellt werden.
1. Aktivieren Sie die Sicherungsfunktion über die Befehlszeile:

   `bin/magento config:set system/backup/functionality_enabled 1`

1. Navigieren Sie zu **System** > **Instrumente** > **Backups** und eine DB-Sicherung erstellen.
1. Öffnen Sie die Browser-Konsole. Der folgende Fehler wird angezeigt:

   ```
   Uncaught SyntaxError: Unexpected token '&' (at (index):606:32)
   
   function eventListener8jtGaqtgG2 () {
   
           return backup.rollback(&#039;db&#039;, &#039;1678391644&#039;);
   ```

1. Versuchen Sie, die DB über die Befehlszeile zu importieren:

   `bin/magento setup:rollback --db-file="<filename>"`

1. Der folgende Fehler wird angezeigt:

   ```
   Syntax error or access violation: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'delimiter' at line 1, query was: delimiter ;;
   ```

<u>Erwartete Ergebnisse</u>:

Die Datenbankwiederherstellung kann sowohl vom Administrator als auch von der Befehlszeile erfolgreich durchgeführt werden.

<u>Tatsächliche Ergebnisse</u>:

Sie haben die in Schritt 4 und Schritt 6 genannten Fehler beobachtet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
