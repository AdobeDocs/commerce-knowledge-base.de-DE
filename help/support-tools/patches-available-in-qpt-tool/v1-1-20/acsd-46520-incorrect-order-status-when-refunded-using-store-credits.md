---
title: 'ACSD-46520: Falscher Bestellstatus bei Rückerstattung über Ladenguthaben'
description: Dieser Artikel bietet eine Lösung für das Problem, dass Benutzende einen falschen Bestellstatus erhalten, wenn sie mithilfe von Store-Guthaben zurückerstattet werden.
exl-id: 8464df22-0223-4ded-a15f-ce06eacdf77c
feature: Orders, Returns
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-46520: Falscher Bestellstatus bei Rückerstattung über Ladenguthaben

Mit dem Patch ACSD-46520 wird das Problem gelöst, dass Benutzende einen falschen Bestellstatus erhalten, wenn sie über Ladenguthaben zurückerstattet werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20 installiert ist. Die Patch-ID ist ACSD-46520. Beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 und 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.5

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Benutzende erhalten bei der Rückerstattung über Ladenguthaben einen falschen Bestellstatus.

<u>Schritte zur Reproduktion</u>:

1. Kundenkonto in der Storefront erstellen und sich anmelden.
1. Weisen Sie dem Kunden vom Administrator Gutschriften aus dem Store zu. Die Ladenguthaben sollten die gesamte Bestellung abdecken.
1. Bestellen Sie mit den Gutschriften aus dem Geschäft.
1. Rechnung der Bestellung.
1. Erstellen Sie eine Gutschrift, um den gesamten Bestellbetrag zurückzuerstatten.
Aktivieren Sie das Kontrollkästchen **[!UICONTROL Refund to store credit]** .
1. Überprüfen Sie den Bestellstatus.

<u>Erwartete Ergebnisse</u>:

Der Bestellstatus lautet *Geschlossen*.

<u>Tatsächliche Ergebnisse</u>:

Der Bestellstatus ist *Abgeschlossen* was nicht der richtige Status ist.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder [!DNL Magento Open Source] On-Premise: [Quality Patches Tools > Usage](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im Handbuch Quality Patches Tool.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html?lang=de)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im Handbuch Quality Patches Tool.
