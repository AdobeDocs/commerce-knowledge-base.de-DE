---
title: 'ACSD-51907: Benutzer mit eingeschränkter Administratorberechtigung kann keine Gutschrift für Offline-Rückerstattung erstellen'
description: Wenden Sie den Patch „ACSD-51907“ an, um das Adobe Commerce-Problem zu beheben, bei dem der eingeschränkte Administrator keine Gutschrift mit einer Offline-Rückerstattung erstellen kann.
exl-id: 564e8524-f2dc-453c-be78-a920fbd47d71
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# ACSD-51907: Benutzer mit eingeschränkter Administratorberechtigung kann keine Gutschrift für Offline-Rückerstattung erstellen

Mit dem Patch ACSD-51907 wird das Leistungsproblem behoben, bei dem der Benutzer mit eingeschränktem Administratorzugriff keine Gutschrift mit einer Offline-Rückerstattung erstellen kann. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.33 installiert ist. Die Patch-ID ist ACSD-51907. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 &lt; 2.4.3-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Ein Benutzer mit eingeschränkter Administratorberechtigung kann keine Gutschrift mit einer Offline-Rückerstattung erstellen.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie **Kunde** auf der Standardwebsite.
1. Erstellen **neuen Website** mit zugehöriger *Store*- und *Store-Ansicht*.
1. Standard-Website auf die neue Website setzen, Caches löschen.
1. Kundenkonfiguration ändern: **Admin** > **Store** > **Configuration** > **Customers** > **Kundenkonfiguration** > **Kundenkonten freigeben = Global**.
1. Erstellen Sie eine neue Admin-Benutzerrolle mit dem Rollenbereich , der auf die neu erstellte Website *nur Zugriff auf Verkaufsdaten)* unter **Admin** > **System** > **Berechtigungen** festgelegt ist.
1. Erstellen Sie ein neues Administratorkonto mit dieser Rolle.
1. Erstellen Sie eine neue Bestellung über die Online-Zahlungsmethode *(z. B. Auth.net oder PayPal)*.
1. Melden Sie sich als Benutzer mit eingeschränktem Administratorzugriff an.
1. Wechseln Sie **Verkauf** > **Bestellungen** > dann **Bestellansichtsseite**.
1. Rechnung erstellen.
1. Navigieren Sie zur Registerkarte Rechnungen .
1. Klicken Sie auf **Rechnung**.
1. Klicken Sie auf **[!UICONTROL Credit Memo]**.
1. Aktivieren Sie das Kontrollkästchen **[!UICONTROL Refund to Store Credit]** und setzen Sie das Textfeld in der Nähe auf den Wert *1*.
1. Klicken Sie auf die Schaltfläche **[!UICONTROL Refund Offline]** .

<u>Erwartete Ergebnisse</u>:

Die Gutschrift wird erstellt und *$ 1* wird an den Gutschein zurückerstattet.

<u>Tatsächliche Ergebnisse</u>:

Die Fehlermeldung *Weitere Berechtigungen sind erforderlich, um dieses Element anzuzeigen* wird angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
