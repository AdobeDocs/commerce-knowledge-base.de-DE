---
title: "ACSD-52133: Kundenkonto kann nach einem Upgrade nicht gespeichert werden"
description: Wenden Sie den Patch ACSD-52133 an, um das Adobe Commerce-Problem zu beheben, bei dem ein Kundenkonto nach einem Upgrade nicht gespeichert werden kann.
feature: Customers, Upgrade
role: Admin
exl-id: 0db7c79e-10e1-4850-81b5-4812fb051941
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-52133: Kundenkonto kann nach einem Upgrade nicht gespeichert werden

Der Patch ACSD-52133 behebt das Problem, dass ein Kundenkonto nach einem Upgrade nicht gespeichert werden kann. Dieser Patch ist verfügbar, wenn die Variable [!DNL Quality Patches Tool (QPT)] 1.1.35 installiert ist. Die Patch-ID ist ACSD-52133. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Kundenkonto kann nach einem Upgrade nicht gespeichert werden.

<u>Zu reproduzierende Schritte</u>:

1. Installieren Sie Adobe Commerce-Version 2.4.4.
1. Erstellen Sie einen Kunden.
1. Aktualisieren Sie Adobe Commerce von der früheren Version 2.4.4 auf 2.4.6, wo bereits ein Kunde erstellt wurde.
1. Legen Sie den Verschlüsselungsschlüssel wie unten unter `env.php`:

   `d337b914e91ff703b1e94ba4156aadf0`

1. Legen Sie die unten stehenden Werte für alle Kunden unter der Variablen `customer_entity` table:

   ```
   -> rp_token as incr4869
   -> rp_token_created_at as "2021-04-29 20:06:14"
   ```

1. Navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.
1. Bearbeiten Sie den Kunden, für den die obigen Werte aktualisiert wurden.
1. Klicken Sie auf **[!UICONTROL Save Customer]** oder **[!UICONTROL Save and Continue Edit]**

<u>Erwartete Ergebnisse</u>:

Der Kunde wird erfolgreich ohne Fehler gespeichert.

<u>Tatsächliche Ergebnisse</u>:

* Der Kundendatensatz wird nicht gespeichert.
* Dem Administrator wird die folgende Fehlermeldung angezeigt: *Beim Speichern des Kunden ist etwas schiefgelaufen.*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
