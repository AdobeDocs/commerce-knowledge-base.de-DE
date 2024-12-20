---
title: 'MDVA-42520: Doppelter Steuersatz bei Verwendung von "Grenzüberschreitenden Handel aktivieren"'
description: Der Patch MDVA-42520 behebt das Problem, dass der Steuersatz bei Verwendung der Funktion **Grenzüberschreitenden Handel aktivieren** zweimal angewendet wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 installiert ist. Die Patch-ID lautet MDVA-42520. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: c1ca44eb-fe92-4f28-807a-3a4563433386
feature: Catalog Management, Orders, Taxes
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---

# MDVA-42520: Doppelter Steuersatz bei Verwendung von &quot;Grenzüberschreitenden Handel aktivieren&quot;

Der Patch MDVA-42520 behebt das Problem, dass der Steuersatz bei Verwendung von **Grenzüberschreitenden Handel aktivieren** zweimal angewendet wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 installiert ist. Die Patch-ID lautet MDVA-42520. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Steuersatz wird zweimal angewendet, wenn **Grenzüberschreitenden Handel aktivieren** verwendet wird.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie **Firma**, **freigegebener Katalog** und **Zitat**
1. Konfigurieren Sie Steuern entsprechend dem Screenshot. Stellen Sie sicher, dass Sie **Grenzüberschreitender Handel** aktivieren.

   ![Steuereinstellungen](/help/support-tools/patches-available-in-qpt-tool/assets/tax_settings_1.png){width="700"}

1. Erstellen Sie einen Steuersatz für Deutschland (10%).
1. Erstellen Sie eine Steuerregel zur Anwendung des Steuersatzes.
1. Erstellen Sie ein Unternehmen und einen benutzerdefinierten freigegebenen Katalog.
1. Erstellen Sie ein Produkt mit einem Preis von 100 und fügen Sie es in den benutzerdefinierten freigegebenen Katalog mit einem Preisnachlass von 20 % ein.
1. Erstellen Sie einen Kunden mit einer deutschen Adresse und weisen Sie ihn dem Unternehmen zu
1. Fügen Sie der Karte als Kunde 10 Produkte hinzu.
1. Gehen Sie zum Warenkorb und fordern Sie ein Angebot an.
1. Öffnen Sie dieses Anführungszeichen im Backend und versuchen Sie, einen zusätzlichen 10-%-Rabatt hinzuzufügen.

<u>Erwartete Ergebnisse</u>:

Anführungszeichen Zwischensumme (einschließlich Steuern) und Anführungsgesamtsumme (einschließlich Steuern) = 720 USD

<u>Tatsächliche Ergebnisse</u>:

Anführungszeichen: Zwischensumme (einschließlich Steuern) und Anführungsgesamtsumme (einschließlich Steuern) = 649,50 USD.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) verfügbar sind, in unserer Entwicklerdokumentation.
