---
title: Fehlerbehebung für die Storefront-Checkout-Seite im eingeschränkten Modus [!UICONTROL CSP]
description: In diesem Artikel werden Fehler erläutert, die beim Anzeigen der Checkout-Seite im eingeschränkten CSP-Modus auftreten können, und es werden Lösungen zur Behebung dieser Fehler bereitgestellt.
feature: Checkout,Security,Orders,Payments
role: Developer
exl-id: fb92b75d-c88b-4810-a309-d6ab38485e86
source-git-commit: 6d0c4ea9576440d66be3b8053a6e362b8ac0ebcb
workflow-type: tm+mt
source-wordcount: '843'
ht-degree: 0%

---

# Fehlerbehebung für die Storefront-Checkout-Seite im eingeschränkten Modus [!UICONTROL CSP]

In diesem Artikel finden Sie Erklärungen und Fehlerbehebungen zu den Adobe Commerce 2.4.7-Problemen beim Anzeigen der Checkout-Seite in **[!UICONTROL CSP restricted mode]**, wobei die Inline-Skripterstellung &quot;*abgelehnt wurde, da sie gegen die folgende Content Security Policy-Richtlinie verstößt: Fehlermeldung &quot;script-src ...*&quot; im Browser-Konsolenprotokoll.

## Betroffene Produkte und Versionen

Adobe Commerce zur Cloud-Infrastruktur, Adobe Commerce vor Ort und Magento Open Source:

* 2,4,7
* 2.4.6-pX
* 2.4.5-pX
* 2.4.4-pX

## Problem - Die Storefront-Checkout-Seite ist fehlerhaft oder kann nicht geladen werden

Die Seite &quot;**storeFront Checkout**&quot; ist beschädigt oder kann nicht geladen werden, wobei die Fehlermeldung &quot;*Abgelehnt, Inline-Skript auszuführen, da sie gegen die folgende Content Security Policy-Anweisung verstößt: &quot;script-src ...*&quot; im Browser-Konsolenprotokoll.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zur Storefront.
1. Fügen Sie ein Produkt zum Warenkorb hinzu und fahren Sie mit dem Checkout fort.

<u>Erwartete Ergebnisse</u>:

Die Checkout-Seite wird normal vollständig geladen.

<u>Tatsächliche Ergebnisse</u>:

Die Checkout-Seite ist leer oder es fehlen Komponenten. Der folgende [!DNL JS]-Fehler wird im Browser-Konsolenprotokoll angezeigt: &quot;*Weigert, Inline-Skript auszuführen, da er gegen die folgende Content Security Policy-Anweisung verstößt: &quot;script-src ...*&quot;

### Ursache

In Adobe Commerce und Magento Open Source Version 2.4.7 und höher ist **[!UICONTROL CSP]** standardmäßig für Zahlungsseiten in den Storefront- und Admin-Bereichen und im Modus `report-only` für alle anderen Seiten konfiguriert.
`restrict-mode`
Die entsprechende Kopfzeile **[!UICONTROL CSP]** enthält nicht das Schlüsselwort `unsafe-inline` innerhalb der Anweisung `script-src` für Zahlungsseiten. Außerdem sind nur Inline-Skripte vom Typ [!DNL whitelisted] zulässig.

### Lösung

Benutzern werden möglicherweise Browserfehler angezeigt, da bestimmte Skripte aufgrund von **[!UICONTROL CSP]** blockiert wurden:

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u>Um dieses Problem zu beheben, müssen Sie entweder</u>:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) die blockierten Skripte, die die `SecureHtmlRenderer`-Klasse verwenden.
1. Verwenden Sie die Klasse `CSPNonceProvider` , um die Ausführung von Skripten zuzulassen.
Adobe Commerce und Magento Open Source 2.4.7 und höher enthalten einen **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] -Provider, um die Erstellung eindeutiger [!DNL nonce] -Zeichenfolgen für jede Anfrage zu erleichtern. Diese [!DNL nonce] -Zeichenfolgen werden dann an die [!UICONTROL CSP] -Kopfzeile angehängt.

   Verwenden Sie die Funktion `generateNonce` in `Magento\Csp\Helper\CspNonceProvider`, um eine [!DNL nonce] -Zeichenfolge zu erhalten.

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

