---
title: '"MDVA-42520: Doppelter Steuersatz bei Verwendung von "Grenzüberschreitenden Handel aktivieren"'
description: Der Patch MDVA-42520 behebt das Problem, dass der Steuersatz bei Verwendung der Funktion **Grenzüberschreitenden Handel aktivieren** zweimal angewendet wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 installiert ist. Die Patch-ID lautet MDVA-42520. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: c1ca44eb-fe92-4f28-807a-3a4563433386
feature: Catalog Management, Orders, Taxes
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---

# MDVA-42520: Doppelter Steuersatz bei Verwendung von &quot;Grenzüberschreitenden Handel aktivieren&quot;

Der Patch MDVA-42520 behebt das Problem, dass der Steuersatz zweimal angewendet wird, wenn die Variable **Grenzüberschreitenden Handel aktivieren** verwendet. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 installiert ist. Die Patch-ID lautet MDVA-42520. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Steuersatz wird zweimal angewendet, wenn die Variable **Grenzüberschreitenden Handel aktivieren** verwendet.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren **Firma**, **Freigegebener Katalog**, und **Anführungszeichen**
1. Konfigurieren Sie Steuern entsprechend dem Screenshot. Aktivieren Sie **Grenzüberschreitender Handel**.

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

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
