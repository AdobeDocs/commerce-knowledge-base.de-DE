---
title: "ACSD-49013: E-Mail-Bestätigung nicht in Website-Gebietsschema übersetzt"
description: Wenden Sie den Patch ACSD-49013 an, um das Adobe Commerce-Problem zu beheben, bei dem die E-Mail-Bestätigung beim Erstellen von Kunden mit Bulk API nicht in das Gebietsschema der Website übersetzt wird.
exl-id: 68203bd4-021a-4736-a793-4b6663a9c66b
feature: Admin Workspace, Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# ACSD-49013: E-Mail-Bestätigung nicht in das Gebietsschema der Website übersetzt

Der Patch ACSD-49013 behebt das Problem, dass die E-Mail-Bestätigung beim Erstellen von Kunden mit Bulk API nicht in das Gebietsschema der Website übersetzt wird. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 ist installiert. Die Patch-ID lautet ACSD-49013. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die E-Mail-Bestätigung wird beim Erstellen von Kunden mithilfe der Bulk API nicht in das Gebietsschema der Website übersetzt.

<u>Zu reproduzierende Schritte</u>:

1. Installieren Sie ein anderes Gebietsschema wie `de_DE`.
1. Konfigurieren *RabbitMQ*.
1. Ausführen `bin/magento setup:upgrade` , um die Warteschlangen in RabbitMQ zu installieren und das Sprachpaket einzurichten.
1. Erstellen Sie eine zusätzliche Website in [!UICONTROL Admin] > **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**.
1. Setzen Sie das Gebietsschema dieser neuen Website auf `de_DE` in [!UICONTROL Admin] > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Locale Options]**.
1. Führen Sie einen API-Aufruf aus, um ein Kundenkonto mit der Bulk API zu erstellen. Verwenden Sie die entsprechende `website_id`.

   `Endpoint: /rest/async/bulk/V1/customers`

   ```
   [{
       "customer": {
       "email": "test@example.com",
       "firstname": "test",
       "lastname": "test",
       "website_id": 2
       },
       "password": "Passw0rd!"
   }]
   ```

1. Ausführen `bin/magento queue:consumers:start async.operations.all --single-thread --max-messages=10`.
1. Sie können sehen, dass das Kundenkonto auf der angegebenen Website korrekt erstellt wurde.
1. Überprüfen Sie die E-Mail, die zur Kundenregistrierung empfangen wurde.

<u>Erwartete Ergebnisse</u>:

Da der Kunde auf einer bestimmten Website erstellt wird, wird die Registrierungs-E-Mail mit dem Gebietsschema dieser Website gesendet.

<u>Tatsächliche Ergebnisse</u>:

Der Kunde wird ordnungsgemäß auf der angegebenen Website erstellt, die Registrierungs-E-Mail wird jedoch mit dem Standardgebietsschema gesendet, wenn die Bulk-API verwendet wird.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
