---
title: Fehlerbehebung für die Storefront-Checkout-Seite [!UICONTROL CSP] eingeschränkten Modus
description: In diesem Artikel werden Fehler erläutert, die beim Anzeigen der Checkout-Seite im eingeschränkten CSP-Modus auftreten können, und Lösungen bereitgestellt, um diese Fehler zu beheben.
feature: Checkout,Security,Orders,Payments
role: Developer
exl-id: fb92b75d-c88b-4810-a309-d6ab38485e86
source-git-commit: 6d0c4ea9576440d66be3b8053a6e362b8ac0ebcb
workflow-type: tm+mt
source-wordcount: '843'
ht-degree: 0%

---

# Fehlerbehebung für die Storefront-Checkout-Seite [!UICONTROL CSP] eingeschränkten Modus

Dieser Artikel enthält Erläuterungen und Fehlerbehebungen für Probleme mit Adobe Commerce 2.4.7 beim Anzeigen der Kaufbestätigungsseite in **[!UICONTROL CSP restricted mode]** mit der Fehlermeldung &quot;*Ausführung des Inline-Skripts abgelehnt, da es gegen die folgende Content Security Policy-Direktive verstößt: „script-src …*&quot; im Protokoll der Browser-Konsole.

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur, Adobe Commerce On-Premise und Magento Open Source:

* 2,4,7
* 2.4.6-pX
* 2,4,5-pX
* 2.4.4-pX

## Problem - Storefront-Checkout-Seite ist fehlerhaft oder kann nicht geladen werden

Die **Storefront Checkout**-Seite ist fehlerhaft oder kann nicht geladen werden, mit dem Fehlerhinweis &quot;*Ausführung des Inline-Skripts wurde abgelehnt, da es gegen die folgende Content Security Policy-Anweisung verstößt: Fehlermeldung „script-src …*&quot; im Protokoll der Browser-Konsole.

<u>Schritte zur Reproduktion</u>:

1. Geh zum Laden.
1. Fügen Sie ein Produkt zum Warenkorb hinzu und fahren Sie mit der Kasse fort.

<u>Erwartete Ergebnisse</u>:

Die Checkout-Seite wird vollständig normal geladen.

<u>Tatsächliche Ergebnisse</u>:

Die Checkout-Seite ist leer oder es fehlen Komponenten. Der folgende [!DNL JS] wird im Protokoll der Browser-Konsole angezeigt: &quot;*Die Ausführung des Inline-Skripts wurde abgelehnt, da es die folgende Content Security Policy-Anweisung verletzt: „script-src …*&quot;

### Ursache

In Adobe Commerce und Magento Open Source ab Version 2.4.7 ist **[!UICONTROL CSP]** standardmäßig in `restrict-mode` für Zahlungsseiten in den Bereichen Storefront und Admin und im `report-only` für alle anderen Seiten konfiguriert.
Der entsprechende **[!UICONTROL CSP]**-Header enthält nicht das `unsafe-inline` Schlüsselwort in der `script-src`-Direktive für Zahlungsseiten. Außerdem sind nur [!DNL whitelisted] Inline-Skripte zulässig.

### Lösung

Benutzer sehen möglicherweise Browser-Fehler, da bestimmte Skripte aufgrund von **[!UICONTROL CSP]** blockiert werden:

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u>Um dieses Problem zu beheben, müssen Sie entweder</u>:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) der blockierten Skripte mithilfe der `SecureHtmlRenderer`-Klasse
1. Verwenden Sie die `CSPNonceProvider`-Klasse, um die Ausführung von Skripten zu ermöglichen.
Adobe Commerce und Magento Open Source 2.4.7 und höher enthalten einen **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce], um die Erstellung eindeutiger [!DNL nonce] für jede Anfrage zu erleichtern. Diese [!DNL nonce] werden dann an den [!UICONTROL CSP]-Header angehängt.

   Verwenden Sie die `generateNonce` Funktion in `Magento\Csp\Helper\CspNonceProvider`, um eine [!DNL nonce] Zeichenfolge abzurufen.

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