1. [Fügen Sie der `csp_whitelist.xml` -Datei Ihres Moduls einen  [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) hinzu.

## Problem - Zahlungsmethode fehlt oder funktioniert nicht

Die Zahlungsmethode fehlt oder funktioniert nicht auf der Seite **storeFront Checkout** , wobei die Fehlermeldung &quot;*Abgelehnt, Inline-Skript auszuführen, da sie gegen die folgende Content Security Policy-Anweisung verstößt: &quot;script-src ...*&quot; im Browser-Konsolenprotokoll.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zur Storefront.
2. Fügen Sie ein Produkt zum Warenkorb hinzu und fahren Sie mit dem Checkout fort.
3. Wählen Sie eine Zahlungsmethode aus.

<u>Erwartete Ergebnisse</u>:

Sie können eine Zahlungsmethode auswählen und mit der erfolgreichen Bestellung fortfahren.

<u>Tatsächliche Ergebnisse</u>:

Die Zahlungsmethode fehlt oder funktioniert nicht. Der folgende [!DNL JS]-Fehler wird im Browser-Konsolenprotokoll angezeigt: &quot;*Weigert, Inline-Skript auszuführen, da er gegen die folgende Content Security Policy-Anweisung verstößt: &quot;script-src ...*&quot;

### Ursache

In Adobe Commerce und Magento Open Source Version 2.4.7 und höher ist **[!UICONTROL CSP]** standardmäßig für Zahlungsseiten in den Storefront- und Admin-Bereichen und im Modus `report-only` für alle anderen Seiten konfiguriert.
`restrict-mode`
Die entsprechende Kopfzeile **[!UICONTROL CSP]** enthält nicht das Schlüsselwort `unsafe-inline` innerhalb der Anweisung `script-src` für Zahlungsseiten. Außerdem sind nur Inline-Skripte vom Typ [!DNL whitelisted] zulässig.

### Lösung

Benutzern werden möglicherweise Browserfehler angezeigt, da bestimmte Skripte aufgrund von **[!UICONTROL CSP]** blockiert wurden:

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u>Um dieses Problem zu beheben, müssen Sie entweder</u>:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) die blockierten Skripte, die die `SecureHtmlRenderer`-Klasse verwenden.
1. Verwenden Sie die Klasse `CSPNonceProvider` , um die Ausführung von Skripten zuzulassen.
Adobe Commerce und Magento Open Source 2.4.7 und höher enthalten einen **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] -Provider, um die Erstellung eindeutiger [!DNL nonce] -Zeichenfolgen für jede Anfrage zu erleichtern. Diese [!DNL nonce] -Zeichenfolgen werden dann an die [!UICONTROL CSP] -Kopfzeile angehängt.

   Verwenden Sie die Funktion `generateNonce` in `Magento\Csp\Helper\CspNonceProvider`, um eine [!DNL nonce] -Zeichenfolge zu erhalten.

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

1. [Fügen Sie der `csp_whitelist.xml` -Datei Ihres Moduls einen  [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) hinzu.

## Problem - Der Kunde kann keine Bestellung aufgeben

Ein Kunde kann keine Bestellung aufgeben, mit dem &quot;*Verweigert, Inline-Skript auszuführen, da es gegen die folgende Content Security Policy-Richtlinie verstößt: Fehlermeldung &quot;script-src ...*&quot; im Browser-Konsolenprotokoll.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zur Storefront.
2. Fügen Sie ein Produkt zum Warenkorb hinzu und fahren Sie mit dem Checkout fort.
3. Wählen Sie eine Zahlungsmethode aus.
4. Klicken Sie auf **Bestellung platzieren**.

<u>Erwartete Ergebnisse</u>:

Sie können erfolgreich eine Bestellung aufgeben.

<u>Tatsächliche Ergebnisse</u>:

Sie können keine Bestellung aufgeben. Der folgende [!DNL JS]-Fehler wird im Browser-Konsolenprotokoll angezeigt: &quot;*Weigert, Inline-Skript auszuführen, da er gegen die folgende Content Security Policy-Anweisung verstößt: &quot;script-src ...*&quot;

### Ursache

In Adobe Commerce und Magento Open Source Version 2.4.7 und höher ist **[!UICONTROL CSP]** standardmäßig für Zahlungsseiten in den Storefront- und Admin-Bereichen und im Modus `report-only` für alle anderen Seiten konfiguriert.
`restrict-mode`
Die entsprechende Kopfzeile **[!UICONTROL CSP]** enthält nicht das Schlüsselwort `unsafe-inline` innerhalb der Anweisung `script-src` für Zahlungsseiten. Außerdem sind nur Inline-Skripte vom Typ [!DNL whitelisted] zulässig.

### Lösung

Benutzern werden möglicherweise Browserfehler angezeigt, da bestimmte Skripte aufgrund von **[!UICONTROL CSP]** blockiert wurden:

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u>Um dieses Problem zu beheben, müssen Sie entweder</u>:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) die blockierten Skripte, die die `SecureHtmlRenderer`-Klasse verwenden.
1. Verwenden Sie die Klasse `CSPNonceProvider` , um die Ausführung von Skripten zuzulassen.
Adobe Commerce und Magento Open Source 2.4.7 und höher enthalten einen **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] -Provider, um die Erstellung eindeutiger [!DNL nonce] -Zeichenfolgen für jede Anfrage zu erleichtern. Diese [!DNL nonce] -Zeichenfolgen werden dann an die [!UICONTROL CSP] -Kopfzeile angehängt.

   Verwenden Sie die Funktion `generateNonce` in `Magento\Csp\Helper\CspNonceProvider`, um eine [!DNL nonce] -Zeichenfolge zu erhalten.

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

1. [Fügen Sie der `csp_whitelist.xml` -Datei Ihres Moduls einen  [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) hinzu.
