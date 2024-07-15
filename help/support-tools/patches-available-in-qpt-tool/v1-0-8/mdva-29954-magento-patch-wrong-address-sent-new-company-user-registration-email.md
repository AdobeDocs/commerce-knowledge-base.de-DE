---
title: "MDVA-29954: Falsche Adresse hat eine E-Mail zur Registrierung neuer Firmenbenutzer gesendet."
description: Der Patch MDVA-29954 behebt das Problem, dass die E-Mails "Neue Firmenregistrierungsanfrage"und "Sie wurden mit einem Unternehmen verknüpft"von der falschen E-Mail-Adresse gesendet werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.
exl-id: 9b3d1b93-3fe6-40a0-a68a-3e3d789c6d66
feature: B2B, Communications, Companies
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# MDVA-29954: Falsche Adresse schickte eine E-Mail zur Registrierung neuer Firmenbenutzer

Der Patch MDVA-29954 behebt das Problem, dass die E-Mails &quot;Neue Firmenregistrierungsanfrage&quot;und &quot;Sie wurden mit einem Unternehmen verknüpft&quot;von der falschen E-Mail-Adresse gesendet werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.3.5-p2, 2.4.0 und 2.4.1.

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Voraussetzungen</u>:

Installieren Sie Adobe Commerce mit B2B, wobei **B2B-Funktionen** und **Unternehmen** aktiviert sind.

<u>Zu reproduzierende Schritte</u>:

1. Klicken Sie in der Storefront auf das Dropdown-Menü **Konto erstellen** und wählen Sie **Neues Unternehmenskonto erstellen** aus.
1. Füllen Sie die erforderlichen Felder aus und registrieren Sie das Konto.
1. Aktivieren Sie die **Firma** aus dem Backend (**Kunde** > **Unternehmen**).
1. Überprüfen Sie die E-Mail-Adresse, die Sie für die Registrierung verwendet haben.
1. Legen Sie das **Firmenadministratorkennwort** fest, indem Sie den Anweisungen in der E-Mail folgen.
1. Melden Sie sich mit dem **Firmenadministratorkennwort** am Frontend an.
1. Erstellen Sie einen neuen **Firmenbenutzer** in **Mein Konto** > **Firmenbenutzer** > **Neuen Benutzer hinzufügen**.
1. Wechseln Sie zu &quot;**Stores**&quot;> &quot;**Konfigurationen**&quot;> &quot;**E-Mail-Adressen im allgemeinen Speicher**&quot;> &quot;**Allgemeiner Kontakt**&quot;und aktivieren Sie die Option &quot;**E-Mail-Versand**&quot;.
1. Rufen Sie die E-Mail auf, mit der Sie in Schritt 7 den **neuen Benutzer** registriert haben.

<u>Erwartete Ergebnisse</u>:

Die E-Mail &quot;Sie wurden mit einem Unternehmen verknüpft&quot;wird von einer E-Mail-Adresse mit demselben Wert wie für die **E-Mail-Adresse des Absenders** in Schritt 8 gesendet.

<u>Tatsächliche Ergebnisse</u>:

Die E-Mail &quot;Sie wurden mit einem Unternehmen verknüpft&quot;wird von der E-Mail &quot;**Admin von Unternehmen**&quot;gesendet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
