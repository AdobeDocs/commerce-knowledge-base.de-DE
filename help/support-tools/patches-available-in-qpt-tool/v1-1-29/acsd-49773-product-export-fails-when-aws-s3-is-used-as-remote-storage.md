---
title: "ACSD-49773: Produktexport schlägt fehl, wenn AWS S3 als Remote-Speicher verwendet wird"
description: Wenden Sie den Patch ACSD-49773 an, um das Adobe Commerce-Problem zu beheben, bei dem der Produktexport fehlschlägt, wenn AWS S3 als Remote-Speicher verwendet wird.
exl-id: 5ef853c3-8080-4403-836b-6fff93ec71c6
feature: Data Import/Export, Iaas, Products, Storage
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-49773: Produktexport schlägt fehl, wenn AWS S3 als Remote-Speicher verwendet wird

Der Patch ACSD-49773 behebt das Problem, bei dem der Produktexport fehlschlägt, wenn AWS S3 als Remote-Speicher verwendet wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 installiert ist. Die Patch-ID ist ACSD-49773. Beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.5-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Produktexport schlägt fehl, wenn AWS S3 als Remote-Speicher verwendet wird.

<u>Zu reproduzierende Schritte</u>:

1. Installieren Sie ein großes Datenprofil.
1. Erstellen Sie ein AWS-Konto und konfigurieren Sie einen S3-Bucket und einen IAM-Benutzer.
1. Aktualisieren Sie `app/etc/env.php` mit den Konfigurationen.
1. Führen Sie `bin/magento setup:upgrade` aus.
1. Gehen Sie zum Backend und führen Sie einen vollständigen Produktexport durch.
1. Überwachen Sie den Nachrichtenstatus der Warteschlange in der Tabelle `[queue_message_status]` .
1. Überprüfen Sie die Systemprotokolle.

<u>Erwartete Ergebnisse</u>:

Der Produktexport wird fehlerfrei abgeschlossen.

<u>Tatsächliche Ergebnisse</u>:

In den Systemprotokollen wird ein Fehler protokolliert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
