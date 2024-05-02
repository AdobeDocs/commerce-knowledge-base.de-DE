---
title: Adobe Commerce 2.3.6, 2.4.1 CAPTCHA im Checkout funktioniert nicht
description: Dieser Artikel enthält einen Patch für das Problem, dass die CAPTCHA-Funktion für den Checkout nicht wie erwartet auf der Bestellseite funktioniert, wenn Sie Zahlungsdienstleister von Drittanbietern wie Paypal Express, Payflow Pro oder CyberSource in Adobe Commerce verwenden.
exl-id: 46ab7f4d-ee0a-4cc1-96cc-6eb408319e9c
feature: Checkout, Orders
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---

# Adobe Commerce 2.3.6, 2.4.1 CAPTCHA im Checkout funktioniert nicht

Dieser Artikel enthält einen Patch für das Problem, dass die CAPTCHA-Funktion für den Checkout nicht wie erwartet auf der Bestellseite funktioniert, wenn Sie Zahlungsdienstleister von Drittanbietern wie Paypal Express, Payflow Pro oder CyberSource in Adobe Commerce verwenden.

Dieses bekannte Problem wird in unserer Entwicklerdokumentation erwähnt:

<u>Für Adobe Commerce 2.3.6</u>:

* [Versionshinweise zu Adobe Commerce 2.3.6: Bekannte Probleme](https://devdocs.magento.com/guides/v2.3/release-notes/commerce-2-3-6.html#known-issues)
* [Versionshinweise zu Magento Open Source 2.3.6: Bekannte Probleme](https://devdocs.magento.com/guides/v2.3/release-notes/open-source-2-3-6.html#known-issues)

<u>Für Adobe Commerce 2.4.1</u>:

* [Adobe Commerce 2.4.1 - Versionshinweise: Bekannte Probleme](https://devdocs.magento.com/guides/v2.4/release-notes/commerce-2-4-1.html#known-issues)
* [Magento Open Source 2.4.1 - Versionshinweise: Bekannte Probleme](https://devdocs.magento.com/guides/v2.4/release-notes/open-source-2-4-1.html#known-issues)

## Betroffene Produkte und Versionen

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.6 und 2.4.1
* Magento Open Source 2.3.6 und 2.4.1

## Problem

<u>Zu reproduzierende Schritte</u>

1. Richten Sie mindestens eine dieser Zahlungsmethoden in Commerce ein: Paypal Express, Payflow Pro oder CyberSource.
1. Navigieren Sie zu **Admin > Stores > Konfiguration > Kunden > Kundenkonfiguration > CAPTCHA** .
   * Satz **CAPTCHA in Storefront aktivieren** = *Ja* .
   * Wählen Sie in **Forms** : *Auschecken/Platzieren der Bestellung* , *Anmelden* , und *Kennwort vergessen* .
   * Satz **Anzeigemodus** = *Nach mehreren Anmeldeversuchen* (um **Anzahl der fehlgeschlagenen Anmeldeversuche** angezeigt).
   * Satz **Anzahl der fehlgeschlagenen Anmeldeversuche** = *0* (damit Captcha immer funktioniert).
1. Fügen Sie am Frontend ein Produkt zum Warenkorb hinzu und versuchen Sie, auszuchecken.
1. Geben Sie auf der Seite mit den Zahlungsinformationen Captcha ein und versuchen Sie, mit Paypal Express, Payflow Pro oder CyberSource auszuchecken.

<u>Erwartetes Ergebnis:</u>

Die CAPTCHA-Funktion funktioniert wie erwartet.

<u>Ergebnis:</u>

Die Fehlermeldung wird angezeigt: *Geben Sie den CAPTCHA-Code an und versuchen Sie es erneut.*

## Lösung

Wenden Sie einen der folgenden Patches an, je nachdem, ob Sie sich auf Adobe Commerce On-Premise/Adobe Commerce in der Cloud-Infrastruktur/Magento Open Source 2.3.6 oder 2.4.1 befinden.

## Patches

Die Patches sind an diesen Artikel angehängt und können in beiden `.composer` und `.git` -Formaten.

Um einen Patch herunterzuladen, scrollen Sie nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf einen der folgenden Links:

<u>Für Adobe Commerce On-Premise/Adobe Commerce über Cloud-Infrastruktur/Magento Open Source 2.3.6</u> :

* [Composer Patch MDVA-33093\_\_\_\_2\_3\_x-p1\_\_CAPTCHA\_COMPOSER.patch](assets/MDVA-33093____2_3_x-p1__CAPTCHA_COMPOSER.patch.zip)
* [Git Patch MDVA-33093\_\_\_\_2\_3\_x-p1\_\_CAPTCHA\_GIT.patch](assets/MDVA-33093____2_3_x-p1__CAPTCHA_GIT.patch.zip)

<u>Für Adobe Commerce On-Premise/Adobe Commerce über Cloud-Infrastruktur/Magento Open Source 2.4.1</u> :

* [Composer Patch MDVA-33093\_\_\_\_2\_4\_x-p1\_\_CAPTCHA\_COMPOSER.patch](assets/MDVA-33093____2_4_x-p1__CAPTCHA_COMPOSER.patch.zip)
* [Git Patch MDVA-33093\_\_\_\_2\_4\_x-p1\_\_CAPTCHA\_GIT.patch](assets/MDVA-33093____2_4_x-p1__CAPTCHA_GIT.patch.zip)

Diese Patches sind nicht mit anderen Adobe Commerce- oder Magento Open Source-Versionen und -Editionen kompatibel.

## Anwenden des Pflasters

<u>Composer-Patch</u>

Siehe [Anwenden eines von Adobe bereitgestellten Composer-Patches](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in unserer Support-Wissensdatenbank für Composer Patch-Anweisungen.

<u>Git Patch</u>

Siehe Entwicklerdokumentation [Anwenden von Patches: Benutzerdefinierte Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#custom-patches) für Git-Patch-Anweisungen für Adobe Commerce/Magento Open Source.
