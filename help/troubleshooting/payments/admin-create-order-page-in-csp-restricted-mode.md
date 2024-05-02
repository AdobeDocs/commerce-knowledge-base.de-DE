---
title: Fehlerbehebung beim Erstellen einer Bestellseite in [!UICONTROL CSP] eingeschränkter Modus
description: In diesem Artikel werden Fehler beim Erstellen einer Bestellung auf der Admin-Seite erläutert, wenn der eingeschränkte CSP-Modus aktiviert ist, und es werden Lösungen zur Behebung dieser Fehler bereitgestellt.
feature: Checkout,Security,Orders,Payments
role: Developer
exl-id: c1a0886a-df1f-418a-9e4d-562b28a0d8b3
source-git-commit: 6d0c4ea9576440d66be3b8053a6e362b8ac0ebcb
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%

---

# Fehlerbehebung beim Erstellen einer Bestellseite in [!UICONTROL CSP] eingeschränkter Modus

In diesem Artikel finden Sie Erklärungen und Fehlerbehebungen zu Problemen mit Adobe Commerce 2.4.7 beim Erstellen einer Bestellung auf der Admin-Seite mit **[!UICONTROL CSP restricted mode]** is *Aktiviert* mit &quot;*Weigert, Inline-Skript auszuführen, weil es die folgende Content Security Policy-Anweisung verletzt: &quot;script-src ...*&quot; Fehlermeldung im Browser-Konsolenprotokoll.

## Betroffene Produkte und Versionen

Adobe Commerce zur Cloud-Infrastruktur, Adobe Commerce vor Ort und Magento Open Source:

* 2,4,7
* 2.4.6-pX
* 2.4.5-pX
* 2.4.4-pX

## Problem - Admin **Bestellung erstellen** Seite ist beschädigt oder kann nicht geladen werden

Der Administrator **Bestellung erstellen** -Seite beschädigt ist oder nicht geladen werden kann, mit dem *Weigert, Inline-Skript auszuführen, weil es die folgende Content Security Policy-Anweisung verletzt: &quot;script-src ...*&quot; Fehlermeldung im Browser-Konsolenprotokoll.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Erstellen Sie eine neue Bestellung.

<u>Erwartete Ergebnisse</u>:

Der Administrator **Bestellung erstellen** Seite wird normal geladen.

<u>Tatsächliche Ergebnisse</u>:

Der Administrator **Bestellung erstellen** -Seite leer ist oder Komponenten fehlen. Die folgenden [!DNL JS] im Protokoll der Browserkonsole wird ein Fehler angezeigt: &quot;*Weigert, Inline-Skript auszuführen, weil es die folgende Content Security Policy-Anweisung verletzt: &quot;script-src ...*&quot;

### Ursache

In Adobe Commerce und Magento Open Source Version 2.4.7 und höher **[!UICONTROL CSP]** konfiguriert in `restrict-mode`, standardmäßig für Zahlungsseiten in den Storefront- und Admin-Bereichen und in `report-only` -Modus für alle anderen Seiten.
Die entsprechende **[!UICONTROL CSP]** -Kopfzeile enthält nicht die `unsafe-inline` Suchbegriff in `script-src` -Anweisung für Zahlungsseiten. Nur [!DNL whitelisted] Inline-Skripte sind zulässig.

### Lösung

Benutzern werden möglicherweise Browserfehler angezeigt, da bestimmte Skripte aufgrund von [!UICONTROL CSP]:

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

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

Zahlungsmethode fehlt oder funktioniert nicht mit dem Administrator **Bestellseite** mit &quot;*Weigert, Inline-Skript auszuführen, weil es die folgende Content Security Policy-Anweisung verletzt: &quot;script-src ...*&quot; Fehlermeldung im Browser-Konsolenprotokoll.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Erstellen Sie eine neue Bestellung.
1. Erstellen Sie einen neuen Kunden.
1. Geben Sie die Kundendetails ein.
1. Geben Sie die Bestelldetails (Produkte, Versandmethode) ein.
1. Wählen Sie eine Zahlungsmethode aus.

<u>Erwartete Ergebnisse</u>:

Sie können eine Zahlungsmethode auswählen und mit der erfolgreichen Bestellung fortfahren.

<u>Tatsächliche Ergebnisse</u>:

Die Zahlungsmethode fehlt oder funktioniert nicht. Die folgenden [!DNL JS] im Protokoll der Browserkonsole wird ein Fehler angezeigt: &quot;*Weigert, Inline-Skript auszuführen, weil es die folgende Content Security Policy-Anweisung verletzt: &quot;script-src ...*&quot;.

### Ursache

In Adobe Commerce und Magento Open Source Version 2.4.7 und höher **[!UICONTROL CSP]** konfiguriert in `restrict-mode`, standardmäßig für Zahlungsseiten in den Storefront- und Admin-Bereichen und in `report-only` -Modus für alle anderen Seiten.
Die entsprechende **[!UICONTROL CSP]** -Kopfzeile enthält nicht die `unsafe-inline` Suchbegriff in `script-src` -Anweisung für Zahlungsseiten. Nur [!DNL whitelisted] Inline-Skripte sind zulässig.

### Lösung

Benutzern werden möglicherweise Browserfehler angezeigt, da bestimmte Skripte aufgrund von **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

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

1. [hinzufügen [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) auf die `csp_whitelist.xml` -Datei.

## Problem - Der Administrator kann keine Bestellung aufgeben

Ein Administrator kann keine Bestellung beim Administrator senden **Bestellseite erstellen** mit &quot;*Weigert, Inline-Skript auszuführen, weil es die folgende Content Security Policy-Anweisung verletzt: &quot;script-src ...*&quot; Fehlermeldung im Browser-Konsolenprotokoll.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Erstellen Sie eine neue Bestellung.
1. Erstellen Sie einen neuen Kunden.
1. Geben Sie die Kundendetails ein.
1. Geben Sie die Bestelldetails (Produkte, Versandmethode) ein.
1. Wählen Sie eine Zahlungsmethode aus.
1. Übermitteln Sie die Bestellung.

<u>Erwartete Ergebnisse</u>:

Sie können eine Bestellung erfolgreich versenden.

<u>Tatsächliche Ergebnisse</u>:

Sie können keine Bestellung senden. Die folgenden [!DNL JS] im Protokoll der Browserkonsole wird ein Fehler angezeigt: &quot;*Weigert, Inline-Skript auszuführen, weil es die folgende Content Security Policy-Anweisung verletzt: &quot;script-src ...*&quot;

### Ursache

In Adobe Commerce und Magento Open Source Version 2.4.7 und höher **[!UICONTROL CSP]** konfiguriert in `restrict-mode`, standardmäßig für Zahlungsseiten in den Storefront- und Admin-Bereichen und in `report-only` -Modus für alle anderen Seiten.
Die entsprechende **[!UICONTROL CSP]** -Kopfzeile enthält nicht die `unsafe-inline` Suchbegriff in `script-src` -Anweisung für Zahlungsseiten. Nur [!DNL whitelisted] Inline-Skripte sind zulässig.

### Lösung

Benutzern werden möglicherweise Browserfehler angezeigt, da bestimmte Skripte aufgrund von **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

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
