---
title: 'MDVA-38666: Admin-Benutzer kann konfigurierbare Produktoptionen nicht ändern'
description: Der Patch MDVA-38666 löst das Problem, dass der Administrator bzw. die Administratorin nicht in der Lage ist, konfigurierbare Produktoptionen im Warenkorb des Kunden zu ändern. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-38666. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
exl-id: 72440e47-1deb-41da-a225-d4bc73029ad5
feature: Admin Workspace, Configuration, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# MDVA-38666: Admin-Benutzer kann konfigurierbare Produktoptionen nicht ändern

Der Patch MDVA-38666 löst das Problem, dass der Administrator bzw. die Administratorin nicht in der Lage ist, konfigurierbare Produktoptionen im Warenkorb des Kunden zu ändern. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-38666. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.2 - 2.3.5-p2

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Administrator bzw. die Administratorin kann die konfigurierbaren Produktoptionen im Warenkorb des Kunden nicht ändern.

<u>Schritte zur Reproduktion</u>:

1. Legen Sie den Kundenkontobereich auf „Global“ fest.
1. Erstellen Sie zwei Websites mit Stores.
1. Erstellen Sie zwei konfigurierbare Produkte und weisen Sie sie jeder Website zu.
1. Erstellen Sie ein Kundenkonto im Frontend und melden Sie sich an.
1. Fügen Sie ein Produkt zum Warenkorb hinzu und checken Sie es aus (dies erfolgt, um die Angebots-IDs auf jeder Website zu verändern).
1. Fügen Sie ein Produkt zum Warenkorb hinzu und lassen Sie es.
1. Wechseln Sie zur zweiten Website und fügen Sie das Produkt zum Warenkorb hinzu (die gleiche Anmeldung sollte funktionieren, da der Umfang des Kundenkontos auf „global“ festgelegt ist).
1. Öffnen Sie den Kunden über die Admin Console und navigieren Sie zur Registerkarte Warenkorb .
1. Wechseln Sie den Store aus der Dropdown-Liste und versuchen Sie, die Konfiguration zu ändern.

<u>Erwartete Ergebnisse</u>:

Der Benutzer erhält ein Popup mit konfigurierbaren Optionen.

<u>Tatsächliche Ergebnisse</u>:

Es wird kein Popup-Formular angezeigt. Der/die Benutzende kann die Konfiguration nicht ändern.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in unserer Entwicklerdokumentation.
