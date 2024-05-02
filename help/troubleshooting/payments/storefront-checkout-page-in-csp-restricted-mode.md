---
title: Fehlerbehebung für die Storefront-Checkout-Seite in [!UICONTROL CSP] eingeschränkter Modus
description: In diesem Artikel werden Fehler erläutert, die beim Anzeigen der Checkout-Seite im eingeschränkten CSP-Modus auftreten können, und es werden Lösungen zur Behebung dieser Fehler bereitgestellt.
feature: Checkout,Security,Orders,Payments
role: Developer
exl-id: fb92b75d-c88b-4810-a309-d6ab38485e86
source-git-commit: 6d0c4ea9576440d66be3b8053a6e362b8ac0ebcb
workflow-type: tm+mt
source-wordcount: '843'
ht-degree: 0%

---

# Fehlerbehebung für die Storefront-Checkout-Seite in [!UICONTROL CSP] eingeschränkter Modus

Dieser Artikel enthält Erklärungen und Fehlerbehebungen für die Probleme in Adobe Commerce 2.4.7 beim Anzeigen der Checkout-Seite in **[!UICONTROL CSP restricted mode]** mit &quot;*Weigert, Inline-Skript auszuführen, weil es die folgende Content Security Policy-Anweisung verletzt: &quot;script-src ...*&quot; Fehlermeldung im Browser-Konsolenprotokoll.

## Betroffene Produkte und Versionen

Adobe Commerce zur Cloud-Infrastruktur, Adobe Commerce vor Ort und Magento Open Source:

* 2,4,7
* 2.4.6-pX
* 2.4.5-pX
* 2.4.4-pX

## Problem - Die Storefront-Checkout-Seite ist fehlerhaft oder kann nicht geladen werden

Die **Storefront-Checkout** -Seite beschädigt ist oder nicht geladen werden kann, mit dem *Weigert, Inline-Skript auszuführen, weil es die folgende Content Security Policy-Anweisung verletzt: &quot;script-src ...*&quot; Fehlermeldung im Browser-Konsolenprotokoll.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zur Storefront.
1. Fügen Sie ein Produkt zum Warenkorb hinzu und fahren Sie mit dem Checkout fort.

<u>Erwartete Ergebnisse</u>:

Die Checkout-Seite wird normal vollständig geladen.

<u>Tatsächliche Ergebnisse</u>:

Die Checkout-Seite ist leer oder es fehlen Komponenten. Die folgenden [!DNL JS] im Protokoll der Browserkonsole wird ein Fehler angezeigt: &quot;*Weigert, Inline-Skript auszuführen, weil es die folgende Content Security Policy-Anweisung verletzt: &quot;script-src ...*&quot;

### Ursache

In Adobe Commerce und Magento Open Source Version 2.4.7 und höher **[!UICONTROL CSP]** konfiguriert in `restrict-mode`, standardmäßig für Zahlungsseiten in den Storefront- und Admin-Bereichen und in `report-only` -Modus für alle anderen Seiten.
Die entsprechende **[!UICONTROL CSP]** -Kopfzeile enthält nicht die `unsafe-inline` Suchbegriff in `script-src` -Anweisung für Zahlungsseiten. Nur [!DNL whitelisted] Inline-Skripte sind zulässig.

### Lösung

Benutzern werden möglicherweise Browserfehler angezeigt, da bestimmte Skripte aufgrund von **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u>Um dieses Problem zu beheben, müssen Sie</u>:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) die blockierten Skripte mithilfe der `SecureHtmlRenderer` -Klasse.
1. Verwenden Sie die `CSPNonceProvider` -Klasse, um die Ausführung von Skripten zu ermöglichen.
Adobe Commerce und Magento Open Source 2.4.7 und höher enthalten eine **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] Anbieter zur Erleichterung der Erstellung von [!DNL nonce] -Zeichenfolgen für jede Anfrage. Diese [!DNL nonce] -Zeichenfolgen dann an die [!UICONTROL CSP] -Kopfzeile.

   Verwenden Sie die `generateNonce` -Funktion in `Magento\Csp\Helper\CspNonceProvider` um [!DNL nonce] Zeichenfolge.

   ```php
   use Magento\Csp\Helper\CspNonceProvider;
   
   class MyClass
   {
   
       /**
        * @var CspNonceProvider
        */
       private $cspNonceProvider;
   
       /**
        * @param CspNonceProvider $cspNonceProvider
        */
       public function __construct(CspNonceProvider $cspNonceProvider)
       {
           $this->cspNonceProvider = $cspNonceProvider
       }
   
       /**
        * Get CSP Nonce
        *
        * @return String
        */
       public function getNonce(): string
       {
           return $this->cspNonceProvider->generateNonce();
       }
   }
   ```

