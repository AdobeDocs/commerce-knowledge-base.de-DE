---
title: 'MDVA-40175: Optionsschaltflächen werden bei der Neuanordnung nicht angezeigt'
description: Der Patch MDVA-40175 löst das Problem, dass die Optionsschaltflächen nicht angezeigt werden, wenn Benutzende versuchen, eine Neuanordnung vorzunehmen. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-40175. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.
exl-id: 307c450d-9f53-40b7-b2f5-d867850c043a
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-40175: Optionsschaltflächen werden bei der Neuanordnung nicht angezeigt

Der Patch MDVA-40175 löst das Problem, dass die Optionsschaltflächen nicht angezeigt werden, wenn Benutzende versuchen, eine Neuanordnung vorzunehmen. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-40175. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Optionsschaltflächen werden im Abschnitt Zahlungs- und Versandinformationen nicht angezeigt, wenn Benutzende versuchen, eine Neuanordnung vorzunehmen.

<u>Voraussetzungen</u>:

1. Es wird ein Kundenkonto mit einer Lieferadresse und einer Rechnungsadresse erstellt.
1. Ein einfaches Produkt wird erstellt.
1. Es sind mehrere Versandmethoden konfiguriert.
1. Mindestens eine Bestellung wird erstellt.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zum Admin-Bedienfeld > **Verkauf** > **Bestellungen**.
1. Wählen Sie die erstellte Bestellung aus.
1. Klicken Sie auf **Link** Anzeigen“.
1. Klicken Sie auf **Schaltfläche „Neu**&quot;.
1. Scrollen Sie auf der Seite nach unten zum Abschnitt **Zahlungs- und Versandinformationen**.
1. Klicken Sie auf **Klicken, um die Versandart zu**.

<u>Erwartete Ergebnisse</u>:

Die Liste der Versandmethoden mit Optionsschaltflächen wird angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Die Liste der Versandmethoden ohne Optionsschaltflächen wird angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) in unserer Entwicklerdokumentation.
