---
title: "ACSD-52041: Beim Rendern von Seiten-Builder werden keine Sperren veröffentlicht."
description: Wenden Sie den Patch ACSD-52041 an, um das Adobe Commerce-Problem zu beheben, bei dem der Seitenaufbau fünf Sekunden lang gerendert wird, ohne Sperren zu veröffentlichen.
feature: Page Builder
role: Admin, Developer
exl-id: f2a1fd36-2098-46a7-aa42-3a5a0014adc9
source-git-commit: fc5dc9fcf610cae6f8c0a334b4ef15029c462c66
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# ACSD-52041: Beim Rendern von Seiten-Builder werden keine Sperren veröffentlicht

Der Patch ACSD-52041 behebt das Problem, bei dem der Seitenaufbau fünf Sekunden lang gerendert wird, ohne Sperren freizugeben. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.48 installiert ist. Die Patch-ID ist ACSD-52041-v2. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.4-p8, 2.4.5 - 2.4.5-p7, 2.4.6 - 2.4.6-p6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Seitenaufbau wird fünf Sekunden lang gerendert, ohne Sperren freizugeben.

<u>Zu reproduzierende Schritte</u>:

1. Bearbeiten Sie eine CMS-Seite, Produktseite oder alles, was über Page Builder verfügt.
1. Speichern Sie die Änderungen.
1. Beachten Sie die Seitenspeicherzeit.

<u>Erwartete Ergebnisse</u>

Der Inhalt wird gespeichert. Keine Fehler im Browserprotokoll gefunden.

<u>Tatsächliche Ergebnisse</u>

Das Speichern dauert länger als die übliche Zeit.
Fehler in Konsole: ``Page Builder was rendering for 5 seconds without releasing locks``

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) im [!DNL Quality Patches Tool] -Handbuch.