1. [Hinzufügen einer [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) auf die `csp_whitelist.xml` -Datei.

## Problem - Zahlungsmethode fehlt oder funktioniert nicht

Die Zahlungsmethode fehlt oder arbeitet nicht an der **Storefront-Checkout** mit dem Zeichen &quot;*Weigert, Inline-Skript auszuführen, weil es die folgende Content Security Policy-Anweisung verletzt: &quot;script-src ...*&quot; Fehlermeldung im Browser-Konsolenprotokoll.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zur Storefront.
2. Fügen Sie ein Produkt zum Warenkorb hinzu und fahren Sie mit dem Checkout fort.
3. Wählen Sie eine Zahlungsmethode aus.

<u>Erwartete Ergebnisse</u>:

Sie können eine Zahlungsmethode auswählen und mit der erfolgreichen Bestellung fortfahren.

<u>Tatsächliche Ergebnisse</u>:

Die Zahlungsmethode fehlt oder funktioniert nicht. Die folgenden [!DNL JS] im Protokoll der Browserkonsole wird ein Fehler angezeigt: &quot;*Weigert, Inline-Skript auszuführen, weil es die folgende Content Security Policy-Anweisung verletzt: &quot;script-src ...*&quot;

### Ursache

In Adobe Commerce und Magento Open Source Version 2.4.7 und höher **[!UICONTROL CSP]** konfiguriert in `restrict-mode`, standardmäßig für Zahlungsseiten in den Storefront- und Admin-Bereichen und in `report-only` -Modus für alle anderen Seiten.
Die entsprechende **[!UICONTROL CSP]** -Kopfzeile enthält nicht die `unsafe-inline` Suchbegriff in `script-src` -Anweisung für Zahlungsseiten. Nur [!DNL whitelisted] Inline-Skripte sind zulässig.

### Lösung

Benutzern werden möglicherweise Browserfehler angezeigt, da bestimmte Skripte aufgrund von **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u>Um dieses Problem zu beheben, müssen Sie</u>:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) die blockierten Skripte mithilfe der `SecureHtmlRenderer` -Klasse.
1. Verwenden Sie die `CSPNonceProvider` -Klasse, um die Ausführung von Skripten zu ermöglichen.
Adobe Commerce und Magento Open Source 2.4.7 und höher enthalten eine **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] Anbieter zur Erleichterung der Erstellung von [!DNL nonce] -Zeichenfolgen für jede Anfrage. Diese [!DNL nonce] -Zeichenfolgen dann an die [!UICONTROL CSP] -Kopfzeile.

   Verwenden Sie die `generateNonce` -Funktion in `Magento\Csp\Helper\CspNonceProvider` um [!DNL nonce] Zeichenfolge.

   ```php
   use Magento\Csp\Helper\CspNonceProvider;
   
   class MyClass
   {
   
       /**
        * @var CspNonceProvider
        */
       private $cspNonceProvider;
   
       /**
        * @param CspNonceProvider $cspNonceProvider
        */
       public function __construct(CspNonceProvider $cspNonceProvider)
       {
           $this->cspNonceProvider = $cspNonceProvider
       }
   
       /**
        * Get CSP Nonce
        *
        * @return String
        */
       public function getNonce(): string
       {
           return $this->cspNonceProvider->generateNonce();
       }
   }
   ```

1. [Hinzufügen einer [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) auf die `csp_whitelist.xml` -Datei.

## Problem - Der Kunde kann keine Bestellung aufgeben

Ein Kunde kann keine Bestellung mit dem *Weigert, Inline-Skript auszuführen, weil es die folgende Content Security Policy-Anweisung verletzt: &quot;script-src ...*&quot; Fehlermeldung im Browser-Konsolenprotokoll.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zur Storefront.
2. Fügen Sie ein Produkt zum Warenkorb hinzu und fahren Sie mit dem Checkout fort.
3. Wählen Sie eine Zahlungsmethode aus.
4. Klicks **Bestellung platzieren**.

<u>Erwartete Ergebnisse</u>:

Sie können erfolgreich eine Bestellung aufgeben.

<u>Tatsächliche Ergebnisse</u>:

Sie können keine Bestellung aufgeben. Die folgenden [!DNL JS] im Protokoll der Browserkonsole wird ein Fehler angezeigt: &quot;*Weigert, Inline-Skript auszuführen, weil es die folgende Content Security Policy-Anweisung verletzt: &quot;script-src ...*&quot;

### Ursache

In Adobe Commerce und Magento Open Source Version 2.4.7 und höher **[!UICONTROL CSP]** konfiguriert in `restrict-mode`, standardmäßig für Zahlungsseiten in den Storefront- und Admin-Bereichen und in `report-only` -Modus für alle anderen Seiten.
Die entsprechende **[!UICONTROL CSP]** -Kopfzeile enthält nicht die `unsafe-inline` Suchbegriff in `script-src` -Anweisung für Zahlungsseiten. Nur [!DNL whitelisted] Inline-Skripte sind zulässig.

### Lösung

Benutzern werden möglicherweise Browserfehler angezeigt, da bestimmte Skripte aufgrund von **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u>Um dieses Problem zu beheben, müssen Sie</u>:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) die blockierten Skripte mithilfe der `SecureHtmlRenderer` -Klasse.
1. Verwenden Sie die `CSPNonceProvider` -Klasse, um die Ausführung von Skripten zu ermöglichen.
Adobe Commerce und Magento Open Source 2.4.7 und höher enthalten eine **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] Anbieter zur Erleichterung der Erstellung von [!DNL nonce] -Zeichenfolgen für jede Anfrage. Diese [!DNL nonce] -Zeichenfolgen dann an die [!UICONTROL CSP] -Kopfzeile.

   Verwenden Sie die `generateNonce` -Funktion in `Magento\Csp\Helper\CspNonceProvider` um [!DNL nonce] Zeichenfolge.

   ```php
   use Magento\Csp\Helper\CspNonceProvider;
   
   class MyClass
   {
   
       /**
        * @var CspNonceProvider
        */
       private $cspNonceProvider;
   
       /**
        * @param CspNonceProvider $cspNonceProvider
        */
       public function __construct(CspNonceProvider $cspNonceProvider)
       {
           $this->cspNonceProvider = $cspNonceProvider
       }
   
       /**
        * Get CSP Nonce
        *
        * @return String
        */
       public function getNonce(): string
       {
           return $this->cspNonceProvider->generateNonce();
       }
   }
   ```

1. [Hinzufügen einer [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) auf die `csp_whitelist.xml` -Datei.
