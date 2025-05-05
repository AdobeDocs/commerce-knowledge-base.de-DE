---
title: 'MDVA-40311: Fehler „Ungültiger Sicherheits- oder Formularschlüssel“ nach der Anmeldung bei Admin, wenn ein benutzerdefinierter Administratorpfad konfiguriert ist'
description: 'Mit dem Patch MDVA-40311 wird das Problem behoben, bei dem der Administrator eine Fehlermeldung erhält: *Ungültiger Sicherheits- oder Formularschlüssel. Bitte aktualisieren Sie die Seite* nach der Anmeldung bei der Administratorin bzw. dem Administrator, wenn der benutzerdefinierte Administratorpfad konfiguriert und der geheime Schlüssel aktiviert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 installiert ist. Die Patch-ID lautet MDVA-40311. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.'
exl-id: d4562f09-0aed-438e-8c2e-90557aa2f146
feature: Admin Workspace, Compliance, Security
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-40311: Fehler „Ungültiger Sicherheits- oder Formularschlüssel“ nach der Anmeldung bei Admin, wenn ein benutzerdefinierter Administratorpfad konfiguriert ist

Der Patch MDVA-40311 behebt das Problem, dass der Admin-Benutzer eine Fehlermeldung erhält: *Ungültige Sicherheit oder Formularschlüssel. Bitte aktualisieren Sie die Seite* nachdem Sie sich beim Administrator angemeldet haben, wenn der benutzerdefinierte Administratorpfad konfiguriert und der geheime Schlüssel aktiviert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 installiert ist. Die Patch-ID lautet MDVA-40311. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Administrator erhält eine Fehlermeldung: *Ungültiger Sicherheits- oder Formularschlüssel. Bitte aktualisieren Sie die Seite* nachdem Sie sich beim Administrator angemeldet haben, wenn der benutzerdefinierte Administratorpfad konfiguriert und der geheime Schlüssel aktiviert ist.

<u>Schritte zur Reproduktion</u>:

* Melden Sie sich als Admin-Benutzer mit einem gültigen Benutzernamen und Kennwort an.

<u>Erwartete Ergebnisse</u>:

Der Benutzer kann sich ohne Fehlermeldung anmelden.

<u>Tatsächliche Ergebnisse</u>:

*Ungültiger Sicherheit- oder Formularschlüssel. Bitte Seite aktualisieren* Fehlermeldung wird angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) in unserer Entwicklerdokumentation.