1. [Fügen Sie  [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) zur `csp_whitelist.xml`-Datei Ihres Moduls hinzu.

## Problem - Zahlungsmethode fehlt oder funktioniert nicht

Die Zahlungsmethode fehlt oder funktioniert nicht auf der Seite **Storefront Checkout** mit der Fehlermeldung &quot;*Ausführung des Inline-Skripts wurde abgelehnt, da es gegen die folgende Content Security Policy-Direktive verstößt: „script-src …*&quot; im Protokoll der Browser-Konsole.

<u>Schritte zur Reproduktion</u>:

1. Geh zum Laden.
2. Fügen Sie ein Produkt zum Warenkorb hinzu und fahren Sie mit der Kasse fort.
3. Wählen Sie eine Zahlungsmethode aus.

<u>Erwartete Ergebnisse</u>:

Sie können eine Zahlungsmethode auswählen und mit der erfolgreichen Bestellung fortfahren.

<u>Tatsächliche Ergebnisse</u>:

Die Zahlungsmethode fehlt oder funktioniert nicht. Der folgende [!DNL JS] wird im Protokoll der Browser-Konsole angezeigt: &quot;*Die Ausführung des Inline-Skripts wurde abgelehnt, da es die folgende Content Security Policy-Anweisung verletzt: „script-src …*&quot;

### Ursache

In Adobe Commerce und Magento Open Source ab Version 2.4.7 ist **[!UICONTROL CSP]** standardmäßig in `restrict-mode` für Zahlungsseiten in den Bereichen Storefront und Admin und im `report-only` für alle anderen Seiten konfiguriert.
Der entsprechende **[!UICONTROL CSP]**-Header enthält nicht das `unsafe-inline` Schlüsselwort in der `script-src`-Direktive für Zahlungsseiten. Außerdem sind nur [!DNL whitelisted] Inline-Skripte zulässig.

### Lösung

Benutzer sehen möglicherweise Browser-Fehler, da bestimmte Skripte aufgrund von **[!UICONTROL CSP]** blockiert werden:

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u>Um dieses Problem zu beheben, müssen Sie entweder</u>:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) der blockierten Skripte mithilfe der `SecureHtmlRenderer`-Klasse
1. Verwenden Sie die `CSPNonceProvider`-Klasse, um die Ausführung von Skripten zu ermöglichen.
Adobe Commerce und Magento Open Source 2.4.7 und höher enthalten einen **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce], um die Erstellung eindeutiger [!DNL nonce] für jede Anfrage zu erleichtern. Diese [!DNL nonce] werden dann an den [!UICONTROL CSP]-Header angehängt.

   Verwenden Sie die `generateNonce` Funktion in `Magento\Csp\Helper\CspNonceProvider`, um eine [!DNL nonce] Zeichenfolge abzurufen.

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

1. [Fügen Sie  [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) zur `csp_whitelist.xml`-Datei Ihres Moduls hinzu.

## Problem - Kunde kann keine Bestellung aufgeben

Eine Kundin oder ein Kunde kann keine Bestellung aufgeben, wobei das Skript &quot;*Ausführung des Inline-Skripts abgelehnt, da es die folgende Content Security Policy-Direktive verletzt: Fehlermeldung „script-src …*&quot; im Protokoll der Browser-Konsole.

<u>Schritte zur Reproduktion</u>:

1. Geh zum Laden.
2. Fügen Sie ein Produkt zum Warenkorb hinzu und fahren Sie mit der Kasse fort.
3. Wählen Sie eine Zahlungsmethode aus.
4. Klicken Sie **Bestellung aufgeben**.

<u>Erwartete Ergebnisse</u>:

Sie können eine Bestellung erfolgreich aufgeben.

<u>Tatsächliche Ergebnisse</u>:

Sie können keine Bestellung aufgeben. Der folgende [!DNL JS] wird im Protokoll der Browser-Konsole angezeigt: &quot;*Die Ausführung des Inline-Skripts wurde abgelehnt, da es die folgende Content Security Policy-Anweisung verletzt: „script-src …*&quot;

### Ursache

In Adobe Commerce und Magento Open Source ab Version 2.4.7 ist **[!UICONTROL CSP]** standardmäßig in `restrict-mode` für Zahlungsseiten in den Bereichen Storefront und Admin und im `report-only` für alle anderen Seiten konfiguriert.
Der entsprechende **[!UICONTROL CSP]**-Header enthält nicht das `unsafe-inline` Schlüsselwort in der `script-src`-Direktive für Zahlungsseiten. Außerdem sind nur [!DNL whitelisted] Inline-Skripte zulässig.

### Lösung

Benutzer sehen möglicherweise Browser-Fehler, da bestimmte Skripte aufgrund von **[!UICONTROL CSP]** blockiert werden:

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u>Um dieses Problem zu beheben, müssen Sie entweder</u>:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) der blockierten Skripte mithilfe der `SecureHtmlRenderer`-Klasse
1. Verwenden Sie die `CSPNonceProvider`-Klasse, um die Ausführung von Skripten zu ermöglichen.
Adobe Commerce und Magento Open Source 2.4.7 und höher enthalten einen **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce], um die Erstellung eindeutiger [!DNL nonce] für jede Anfrage zu erleichtern. Diese [!DNL nonce] werden dann an den [!UICONTROL CSP]-Header angehängt.

   Verwenden Sie die `generateNonce` Funktion in `Magento\Csp\Helper\CspNonceProvider`, um eine [!DNL nonce] Zeichenfolge abzurufen.

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

1. [Fügen Sie  [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) zur `csp_whitelist.xml`-Datei Ihres Moduls hinzu.
