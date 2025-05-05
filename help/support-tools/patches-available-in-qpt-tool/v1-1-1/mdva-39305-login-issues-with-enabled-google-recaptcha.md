---
title: 'MDVA-39305: Anmeldeproblem mit aktiviertem Google reCAPTCHA'
description: Mit dem Patch MDVA-39305 wird das Problem behoben, dass registrierte Kunden sich nicht mit aktiviertem Google reCAPTCHA anmelden können. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1 installiert ist. Die Patch-ID lautet MDVA-39305. Beachten Sie, dass das Problem in den Adobe Commerce-Versionen 2.4.4 und 2.4.7 behoben werden soll.
exl-id: 1e8e7dc7-f8f1-4432-90f4-dc73d85f353a
feature: Console
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# MDVA-39305: Anmeldeproblem mit aktiviertem Google reCAPTCHA

Mit dem Patch MDVA-39305 wird das Problem behoben, dass registrierte Kunden sich nicht mit aktiviertem Google reCAPTCHA anmelden können. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1 installiert ist. Die Patch-ID lautet MDVA-39305. Beachten Sie, dass das Problem in den Adobe Commerce-Versionen 2.4.4 und 2.4.7 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce auf Cloud-Infrastruktur 2.4.2-p1, 2.4.3-p3, 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1-p1 - 2.4.3-p3, 2.4.4-p1 - 2.4.4-p5, 2.4.5 - 2.4.6-p2

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Registrierte Kunden können sich nicht mit dem aktivierten Google reCAPTCHA anmelden.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zu **Store** > **Configuration** > **Security** > **Google reCAPTCHA Storefront** und aktivieren Sie **Google reCAPTCHA**.
1. Gehen Sie zu **Frontend**.
1. Öffnen Sie **Entwickler-Tool** Konsole im Browser.

<u>Erwartete Ergebnisse</u>:

Keine CSP-Warnungen in der Konsole.

<u>Tatsächliche Ergebnisse</u>:

CSP-Warnungen in der Konsole.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) in unserer Entwicklerdokumentation.
