---
title: 'MDVA-39195: Zum Warenkorb hinzufügen ist auf der Kategorieseite inaktiv'
description: Der Patch MDVA-39195 löst das Problem, dass die Schaltfläche **Zum Warenkorb hinzufügen** auf der Kategorieseite inaktiv ist, wenn die Umleitung zum Warenkorb aktiviert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-39195. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.
exl-id: de434908-e13a-4ab5-abb1-570bcc59c83d
feature: Categories, Orders, Shopping Cart
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# MDVA-39195: Zum Warenkorb hinzufügen ist auf der Kategorieseite inaktiv

Der Patch MDVA-39195 löst das Problem, dass die Schaltfläche **Zum Warenkorb hinzufügen** auf der Kategorieseite inaktiv ist, wenn die Umleitung zum Warenkorb aktiviert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-39195. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die **„Zum Warenkorb hinzufügen** auf der Kategorieseite ist inaktiv, wenn die Umleitung zum Warenkorb aktiviert ist.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie **Stores** > Einstellungen > **Konfiguration** > **Verkauf** > **Checkout**.
1. Erweitern Sie den **Warenkorb**.
1. Legen Sie die **Nach dem Hinzufügen einer Produktumleitung zum Warenkorb** auf Ja fest.
1. Besuchen Sie die Kategorieseite.

<u>Erwartete Ergebnisse</u>:

**Zum Warenkorb hinzufügen** ist auf der Kategorieseite aktiv.

<u>Tatsächliche Ergebnisse</u>:

**Zum Warenkorb hinzufügen**-Schaltfläche auf der Kategorieseite ist inaktiv.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) in unserer Entwicklerdokumentation.
