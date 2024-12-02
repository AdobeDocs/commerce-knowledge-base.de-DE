---
title: 'ACSD-54472: Kunden eines abgelehnten Unternehmens können sich weiterhin authentifizieren'
description: Wenden Sie den Patch ACSD-54472 an, um das Adobe Commerce-Problem zu beheben, bei dem Kunden eines abgelehnten Unternehmens sich weiterhin authentifizieren können und Kunden eines blockierten und abgelehnten Unternehmens weiterhin Bestellungen aufgeben können.
feature: B2B
role: Admin, Developer
exl-id: 76fc4553-02b1-4563-91a9-0cda99fa4c7d
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# ACSD-54472: Kunden eines abgelehnten Unternehmens können sich weiterhin authentifizieren

Der Patch ACSD-54472 behebt das Problem, dass Kunden eines abgelehnten Unternehmens sich weiterhin authentifizieren können und Kunden eines blockierten und abgelehnten Unternehmens weiterhin Bestellungen aufgeben können. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40 installiert ist. Die Patch-ID ist ACSD-54472. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6 - p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Kunden eines abgelehnten Unternehmens können sich weiterhin authentifizieren, und Kunden eines blockierten und abgelehnten Unternehmens können weiterhin Bestellungen aufgeben.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein Unternehmen.
1. Fügen Sie Produkte über [!DNL GraphQL] zum Warenkorb hinzu.
1. Ändern Sie den Unternehmensstatus in &quot;*Blocked*&quot;.
1. Senden Sie eine [!DNL GraphQL] -Anfrage, um die Bestellung zu platzieren und ein verhandelbares Angebot zu erstellen.
1. Ändern Sie den Unternehmensstatus in &quot;*Abgelehnt*&quot;.
1. Senden Sie eine [!DNL GraphQL] -Anfrage, um das Benutzerautorisierungstoken des Unternehmens abzurufen.
1. Stellen Sie den Kundenstatus auf *Inaktiv* ein.
1. Senden Sie eine [!DNL GraphQL] -Anfrage, um das Benutzerautorisierungstoken des Unternehmens abzurufen.

<u>Erwartete Ergebnisse</u>:

* Die Bestellung und das verhandelbare Angebot werden vom Benutzer des Unternehmens *Blocked* nicht platziert.
* Das Autorisierungstoken wird für den Benutzer des Unternehmens *Abgelehnt* nicht abgerufen.
* Das Autorisierungstoken wird für den Kunden *Inaktiv* nicht abgerufen.

<u>Tatsächliche Ergebnisse</u>:

* Die Bestellung und das verhandelbare Angebot werden vom Benutzer des Unternehmens *Blocked* platziert.
* Das Autorisierungstoken wird für den Benutzer des Unternehmens *Abgelehnt* abgerufen.
* Das Autorisierungstoken wird für den Kunden *Inaktiv* abgerufen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
