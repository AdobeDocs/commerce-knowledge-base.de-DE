---
title: Fehlerbehebung beim Erstellen einer Bestellseite im eingeschränkten Modus [!UICONTROL CSP]
description: In diesem Artikel werden Fehler beim Erstellen einer Bestellung auf der Admin-Seite erläutert, wenn der eingeschränkte CSP-Modus aktiviert ist, und es werden Lösungen zur Behebung dieser Fehler bereitgestellt.
feature: Checkout,Security,Orders,Payments
role: Developer
exl-id: c1a0886a-df1f-418a-9e4d-562b28a0d8b3
source-git-commit: 6d0c4ea9576440d66be3b8053a6e362b8ac0ebcb
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%

---

# Fehlerbehebung beim Erstellen einer Bestellseite im eingeschränkten Modus [!UICONTROL CSP]

Dieser Artikel enthält Erklärungen und Fehlerbehebungen für die Probleme in Adobe Commerce 2.4.7 beim Erstellen einer Bestellung auf der Admin-Seite mit **[!UICONTROL CSP restricted mode]** ist *Aktiviert*. Die &quot;*Weigerung, Inline-Skript auszuführen, weil sie gegen die folgende Content Security Policy-Anweisung verstößt: Fehlermeldung &quot;script-src ...*&quot; im Browser-Konsolenprotokoll.

## Betroffene Produkte und Versionen

Adobe Commerce zur Cloud-Infrastruktur, Adobe Commerce vor Ort und Magento Open Source:

* 2,4,7
* 2.4.6-pX
* 2.4.5-pX
* 2.4.4-pX

## Problem - Die Admin **-Seite zum Erstellen einer Bestellung** ist fehlerhaft oder kann nicht geladen werden

Die Admin-Seite **Reihenfolge erstellen** ist beschädigt oder kann nicht geladen werden. Die Fehlermeldung &quot;*Abgelehnt, Inline-Skript auszuführen, da sie gegen die folgende Content Security Policy-Anweisung verstößt: &quot;script-src ...*&quot;-Fehlermeldung im Browser-Konsolenprotokoll.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Erstellen Sie eine neue Bestellung.

<u>Erwartete Ergebnisse</u>:

Die Seite Admin **create order** wird normal geladen.

<u>Tatsächliche Ergebnisse</u>:

Die Seite Admin **Bestellung erstellen** ist leer oder es fehlen Komponenten. Der folgende [!DNL JS]-Fehler wird im Browser-Konsolenprotokoll angezeigt: &quot;*Weigert, Inline-Skript auszuführen, da er gegen die folgende Content Security Policy-Anweisung verstößt: &quot;script-src ...*&quot;

### Ursache

In Adobe Commerce und Magento Open Source Version 2.4.7 und höher ist **[!UICONTROL CSP]** standardmäßig für Zahlungsseiten in den Storefront- und Admin-Bereichen und im Modus `report-only` für alle anderen Seiten konfiguriert.
`restrict-mode`
Die entsprechende Kopfzeile **[!UICONTROL CSP]** enthält nicht das Schlüsselwort `unsafe-inline` innerhalb der Anweisung `script-src` für Zahlungsseiten. Außerdem sind nur Inline-Skripte vom Typ [!DNL whitelisted] zulässig.

### Lösung

Benutzern werden möglicherweise Browserfehler angezeigt, da bestimmte Skripte aufgrund von [!UICONTROL CSP] blockiert wurden:

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

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

Die Zahlungsmethode fehlt oder funktioniert nicht auf der Admin- **Seite zum Erstellen der Bestellung**, mit der &quot;*Verweigert, Inline-Skript auszuführen, da sie gegen die folgende Content Security Policy-Anweisung verstößt: Fehlermeldung &quot;script-src ...*&quot; im Browser-Konsolenprotokoll.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Erstellen Sie eine neue Bestellung.
1. Erstellen Sie einen neuen Kunden.
1. Geben Sie die Kundendetails ein.
1. Geben Sie die Bestelldetails (Produkte, Versandmethode) ein.
1. Wählen Sie eine Zahlungsmethode aus.

<u>Erwartete Ergebnisse</u>:

Sie können eine Zahlungsmethode auswählen und mit der erfolgreichen Bestellung fortfahren.

<u>Tatsächliche Ergebnisse</u>:

Die Zahlungsmethode fehlt oder funktioniert nicht. Der folgende [!DNL JS] -Fehler wird im Browser-Konsolenprotokoll angezeigt: &quot;*Weigert, Inline-Skript auszuführen, da er gegen die folgende Content Security Policy-Anweisung verstößt: &quot;script-src ...*&quot;.

### Ursache

In Adobe Commerce und Magento Open Source Version 2.4.7 und höher ist **[!UICONTROL CSP]** standardmäßig für Zahlungsseiten in den Storefront- und Admin-Bereichen und im Modus `report-only` für alle anderen Seiten konfiguriert.
`restrict-mode`
Die entsprechende Kopfzeile **[!UICONTROL CSP]** enthält nicht das Schlüsselwort `unsafe-inline` innerhalb der Anweisung `script-src` für Zahlungsseiten. Außerdem sind nur Inline-Skripte vom Typ [!DNL whitelisted] zulässig.

### Lösung

Benutzern werden möglicherweise Browserfehler angezeigt, da bestimmte Skripte aufgrund von **[!UICONTROL CSP]** blockiert wurden:

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

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

## Problem - Der Administrator kann keine Bestellung aufgeben

Ein Administrator kann auf der Admin-Seite **Bestellseite erstellen** keine Bestellung senden, mit der Fehlermeldung &quot;*Abgelehnt, Inline-Skript auszuführen, da sie gegen die folgende Content Security Policy-Anweisung verstößt: &quot;script-src ...*&quot; im Browser-Konsolenprotokoll.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Erstellen Sie eine neue Bestellung.
1. Erstellen Sie einen neuen Kunden.
1. Geben Sie die Kundendetails ein.
1. Geben Sie die Bestelldetails (Produkte, Versandmethode) ein.
1. Wählen Sie eine Zahlungsmethode aus.
1. Übermitteln Sie die Bestellung.

<u>Erwartete Ergebnisse</u>:

Sie können eine Bestellung erfolgreich versenden.

<u>Tatsächliche Ergebnisse</u>:

Sie können keine Bestellung senden. Der folgende [!DNL JS]-Fehler wird im Browser-Konsolenprotokoll angezeigt: &quot;*Weigert, Inline-Skript auszuführen, da er gegen die folgende Content Security Policy-Anweisung verstößt: &quot;script-src ...*&quot;

### Ursache

In Adobe Commerce und Magento Open Source Version 2.4.7 und höher ist **[!UICONTROL CSP]** standardmäßig für Zahlungsseiten in den Storefront- und Admin-Bereichen und im Modus `report-only` für alle anderen Seiten konfiguriert.
`restrict-mode`
Die entsprechende Kopfzeile **[!UICONTROL CSP]** enthält nicht das Schlüsselwort `unsafe-inline` innerhalb der Anweisung `script-src` für Zahlungsseiten. Außerdem sind nur Inline-Skripte vom Typ [!DNL whitelisted] zulässig.

### Lösung

Benutzern werden möglicherweise Browserfehler angezeigt, da bestimmte Skripte aufgrund von **[!UICONTROL CSP]** blockiert wurden:

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

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
