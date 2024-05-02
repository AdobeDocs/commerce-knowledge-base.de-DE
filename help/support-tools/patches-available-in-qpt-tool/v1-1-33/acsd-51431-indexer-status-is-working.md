---
title: '"ACSD-51431: Indexerstatus ist *[!UICONTROL Working]* auch wenn es keine Einträge in der changelog'' gibt'
description: Wenden Sie den Patch ACSD-51431 an, um das Adobe Commerce-Problem zu beheben, bei dem der Indexstatus * lautet.[!UICONTROL Working]* auch wenn es keine Einträge in der changelog gibt.
feature: Logs, Price Indexer
role: Admin
exl-id: 85977b78-7f6b-47c7-b33e-16668bdf98fe
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-51431: Indexerstatus *[!UICONTROL Working]* auch wenn es keine Einträge im Changelog gibt

Der Patch ACSD-51431 behebt das Leistungsproblem bei Indexerstatus *[!UICONTROL Working]* auch wenn es keine Einträge in der changelog gibt. Dieser Patch ist verfügbar, wenn die Variable [!DNL Quality Patches Tool (QPT)] 1.1.33 installiert ist. Die Patch-ID ist ACSD-51431. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Indexstatus lautet *[!UICONTROL Working]* auch wenn es keine Einträge in der changelog gibt.

<u>Zu reproduzierende Schritte</u>:

1. Satz **[!UICONTROL indexers]** nach [!UICONTROL Update on Schedule].
1. Konfigurieren Sie den Cron-Auftrag so, dass er jede Minute ausgeführt wird.
1. Speichern Sie Änderungen an verschiedenen Produkten gleichzeitig.
1. Ausführen `bin/magento indexer:status` in ein paar Minuten.

<u>Erwartete Ergebnisse</u>:

Die Änderungen werden verarbeitet und die Indexer befinden sich in *[!UICONTROL Ready]* -Status. Die *[!UICONTROL Schedule]* status is *[!UICONTROL idle (0 in the backlog)]*.

<u>Tatsächliche Ergebnisse</u>:

Die Änderungen werden verarbeitet und die Indexer befinden sich in *[!UICONTROL Ready]* -Status. Die Variable *[!UICONTROL Schedule]* Statusanzeigen *[!UICONTROL working (0 in the backlog)]*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
