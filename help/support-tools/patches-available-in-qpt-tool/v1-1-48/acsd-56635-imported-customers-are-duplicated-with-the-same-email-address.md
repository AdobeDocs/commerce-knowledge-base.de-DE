---
title: '"ACSD-56635: Importierte Kunden werden dupliziert, wenn die Kontofreigabe auf [!DNL Global]'''
description: Wenden Sie den Patch ACSD-56635 an, um das Adobe Commerce-Problem zu beheben, bei dem der importierte Kunde mit derselben E-Mail-Adresse dupliziert wird, wenn der Import verwendet wird und die Kontofreigabe auf eingestellt ist [!DNL Global].
feature: Customers, Attributes
role: Admin, Developer
source-git-commit: 86d752c9c2791ef19960876afafe24fefe5d29ed
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-56635: Importierte Kunden werden mit derselben E-Mail-Adresse dupliziert, wenn die Kontofreigabe auf [!DNL Global]

Der Patch ACSD-56635 behebt das Problem, dass der importierte Kunde mit derselben E-Mail-Adresse dupliziert wird, wenn der Import verwendet wird und die Kontofreigabe auf eingestellt ist. [!DNL Global]. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48 ist installiert. Die Patch-ID ist ACSD-56635. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6 - p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Importierte Kunden werden mit derselben E-Mail-Adresse dupliziert, wenn die Kontofreigabe auf [!DNL Global].

<u>Zu reproduzierende Schritte</u>:

1. Unter der Adobe Commerce (2.4-develop b2b) **[!UICONTROL Admin]**, Zugriff **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]**.
1. Legen Sie die *[!UICONTROL Share Customer Accounts]* Einstellung auf *[!DNL Global]*.
1. Erstellen Sie mehrere Websites und Stores:

   * ws1 > s11, s12 > sw11, sw122
   * ws2 > s21, s22 > sw211, sw212

1. Erstellen Sie einen neuen Kunden unter dem *Hauptseite* vom Administrator mit der als <adb@yormail.com>.
1. under **[!UICONTROL Admin]**, navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Import]**.
1. Auswählen **[!UICONTROL Customer Entity Type]** as *[!UICONTROL Customers Main File]*.
1. Verwenden Sie dieselbe E-Mail-Adresse wie <adb@yormail.com> auf einer anderen Website, z. B. ws1. Siehe Beispiel für eine CSV-Datei customer.csv im Folgenden.
1. Schließen Sie den Import ab, um den neuen Benutzer anzuzeigen, der unter der *ws1* Website mit derselben E-Mail-Adresse.

customer.csv-Inhalt:

```
email,_website,_store,confirmation,created_at,created_in,disable_auto_group_change,dob,firstname,gender,group_id,lastname,middlename,password_hash,prefix,rp_token,rp_token_created_at,store_id,suffix,taxvat,updated_at,website_id,password
adb@yopmail.com,ws1,sv111,,09/01/24 12:49,Default Store View,0,,newjon,,1,newDoe,,d708be3fe0fe0120840e8b13c8faae97424252c6374227ff59c05814f1aecd79:mgLqkqgTwLPLlCljzvF8hp67fNOOvOZb:1,,07e71459c137f4da15292134ff459cba,30/10/15 12:49,1,,,09/01/24 12:49,1,
```

<u>Erwartete Ergebnisse</u>:

Der importierte Kunde mit derselben E-Mail-Adresse wird aktualisiert, anstatt dupliziert zu werden.

<u>Tatsächliche Ergebnisse</u>:

Bei Verwendung des Kundenimports werden doppelte Kunden mit derselben E-Mail-Adresse erstellt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
