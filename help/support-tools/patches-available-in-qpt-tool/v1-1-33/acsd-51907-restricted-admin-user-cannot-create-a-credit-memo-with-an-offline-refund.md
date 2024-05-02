---
title: "ACSD-51907: Eingeschränkte Administratoren können kein Kreditmemo zur Offline-Rückerstattung erstellen."
description: Wenden Sie den Patch ACSD-51907 an, um das Adobe Commerce-Problem zu beheben, bei dem der eingeschränkte Administratorbenutzer kein Kreditmemo mit einer Offline-Rückerstattung erstellen kann.
exl-id: 564e8524-f2dc-453c-be78-a920fbd47d71
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# ACSD-51907: Eingeschränkte Administratoren können kein Kreditmemo für Offline-Rückerstattung erstellen

Der Patch ACSD-51907 behebt das Leistungsproblem, bei dem der eingeschränkte Administrator kein Kreditmemo mit Offline-Rückerstattung erstellen kann. Dieser Patch ist verfügbar, wenn die Variable [!DNL Quality Patches Tool (QPT)] 1.1.33 installiert ist. Die Patch-ID ist ACSD-51907. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 &lt; 2.4.3-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Eingeschränkte Administratoren können kein Kreditmemo mit Offline-Rückerstattung erstellen.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine **customer** auf der Standardwebsite.
1. Erstellen **neue Website** mit verwandten *store* und *Store-Ansicht*.
1. Setzen Sie die Standardwebsite auf die neue Website, löschen Sie Caches.
1. Ändern der Kundenkonfiguration: **Admin** > **Store** > **Konfiguration** > **Kunden** > **Kundenkonfiguration** > **Kundenkonten freigeben = Global**.
1. Erstellen Sie eine neue Admin-Benutzerrolle, deren Rollenbereich auf eine neu erstellte Website eingestellt ist. *(nur Zugriff auf Verkaufsdaten)* in **Admin** > **System** > **Berechtigungen**.
1. Erstellen Sie ein neues Administratorkonto mit dieser Rolle.
1. Erstellen neuer Bestellungen mithilfe der Online-Zahlungsmethode *(z. B. Auth.net oder PayPal)*.
1. Melden Sie sich als eingeschränkter Administrator an.
1. Navigieren Sie zu **Vertrieb** > **Bestellungen** > then **Bestellseite**.
1. Erstellen Sie eine Rechnung.
1. Navigieren Sie zur Registerkarte Rechnungen .
1. Klicken Sie auf **Rechnung**.
1. Klicken Sie auf **[!UICONTROL Credit Memo]**.
1. Überprüfen Sie die **[!UICONTROL Refund to Store Credit]** aktivieren, legen Sie das Textfeld daneben auf *1* -Wert.
1. Klicken Sie auf **[!UICONTROL Refund Offline]** Schaltfläche.

<u>Erwartete Ergebnisse</u>:

Das Kreditmemo wird erstellt und *1$* wird dem Geschäft gutgeschrieben.

<u>Tatsächliche Ergebnisse</u>:

die Fehlermeldung, *Weitere Berechtigungen zum Anzeigen dieses Elements sind erforderlich* angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
