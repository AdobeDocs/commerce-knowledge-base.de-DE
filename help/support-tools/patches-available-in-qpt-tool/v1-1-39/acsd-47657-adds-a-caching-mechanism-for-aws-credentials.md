---
title: "ACSD-47657: Fügt einen Caching-Mechanismus für AWS-Anmeldeinformationen hinzu."
description: Wenden Sie den Patch ACSD-47657 an, um das Adobe Commerce-Problem zu beheben, das bei einer hohen Anzahl von Anfragen an AWS S3 auftritt, indem Sie einen Caching-Mechanismus für AWS-Anmeldeinformationen hinzufügen.
feature: Cache
role: Admin, Developer
exl-id: d5822082-c656-45bf-b192-9cc8007b82a2
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# ACSD-47657: Fügt einen Caching-Mechanismus für AWS-Anmeldeinformationen hinzu

Der Patch ACSD-47657 behebt das Problem, das bei einer hohen Anzahl von Anfragen an AWS S3 auftritt, indem ein Caching-Mechanismus für AWS-Anmeldeinformationen hinzugefügt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.39 installiert ist. Die Patch-ID ist ACSD-47657. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Hinzufügen eines Caching-Mechanismus für AWS-Anmeldeinformationen, die von AWS für die EC2-Konfiguration abgerufen werden.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie den AWS S3-Behälterspeicher für Adobe Commerce:

   ```
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="magentopubmedia-prod" --remote-storage-region="aws-west" --no-interaction
   bin/magento config:set 
   system/media_storage_configuration/media_database 0 
   bin/magento cache:flush
   ```

1. Synchronisierung ausführen:

   ```
   bin/magento remote-storage:sync
   ```

<u>Erwartete Ergebnisse</u>:

Die Synchronisierung wurde erfolgreich abgeschlossen.

<u>Tatsächliche Ergebnisse</u>:

In etwa einer Stunde tritt der folgende Fehler auf:

```
    report.CRITICAL: Aws\Exception\CredentialsException: Error retrieving credentials from the instance profile metadata service. (cURL error 28: Connection timed out after 1001 milliseconds) (see https://curl.haxx.se/libcurl/c/libcurl-errors.html) 
```

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
