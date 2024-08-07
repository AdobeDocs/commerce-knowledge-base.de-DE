---
title: '"MDVA-40311: Fehler "Ungültige Sicherheit oder Formularschlüssel"nach der Anmeldung bei Admin, wenn der benutzerdefinierte Administratorpfad konfiguriert ist"'
description: 'Der Patch MDVA-40311 behebt das Problem, dass der Admin-Benutzer eine Fehlermeldung erhält: *Ungültige Sicherheit oder Formularschlüssel. Aktualisieren Sie die Seite* nach der Anmeldung beim Administrator, wenn der benutzerdefinierte Administratorpfad konfiguriert und der geheime Schlüssel aktiviert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 installiert ist. Die Patch-ID lautet MDVA-40311. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben werden soll."'
exl-id: d4562f09-0aed-438e-8c2e-90557aa2f146
feature: Admin Workspace, Compliance, Security
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-40311: Fehler &quot;Ungültige Sicherheit oder Formularschlüssel&quot;nach der Anmeldung bei Admin, wenn der benutzerdefinierte Administratorpfad konfiguriert ist

Der Patch MDVA-40311 behebt das Problem, dass der Admin-Benutzer eine Fehlermeldung erhält: *Ungültige Sicherheit oder Formularschlüssel. Aktualisieren Sie die Seite* nach der Anmeldung beim Administrator, wenn der benutzerdefinierte Administratorpfad konfiguriert und der geheime Schlüssel aktiviert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 installiert ist. Die Patch-ID lautet MDVA-40311. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Administrator erhält eine Fehlermeldung: *Ungültige Sicherheit oder Formularschlüssel. Aktualisieren Sie die Seite* nach der Anmeldung beim Administrator, wenn der benutzerdefinierte Administratorpfad konfiguriert und der geheime Schlüssel aktiviert ist.

<u>Zu reproduzierende Schritte</u>:

* Melden Sie sich mit einem gültigen Benutzernamen und Kennwort als Admin-Benutzer an.

<u>Erwartete Ergebnisse</u>:

Der Benutzer kann sich ohne Fehlermeldung anmelden.

<u>Tatsächliche Ergebnisse</u>:

*Ungültige Sicherheit oder Formularschlüssel. Bitte aktualisieren Sie, dass die Fehlermeldung Seite* angezeigt wird.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
