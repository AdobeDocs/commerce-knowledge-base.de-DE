---
title: '"ACSD-51636: Unternehmensadministrator kann keine neuen Benutzer aus dem Abschnitt "Kundenkonto"hinzufügen."'
description: Wenden Sie den Patch ACSD-51636 an, um das Adobe Commerce-Problem zu beheben, bei dem der Unternehmensadministrator keine neuen Benutzer aus dem Abschnitt "Kundenkonto"hinzufügen kann, obwohl er über alle erforderlichen Rollen und Berechtigungen verfügt.
feature: Admin Workspace, B2B, Companies, Customer Service
role: Admin
exl-id: 78395584-e5d3-414e-859d-a68ce1af5af1
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-51636: Unternehmensadministrator kann keine neuen Benutzer aus dem Abschnitt &quot;Kundenkonto&quot;hinzufügen

Der Patch ACSD-51636 behebt das Problem, dass der Unternehmensadministrator keine neuen Benutzer aus dem Abschnitt &quot;Kundenkonto&quot;hinzufügen kann, obwohl er über alle erforderlichen Rollen und Berechtigungen verfügt. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.34 ist installiert. Die Patch-ID ist ACSD-51636. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Unternehmensadministrator kann keine neuen Benutzer aus dem Abschnitt &quot;Kundenkonto&quot;hinzufügen, obwohl er über alle erforderlichen Rollen und Berechtigungen verfügt.

Voraussetzungen:

* Das B2B-Modul ist installiert.
* Die Unternehmensfunktionalität ist aktiviert.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein neues Unternehmen.
1. Navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.
1. Bearbeiten **[!UICONTROL Company Admin]** type to *Kunde*.
1. Melden Sie sich als Kunde an.
1. Navigieren Sie zu **[!UICONTROL My Account]** > **[!UICONTROL Company Users]** > **[!UICONTROL Add User]** und fügen Details für den Benutzer hinzu und aktivieren Sie sie.
1. Speichern Sie den neuen Benutzer.

<u>Erwartete Ergebnisse</u>

Der Admin-Benutzer kann einen neuen Benutzer hinzufügen.

<u>Tatsächliche Ergebnisse</u>

* Der Administrator erhält eine Fehlermeldung: *Etwas ist schiefgegangen*.
* Der Admin-Benutzer kann keinen neuen Kunden erstellen.
* Das Protokoll enthält den folgenden Fehler:

  ```PHP
      report.CRITICAL: Error: Call to a member function __toArray() on null in app/code/Magento/LoginAsCustomerLogging/Observer/LogSaveCustomerObserver.php:123
  ```

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) im [!DNL Quality Patches Tool] Handbuch.
