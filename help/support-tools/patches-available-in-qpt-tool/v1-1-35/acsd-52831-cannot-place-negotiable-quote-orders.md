---
title: '"ACSD-52831: Kann keine begebbaren Anführungsaufträge geben, wenn [!DNL Google reCAPTCHA v3 Invisible] enabled'''
description: Wenden Sie den Patch ACSD-52831 an, um das Adobe Commerce-Problem zu beheben, bei dem Sie nicht in der Lage sind, begebbare Anführungsaufträge zu tätigen, wenn Sie [!DNL Google reCAPTCHA v3 Invisible] aktiviert ist.
feature: Quotes, B2B, Checkout
role: Admin
exl-id: 80cf5592-0784-4b37-8373-abec0847a9f0
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# ACSD-52831: Kann keine begebbaren Anführungsaufträge geben, wenn [!DNL Google reCAPTCHA v3 Invisible] enabled

Der Patch ACSD-52831 behebt das Problem, dass Sie nicht in der Lage sind, begebbare Anführungsaufträge zu tätigen, wenn Sie [!DNL Google reCAPTCHA v3 Invisible] aktiviert ist. Dieser Patch ist verfügbar, wenn die Variable [!DNL Quality Patches Tool (QPT)] 1.1.35 installiert ist. Die Patch-ID ist ACSD-52831. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Es ist nicht möglich, börsenfähige Kursaufträge zu tätigen, wenn [!DNL Google reCAPTCHA v3 Invisible] aktiviert ist.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie die Anführungsfunktion für B2B.
1. Aktivieren [!DNL Google reCAPTCHA v3 Invisible] auf der Storefront, um das Auschecken/Platzieren von Bestellungen zu ermöglichen.
1. Sprechen Sie ein Angebot an und gehen Sie mit diesem Zitat zum Kasse.
1. Sie können aufgrund des CAPTCHA-Fehlers keine Bestellung aufgeben.

<u>Erwartete Ergebnisse</u>:

Das Zitat geht zum Kassengang.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten den Fehler *reCAPTCHA-Validierung fehlgeschlagen, versuchen Sie es erneut.*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
