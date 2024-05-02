---
title: "MDVA-35254: Checkout-CAPTCHA funktioniert nicht ordnungsgemäß"
description: Der Patch MDVA-35254 behebt das Problem, dass CAPTCHA-Felder nach einer nicht erfolgreichen Anzahl von Versuchen, zur Zahlung durch Dritte auszuchecken, nicht angezeigt wurden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 installiert ist. Die Patch-ID lautet MDVA-35254. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.3 behoben wurde.
exl-id: 226c672b-3740-4a87-9ea1-66892acb9fe2
feature: Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# MDVA-35254: Checkout-CAPTCHA funktioniert nicht ordnungsgemäß

Der Patch MDVA-35254 behebt das Problem, dass CAPTCHA-Felder nach einer nicht erfolgreichen Anzahl von Versuchen, zur Zahlung durch Dritte auszuchecken, nicht angezeigt wurden. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 ist installiert. Die Patch-ID lautet MDVA-35254. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce in Cloud-Infrastruktur 2.4.1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.1-2.4.2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Zu reproduzierende Schritte</u>:

CAPTCHA konfigurieren:

1. Installieren und konfigurieren Sie einen Zahlungsdienstleister eines Drittanbieters (Beispiel: Braintree).
1. Navigieren Sie zu **Store > Konfiguration > Kunde > Kundenkonfiguration > CAPTCHA > Forms**.
1. Auswählen **Auschecken/Platzieren der Bestellung**.
1. Behalten Sie die **Anzahl der fehlgeschlagenen Anmeldeversuche** als Standard (Standard = *3*).
1. Melden Sie sich als Kunde an.
1. Fügen Sie beliebige Produkte zum Warenkorb hinzu.
1. Gehen Sie zum Zahlungsabschnitt beim Checkout.
1. Auswählen **Kreditkarte** Zahlungsmethode (Beispiel: Braintree).
1. Machen Sie drei erfolglose Zahlungsversuche.

<u>Erwartete Ergebnisse</u>:

Das CAPTCHA-Feld wird angezeigt, wenn die Anzahl fehlgeschlagener Versuche erreicht ist.

<u>Tatsächliche Ergebnisse</u>:

Das CAPTCHA-Feld wird nie angezeigt, nur die Fehlermeldung: *Geben Sie den CAPTCHA-Code an und versuchen Sie es erneut.*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
