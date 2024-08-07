---
title: "ACSD-54264: Fehler, wenn der Kunde versucht, mit einem verhandelbaren Angebot auszuchecken"
description: Wenden Sie den Patch ACSD-54264 an, um das Adobe Commerce-Problem zu beheben, bei dem die Fehlermeldung "Sie können das angeforderte Attribut nicht aktualisieren können. Zeile-ID:store_id"angezeigt, wenn ein Kunde versucht, mit einem verhandelbaren Angebot aus einer anderen Store-Ansicht auszuchecken.
feature: B2B, Checkout
role: Admin, Developer
exl-id: de8f451e-3b0a-4721-9ff4-18553477db1d
source-git-commit: 2e344b1ca4bc075bdbc9074bb431a398f0871698
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# ACSD-54264: Fehler wird angezeigt, wenn der Kunde versucht, mit einem verhandelbaren Angebot auszuchecken

Der Patch ACSD-54264 behebt das Problem, dass eine Fehlermeldung *Sie das angeforderte Attribut nicht aktualisieren können. Zeilen-ID: store_id* wird angezeigt, wenn ein Kunde versucht, mit einem übertragbaren Angebot aus einer anderen Store-Ansicht auszuchecken. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 installiert ist. Die Patch-ID ist ACSD-54264. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Fehlermeldung *Das angeforderte Attribut kann nicht aktualisiert werden. Zeilen-ID: store_id* wird angezeigt, wenn ein Kunde versucht, mit einem übertragbaren Angebot aus einer anderen Store-Ansicht auszuchecken.

<u>Voraussetzungen</u>:

Adobe Commerce B2B-Module werden installiert und aktiviert.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine zusätzliche Store-Ansicht für die Standardwebsite.
1. Aktivieren Sie die *[!UICONTROL B2B Quote]* in der Konfiguration.
1. Melden Sie sich als Firmenkunde in einer der Store-Ansichten an.
1. Fügen Sie ein Produkt zum *[!UICONTROL Shopping Cart]* hinzu.
1. Übermitteln Sie das Angebot zur Überprüfung.
1. Gehen Sie als Administrator zu **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** und senden Sie das genehmigte Angebot.
1. Ändern Sie als Firmenkunde die Store-Ansicht in eine andere Store-Ansicht.
1. Versuchen Sie es auszuchecken.

<u>Erwartete Ergebnisse</u>:

Der Kunde gibt mit diesem Angebot eine Bestellung auf.

<u>Tatsächliche Ergebnisse</u>:

* Der Fehler tritt beim Speichern der Versandinformationen auf:

  `You cannot update the request attribute. Row ID: store_id =#`

* Der folgende Fehler wird protokolliert:

  `report.CRITICAL: Magento\Framework\Exception\InputException: You cannot update the requested attribute. Row ID: store_id = 2. in /app/code/Magento/NegotiableQuote/Plugin/Quote/Model/QuoteUpdateValidator.php:100`

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
