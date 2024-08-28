---
title: '"ACSD-46938: Leistungsprobleme mit DB-Triggern während "setup:upgrade"'
description: Wenden Sie den Patch ACSD-46938 an, um das Adobe Commerce-Problem zu beheben, bei dem der Befehl "setup:upgrade"den Indexmodus von geplant zu speichern ändert und zu erheblichen Leistungseinbußen führt.
feature: Upgrade
role: Admin, Developer
source-git-commit: cbd16ac7c6d6d7a4e3786880409475a10964c070
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-46938: Leistungsprobleme mit DB-Triggern während `setup:upgrade`

Der Patch ACSD-46938 behebt das Problem, bei dem der Befehl `setup:upgrade` den Indexmodus von einem Zeitplan zum Speichern ändert, was zu erheblichen Leistungseinbußen führt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 installiert ist. Die Patch-ID lautet ACSD-46938. Beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5-p9

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Leistungsbeeinträchtigung bei der DB-Trigger-Neuerstellung in `setup:upgrade`.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie einen großen Katalog mit vielen Produkten und Kategorien.
1. Melden Sie sich bei [!UICONTROL Admin] an.
1. Setzen Sie alle Indexer auf den Modus [!UICONTROL Update By Schedule] .
1. Öffnen Sie ein beliebiges Produkt.
1. Aktualisieren Sie es. Weisen Sie ihr beispielsweise eine neue Kategorie zu.
1. Klicken Sie auf [!UICONTROL Save].
1. Führen Sie die Befehle `bin/magento setup:upgrade` und `bin/magento cron:run` parallel aus.

<u>Erwartete Ergebnisse</u>:

Die Ausführungszeit des Befehls `bin/magento setup:upgrade` erhöht sich erheblich, wenn der Befehl `bin/magento cron:run` gleichzeitig ausgeführt wird.

<u>Tatsächliche Ergebnisse</u>:

Die Ausführungsdauer des Befehls nimmt nicht zu.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
