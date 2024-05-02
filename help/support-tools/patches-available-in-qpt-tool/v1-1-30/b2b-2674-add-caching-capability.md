---
title: "B2B-2674: Fügt der GraphQL-Abfrage customAttributeMetadata eine Caching-Funktion hinzu."
description: Wenden Sie den Patch B2B-2674 an, um der GraphQL-Abfrage customAttributeMetadata eine Caching-Funktion hinzuzufügen.
feature: Attributes, B2B, Cache, GraphQL
role: Admin
exl-id: a4efb268-f811-41f2-a788-a8cfc3016f61
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# B2B-2674: Fügt der `customAttributeMetadata` GraphQL-Abfrage

Der Patch B2B-2674 erweitert die `customAttributeMetadata` GraphQL-Abfragen. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 installiert ist. Die Patch-ID lautet B2B-2674. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7-Beta1 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

`customAttributeMetadata` GraphQL-Abfrage kann nicht zwischengespeichert werden.

<u>Voraussetzungen</u>:

* Server verweist auf [!DNL Varnish] Weiterleitung an das Adobe Commerce-Backend.
* Konfigurationseinstellung `system/full_page_cache/caching_application` auf *2* ([!DNL Varnish]) oder navigieren Sie zu Adobe Commerce Admin > **[!UICONTROL Stores]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Caching Application]** > und setzen Sie sie auf [!DNL Varnish].

Nachdem der Patch angewendet wurde, führen Sie die folgenden Schritte aus, um sicherzustellen, dass die Zwischenspeicherungsfunktion jetzt verfügbar ist:

1. Senden `GET` Anfrage an die oben aufgeführte GraphQL-Abfrage mit beliebigen Feldern.
1. Senden Sie die Anfrage ohne Änderungen erneut. Sie werden feststellen, dass sie viel schneller ist. Beachten Sie, dass die Anfrage nicht an das Backend gesendet wird, aber vollständig von [!DNL Varnish] als Cache-Treffer.
1. Wenn ein weiterer Nachweis erforderlich ist, kommentieren Sie die Unmenge von `X-Magento-Debug` -Kopfzeile in unserer [VCL](https://github.com/magento/magento2/blob/2.4-develop/app/code/Magento/PageCache/etc/varnish6.vcl#L239), starten Sie [!DNL Varnish] und führen Sie die oben genannten Schritte erneut aus.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
