---
title: "ACSD-52929: Redundante Anfrage zur Neuindizierung von Standardquellelementen"
description: Wenden Sie den Patch ACSD-52929 an, um das Adobe Commerce-Problem zu beheben, bei dem eine redundante Anfrage zur Neuindizierung der Standardquellelemente vorliegt, wenn der Inventarindexer im asynchronen Modus konfiguriert ist.
feature: Configuration, Inventory
role: Admin, Developer
exl-id: 978fe0d0-3917-4ba2-94bb-01c607a825cc
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-52929: Redundante Anfrage zum Neuindizieren von Standardquellelementen

Der Patch ACSD-52929 behebt das Problem, bei dem Anforderungen an die Neuindizierung von Standardquellelementen Redundanz aufweisen, wenn der Inventarindexer im asynchronen Modus konfiguriert ist. Dieser Patch ist verfügbar, wenn die Variable [!DNL Quality Patches Tool (QPT)] 1.1.38 installiert ist. Die Patch-ID ist ACSD-52929. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6 - p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Es gibt eine Redundanz von Anforderungen zur Neuindizierung von Standardquellelementen, wenn der Inventarindexer im asynchronen Modus konfiguriert ist.

<u>Zu reproduzierende Schritte</u>:

1. Konfigurieren [!DNL RabbitMQ].
1. Aktivieren Sie die asynchrone Neuindizierungsstrategie, indem Sie **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Inventory Indexer Setting]** und **[!UICONTROL Stock/Source reindex strategy]=[!UICONTROL Asynchronous]**.
1. Erstellen Sie eine benutzerdefinierte Inventarquelle.
1. Anmelden bei der [!DNL RabbitMQ] Dashboard und rufen Sie die Registerkarte &quot;Warteschlangen&quot;auf.
1. Überprüfen `inventory.indexer.sourceItem` und stellen Sie sicher, dass keine Nachrichten gesendet werden.
1. Öffnen Sie ein einfaches Produkt aus dem Backend und fügen Sie *[!UICONTROL stock only]* in die benutzerdefinierte Quelle eingeben und das Produkt speichern.
1. Laden Sie die `inventory.indexer.sourceItem` Warteschlange im [!DNL RabbitMQ] Dashboard und überprüfen Sie dann die Nachrichten.

<u>Erwartete Ergebnisse</u>:

Es ist nur eine Nachricht in der Warteschlange für die benutzerdefinierte Quelle vorhanden.

<u>Tatsächliche Ergebnisse</u>:

In der Warteschlange werden zwei Nachrichten angezeigt: eine für die Standardquelle und die andere für die benutzerdefinierte Quelle.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
