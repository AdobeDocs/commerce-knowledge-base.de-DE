---
title: 'MDVA-39384: Benutzerdefiniertes Kundenattribut für Firmenbenutzer kann nicht gespeichert werden'
description: Der Patch MDVA-39384 löst das Problem, dass das benutzerdefinierte Kundenattribut für einen Firmenbenutzer nicht gespeichert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-39384. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
exl-id: b9864ca6-307b-4649-b764-4512abc503d3
feature: Attributes, B2B, Companies
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# MDVA-39384: Benutzerdefiniertes Kundenattribut für Firmenbenutzer kann nicht gespeichert werden

Der Patch MDVA-39384 löst das Problem, dass das benutzerdefinierte Kundenattribut für einen Firmenbenutzer nicht gespeichert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-39384. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.1 - 2.3.6, 2.4.1 - 2.4.3

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Benutzerdefiniertes Kundenattribut für einen Firmenbenutzer wird nicht gespeichert.

<u>Voraussetzungen</u>:

B2B-Module werden installiert.

<u>Schritte zur Reproduktion</u>:

1. Gehen Sie zu **Stores** > Einstellungen > **Konfiguration** > **B2B-** und setzen Sie **Firma aktivieren** auf Ja.
1. Benutzerdefiniertes Kundenattribut erstellen:
   * Erforderliche Werte: Ja (optional, aktivieren Sie diese, damit der Validierungsfehler angezeigt wird).
   * In Storefront anzeigen: Ja.
   * Forms zu verwenden in: Alle in der Liste verfügbaren.
1. Erstellen Sie eine Firma und melden Sie sich als Unternehmensadministrator an.
1. Navigieren Sie in Ihrem Konto zur Unternehmensstruktur .
1. Klicken Sie auf den Link **Benutzer hinzufügen**.
1. Füllen Sie das Formular mit dem benutzerdefinierten Attribut aus.
1. Klicken Sie **Speichern**.

<u>Erwartete Ergebnisse</u>:

Die benutzerdefinierten Attributwerte werden mit dem neuen Firmenbenutzer gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Die benutzerdefinierten Attributwerte werden NICHT mit dem neuen Firmenbenutzer gespeichert.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) in unserer Entwicklerdokumentation.
