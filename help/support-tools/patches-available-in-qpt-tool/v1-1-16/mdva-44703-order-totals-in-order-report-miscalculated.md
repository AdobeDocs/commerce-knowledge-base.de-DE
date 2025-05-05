---
title: 'MDVA-44703: Die Bestellsummen im Bericht „Bestellungen“ sind falsch berechnet'
description: Der Patch MDVA-44703 behebt das Problem, dass die Bestellsummen im Bericht Bestellungen für den Benutzer mit eingeschränkten Administratorrechten falsch berechnet werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 installiert ist. Die Patch-ID lautet MDVA-44703. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.
exl-id: d8c31e47-ace6-4dba-a57c-941e722a6aad
feature: Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# MDVA-44703: Die Bestellsummen im Bericht „Bestellungen“ sind falsch berechnet

Der Patch MDVA-44703 behebt das Problem, dass die Bestellsummen im Bericht Bestellungen für den Benutzer mit eingeschränkten Administratorrechten falsch berechnet werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 installiert ist. Die Patch-ID lautet MDVA-44703. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.4

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Bestellsummen im Bericht „Bestellungen“ sind für den eingeschränkten Admin-Benutzer falsch berechnet.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine zusätzliche Website mit zwei Stores.
1. Erstellen Sie einen Benutzer mit eingeschränktem Administratorzugriff, der nur auf die neue Website zugreifen darf.
1. Melden Sie sich als eingeschränkter Admin-Benutzer an.
1. Erstellen Sie zwei Bestellungen mit unterschiedlichen Gesamtwerten, eine für jeden neuen Store.
1. Rechnungen für die Bestellungen erstellen.
1. Navigieren Sie zu **Berichte** > **Vertrieb** und öffnen Sie **Bestellungsbericht**.
1. Statistiken aktualisieren.
1. Siehe den Bericht für jeden Shop.

<u>Erwartete Ergebnisse</u>:

Die Verkaufssummen entsprechen dem Bestellbetrag jedes Geschäfts.

<u>Tatsächliche Ergebnisse</u>:

Die aggregierte Verkaufssumme für die gesamte Website wird für jeden Shop angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) in unserer Entwicklerdokumentation.
