---
title: 'ACSD-46938: Leistungsprobleme mit DB-Triggern während „setup:upgrade“'
description: Wenden Sie den Patch ACSD-46938 an, um das Adobe Commerce-Problem zu beheben, bei dem der Befehl „setup:upgrade“ den Indexermodus von „schedule“ in „save“ ändert, was zu erheblichen Leistungseinbußen führt.
feature: Upgrade
role: Admin, Developer
exl-id: 967727ed-f490-4233-a2b0-fcb2fa3f964b
source-git-commit: 151e5b70433fbebf0e2b1376d7fc540850978bb0
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-46938: Leistungsprobleme mit DB-Triggern beim `setup:upgrade`

Mit dem Patch ACSD-46938 wird das Problem behoben, dass der Befehl `setup:upgrade` den Indexermodus von Zeitplan in Speichern ändert, was zu erheblichen Leistungseinbußen führt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 installiert ist. Die Patch-ID ist ACSD-46938. Beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5-p9

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Leistungseinbußen bei der Neuerstellung des DB-Triggers in `setup:upgrade`.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie einen großen Katalog mit vielen Produkten und Kategorien.
1. Melden Sie sich beim [!UICONTROL Admin] an.
1. Setzen Sie alle Indexer auf den [!UICONTROL Update By Schedule].
1. Öffnen Sie ein beliebiges Produkt.
1. Aktualisieren Sie sie. Weisen Sie ihm beispielsweise eine neue Kategorie zu.
1. Klicken Sie auf [!UICONTROL Save].
1. Führen Sie `bin/magento setup:upgrade` und `bin/magento cron:run` Befehle parallel aus.

<u>Erwartete Ergebnisse</u>:

Die Ausführungszeit des `bin/magento setup:upgrade`-Befehls erhöht sich erheblich, wenn der `bin/magento cron:run`-Befehl gleichzeitig ausgeführt wird.

<u>Tatsächliche Ergebnisse</u>:

Die Ausführungszeit des Befehls erhöht sich nicht.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
