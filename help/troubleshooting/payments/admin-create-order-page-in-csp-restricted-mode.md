---
title: Fehlerbehebung bei der Erstellung einer Auftragsseite im eingeschränkten [!UICONTROL CSP]
description: In diesem Artikel werden Fehler bei der Erstellung einer Bestellung auf der Admin-Seite erläutert, wenn der eingeschränkte CSP-Modus aktiviert ist, und Lösungen bereitgestellt, um diese Fehler zu beheben.
feature: Checkout,Security,Orders,Payments
role: Developer
exl-id: c1a0886a-df1f-418a-9e4d-562b28a0d8b3
source-git-commit: 6d0c4ea9576440d66be3b8053a6e362b8ac0ebcb
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%

---

# Fehlerbehebung bei der Erstellung einer Auftragsseite im eingeschränkten [!UICONTROL CSP]

In diesem Artikel finden Sie Erläuterungen und Fehlerbehebungen für Adobe Commerce 2.4.7-Probleme beim Erstellen einer Bestellung auf der Admin-Seite mit **[!UICONTROL CSP restricted mode]** ist *Aktiviert* mit der Fehlermeldung &quot;*Ausführung des Inline-Skripts wurde abgelehnt, da es gegen die folgende Content Security Policy-Anweisung verstößt: „script-src …*&quot; im Protokoll der Browser-Konsole.

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur, Adobe Commerce On-Premise und Magento Open Source:

* 2,4,7
* 2.4.6-pX
* 2,4,5-pX
* 2.4.4-pX

## Problem - Admin **Bestellung erstellen** Seite ist fehlerhaft oder kann nicht geladen werden

Die Admin **Seite „Bestellung erstellen** ist fehlerhaft oder kann nicht geladen werden, mit der Fehlermeldung &quot;*Ausführung des Inline-Skripts wurde abgelehnt, da es gegen die folgende Content Security Policy-Anweisung verstößt: „script-src …*&quot; im Protokoll der Browser-Konsole.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Erstellen Sie eine neue Bestellung.

<u>Erwartete Ergebnisse</u>:

Die Admin **Seite „Bestellung erstellen** wird vollständig normal geladen.

<u>Tatsächliche Ergebnisse</u>:

Die Admin **Seite „Auftrag erstellen** ist leer oder es fehlen Komponenten. Der folgende [!DNL JS] wird im Protokoll der Browser-Konsole angezeigt: &quot;*Die Ausführung des Inline-Skripts wurde abgelehnt, da es die folgende Content Security Policy-Anweisung verletzt: „script-src …*&quot;

### Ursache

In Adobe Commerce und Magento Open Source ab Version 2.4.7 ist **[!UICONTROL CSP]** standardmäßig in `restrict-mode` für Zahlungsseiten in den Bereichen Storefront und Admin und im `report-only` für alle anderen Seiten konfiguriert.
Der entsprechende **[!UICONTROL CSP]**-Header enthält nicht das `unsafe-inline` Schlüsselwort in der `script-src`-Direktive für Zahlungsseiten. Außerdem sind nur [!DNL whitelisted] Inline-Skripte zulässig.

### Lösung

Benutzer sehen möglicherweise Browser-Fehler, da bestimmte Skripte aufgrund von [!UICONTROL CSP] blockiert werden:

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

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

Die Zahlungsmethode fehlt oder funktioniert nicht auf der Admin-Seite **Bestellerstellung** mit der Fehlermeldung &quot;*Ausführung des Inline-Skripts wurde abgelehnt, da es gegen die folgende Content Security Policy-Direktive verstößt: „script-src …*&quot; im Protokoll der Browser-Konsole.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Erstellen Sie eine neue Bestellung.
1. Neuen Kunden erstellen.
1. Geben Sie die Kundendetails ein.
1. Geben Sie die Bestelldetails (Produkte, Versandart) ein.
1. Wählen Sie eine Zahlungsmethode aus.

<u>Erwartete Ergebnisse</u>:

Sie können eine Zahlungsmethode auswählen und mit der erfolgreichen Bestellung fortfahren.

<u>Tatsächliche Ergebnisse</u>:

Die Zahlungsmethode fehlt oder funktioniert nicht. Der folgende [!DNL JS] wird im Protokoll der Browser-Konsole angezeigt: &quot;*Die Ausführung des Inline-Skripts wurde abgelehnt, da es die folgende Content Security Policy-Anweisung verletzt: „script-src …*&quot;.

### Ursache

In Adobe Commerce und Magento Open Source ab Version 2.4.7 ist **[!UICONTROL CSP]** standardmäßig in `restrict-mode` für Zahlungsseiten in den Bereichen Storefront und Admin und im `report-only` für alle anderen Seiten konfiguriert.
Der entsprechende **[!UICONTROL CSP]**-Header enthält nicht das `unsafe-inline` Schlüsselwort in der `script-src`-Direktive für Zahlungsseiten. Außerdem sind nur [!DNL whitelisted] Inline-Skripte zulässig.

### Lösung

Benutzer sehen möglicherweise Browser-Fehler, da bestimmte Skripte aufgrund von **[!UICONTROL CSP]** blockiert werden:

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

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

## Problem - Der Administrator kann keine Bestellung aufgeben

Ein Administrator kann keine Bestellung auf der Admin-Seite **Bestellung erstellen** mit der Fehlermeldung &quot;*Ausführung des Inline-Skripts wurde abgelehnt, da es gegen die folgende Content Security Policy-Direktive verstößt: „script-src …*&quot; im Protokoll der Browser-Konsole.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Erstellen Sie eine neue Bestellung.
1. Neuen Kunden erstellen.
1. Geben Sie die Kundendetails ein.
1. Geben Sie die Bestelldetails (Produkte, Versandart) ein.
1. Wählen Sie eine Zahlungsmethode aus.
1. Senden Sie die Bestellung.

<u>Erwartete Ergebnisse</u>:

Sie können eine Bestellung erfolgreich senden.

<u>Tatsächliche Ergebnisse</u>:

Sie können keine Bestellung abschicken. Der folgende [!DNL JS] wird im Protokoll der Browser-Konsole angezeigt: &quot;*Die Ausführung des Inline-Skripts wurde abgelehnt, da es die folgende Content Security Policy-Anweisung verletzt: „script-src …*&quot;

### Ursache

In Adobe Commerce und Magento Open Source ab Version 2.4.7 ist **[!UICONTROL CSP]** standardmäßig in `restrict-mode` für Zahlungsseiten in den Bereichen Storefront und Admin und im `report-only` für alle anderen Seiten konfiguriert.
Der entsprechende **[!UICONTROL CSP]**-Header enthält nicht das `unsafe-inline` Schlüsselwort in der `script-src`-Direktive für Zahlungsseiten. Außerdem sind nur [!DNL whitelisted] Inline-Skripte zulässig.

### Lösung

Benutzer sehen möglicherweise Browser-Fehler, da bestimmte Skripte aufgrund von **[!UICONTROL CSP]** blockiert werden:

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

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
