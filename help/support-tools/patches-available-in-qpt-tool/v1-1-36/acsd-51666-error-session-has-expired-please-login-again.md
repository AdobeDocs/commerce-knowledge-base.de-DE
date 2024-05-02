---
title: '"ACSD-51666: Fehler "Die Sitzung ist abgelaufen, melden Sie sich bitte erneut an." nach der Anmeldung"'
description: Wenden Sie den Patch ACSD-51666 an, um das Adobe Commerce-Problem zu beheben, bei dem der Fehler *Die Sitzung ist abgelaufen ist. Melden Sie sich bitte erneut an.* tritt auf, nachdem Sie sich angemeldet haben.
feature: Customers
role: Admin, Developer
exl-id: c3913f1c-f401-440b-b6b3-10702f13fff5
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# ACSD-51666: Fehler *Die Sitzung ist abgelaufen. Melden Sie sich bitte erneut an.* nach der Anmeldung

Der Patch ACSD-51666 behebt das Problem, bei dem der Fehler *Die Sitzung ist abgelaufen. Melden Sie sich bitte erneut an.* tritt auf, nachdem Sie versucht haben, sich anzumelden. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.36 installiert ist. Die Patch-ID ist ACSD-51666. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6 - p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Sie erhalten den Fehler *Die Sitzung ist abgelaufen. Melden Sie sich bitte erneut an.* wenn versucht wird, sich mit dem neuen Kennwort von einem Gerät aus anzumelden, nachdem das Kennwort auf einem anderen Gerät zurückgesetzt wurde. Dies geschieht nur, wenn eine zusätzliche Ajax-Anfrage auf der Seite vorhanden ist, die von einem benutzerdefinierten Modul hinzugefügt wird.

<u>Zu reproduzierende Schritte</u>:

1. Installieren Sie ein benutzerdefiniertes Modul, das auf jeder Seite des Storefront eine Ajax-Anfrage hinzufügt.
1. Erstellen Sie ein neues Konto.
1. Melden Sie sich ab und gehen Sie zurück zur Anmeldeseite.
1. Öffnen Sie die *Kennwort vergessen* in einem anderen Browser verknüpfen und die *Kennwort zurücksetzen* E-Mail
1. Öffnen Sie die E-Mail zum Zurücksetzen des Kennworts im ersten Browser und legen Sie das neue Kennwort fest.
1. Versuchen Sie, sich im zweiten Browser anzumelden.

<u>Erwartete Ergebnisse</u>:

Sie können sich beim ersten Versuch erfolgreich anmelden.

<u>Tatsächliche Ergebnisse</u>:

* Sie sehen die *Die Sitzung ist abgelaufen. Melden Sie sich bitte erneut an.* Fehler.
* Sie werden nicht angemeldet und zur Homepage weitergeleitet.
* Ihr zweiter Anmeldeversuch ist erfolgreich.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
