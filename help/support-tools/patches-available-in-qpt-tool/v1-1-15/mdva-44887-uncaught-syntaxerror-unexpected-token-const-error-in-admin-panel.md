---
title: 'MDVA-44887: Fehler „Nicht erfasste SyntaxError: Unerwartete Token-Konstante“ im Admin-Bedienfeld'
description: 'Der Patch MDVA-44887 behebt das Problem, dass der Admin-Benutzer auf keine Menüoption klicken kann. Der Fehler *Nicht erfasster Syntaxfehler: Unerwartete Tokenanzahl* wird im Admin-Bedienfeld angezeigt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 installiert ist. Die Patch-ID lautet MDVA-44887. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.'
exl-id: 66555e66-49d0-4f80-8f77-84ee107ab12e
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# MDVA-44887: Fehler „Nicht erfasste SyntaxError: Unerwartete Token-Konstante“ im Admin-Bedienfeld

Der Patch MDVA-44887 behebt das Problem, dass der Admin-Benutzer auf keine Menüoption klicken kann. Der Fehler *Nicht erfasste SyntaxError: Unerwarteter Token-* wird im Admin-Bedienfeld angezeigt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 installiert ist. Die Patch-ID lautet MDVA-44887. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Administrator kann auf keine Menüoption klicken. Der Fehler *Nicht erfasste SyntaxError: Unerwarteter Token-* wird im Admin-Bedienfeld angezeigt.

<u>Schritte zur Reproduktion</u>:

1. JS-Bundle aktivieren.
1. Minimieren Sie die JS-Dateien.
1. Melden Sie sich beim Commerce Admin Panel an.

<u>Erwartete Ergebnisse</u>:

Der Administrator kann auf keine Menüoption klicken. In der Browser-Konsole ist ein Fehler aufgetreten: *Nicht erfasster Syntaxfehler: Unerwartete Token-*.

<u>Tatsächliche Ergebnisse</u>:

Admins können auf das Admin-Bedienfeld zugreifen.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in unserer Entwicklerdokumentation.
