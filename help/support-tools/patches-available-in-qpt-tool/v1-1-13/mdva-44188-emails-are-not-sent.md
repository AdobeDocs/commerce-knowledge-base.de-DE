---
title: 'MDVA-44188: E-Mails werden nicht an IDs gesendet, die ".-"'
description: Der Patch MDVA-44188 behebt das Problem, dass E-Mails nicht an die E-Mail-IDs gesendet werden, die "" enthalten.-". Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-44188. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
exl-id: 2abd300a-6cf3-4973-9b36-1bba7b578378
feature: Communications
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# MDVA-44188: E-Mails werden nicht an IDs gesendet, die &quot;.-&quot;

Der Patch MDVA-44188 behebt das Problem, dass E-Mails nicht an die E-Mail-IDs gesendet werden, die `.-` enthalten. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-44188. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.4

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Es können keine E-Mails an E-Mail-IDs gesendet werden, die `.-` in ihrem Benutzernamen enthalten.

<u>Schritte zur Reproduktion</u>:

1. Registrieren Sie einen Kunden mit einer E-Mail-Adresse, die `.-` enthält. Beispiel: `.-foo@example.com`.
1. Bestellung aufgeben.

<u>Erwartete Ergebnisse</u>:

Benutzer mit der E-Mail-ID, die `.-` enthält, erhält wie gewohnt E-Mails.

<u>Tatsächliche Ergebnisse</u>:

E-Mail wird nicht an die E-Mail-ID gesendet, die `.-` enthält. Der folgende Fehler wird in den Fehlerprotokollen angezeigt: *Der Mailing-Warteschlange konnte keine ungültige E-Mail-Adresse hinzugefügt werden*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in unserer Entwicklerdokumentation.
