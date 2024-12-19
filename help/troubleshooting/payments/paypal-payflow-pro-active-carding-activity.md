---
title: PayPal Payflow Proaktive Kartenaktivität
description: 'AKTUALISIERT: 2. April 2019'
exl-id: 9fe73788-5b67-445a-9b0d-86489125d271
feature: Cache, Orders, Payments
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '665'
ht-degree: 0%

---

# PayPal Payflow Proaktive Kartenaktivität

AKTUALISIERT: 2. April 2019

Die Integration von PayPal Payflow Pro in Adobe Commerce wird aktiv durch Kartenaktivitäten angegriffen, bei denen Angreifer Hunderte von $0 Transaktionen mit gestohlenen Kreditkarten versuchen, die Gültigkeit der Karte zu überprüfen.

Die Aktivität zielt derzeit auf Versionen dieser Payflow Pro-Integration ab, die in Adobe Commerce 2.1.x, 2.2.x, 2.3.x für Magento Open Source und Commerce (On-Premise und Cloud) enthalten waren. Die Kartenaktivität ist mit der Art und Weise verbunden, wie Payflow Pro in Einkaufswagen integriert wird.

>[!NOTE]
>
>Um diese Probleme zu beheben, haben wir neue Composer-Pakete bereitgestellt, um Google reCAPTCHA oder CAPTCHA zum Payflow Pro-Checkout-Formular hinzuzufügen. Es wird empfohlen, diese Pakete in allen Versionen und Editionen von Adobe Commerce zu installieren.

Das Problem betrifft die folgenden Adobe Commerce-Versionen:

* Adobe Commerce On-Premises v2.1.x, 2.2.x, 2.3.x
* Adobe Commerce auf Cloud-Infrastruktur v2.1.x, 2.2.x, 2.3.x

## Problem

Symptome dieser Anfälle sind:

* In Ihrem PayPal Payflow Pro-Konto werden Hunderte von betrügerischen Transaktionen angezeigt
* PayPal kann ein Payflow Pro-Konto aufgrund eingehender Betrugsvorgänge sperren und hohe Gebühren erheben

## Lösung

Um sich vor diesen Angriffen zu schützen, empfehlen wir, Google reCAPTCHA (empfohlen) oder CAPTCHA zum Payflow Pro-Checkout-Formular hinzuzufügen. Dazu gehört die Installation der Composer-Pakete und die Konfiguration von Google reCAPTCHA oder CAPTCHA in Commerce Admin.

### Installieren von Paketen

Adobe hat zwei Paketoptionen erstellt, um Google reCAPTCHA und/oder CAPTCHA zum Payflow Pro-Checkout-Formular hinzuzufügen. Mit der Installation eines dieser Pakete werden die aktuellen Installationen aktualisiert und eine Option hinzugefügt, mit der diese Sicherheit im Payflow Pro-Checkout-Formular verbessert werden kann.

Diese Pakete sind mit den folgenden Adobe Commerce-Bereitstellungen und -Versionen kompatibel:

Adobe Commerce (alle Bereitstellungsmethoden) und Magento Open Source 2.1.x, 2.2.x, 2.3.x

Die Installation erfordert CLI-Befehle für Ihre Adobe Commerce-Instanz. Es kann Unterstützung durch einen Entwickler erforderlich sein.

>[!NOTE]
>
>Es wird empfohlen, Google reCAPTCHA zusätzlich zur Installation relevanter Payflow Pro Checkout-Formular-Updates zu installieren und zu konfigurieren. Diese Option bietet eine unsichtbare Prüfung und mehrere Konfigurationsoptionen.

#### Installieren von Google reCAPTCHA- und Checkout-Formular-Updates

Das `magento/module-paypal-recaptcha`-Paket enthält die Integration mit Google reCAPTCHA- und Payflow Pro-Zahlungsformularaktualisierungen. Auch wenn Sie das reCAPTCHA-Modul installiert und konfiguriert haben, empfehlen wir die Installation dieses Pakets.

Führen Sie die folgenden Befehle aus, um es zu installieren.

**Für Adobe Commerce On-Premise:**

```bash
composer require magento/module-paypal-recaptcha
bin/magento module:enable Magento_PaypalReCaptcha
bin/magento setup:upgrade
bin/magento cache:clean
```

**Für Adobe Commerce auf Cloud-Infrastruktur:**

1. Führen Sie den folgenden Befehl aus:

   ```bash
   composer require magento/module-paypal-recaptcha
   ```

1. Änderungen übertragen und übertragen:

   ```bash
   git add -A && git commit -m "Install Google reCAPTCHA"    git push origin %branch_name%
   ```

1. Warten Sie, bis die Bereitstellung abgeschlossen ist.

#### Installieren von Aktualisierungen des Checkout-Formulars für CAPTCHA

Das `magento/module-paypal-captcha`-Paket enthält die Integration mit dem nativen Adobe Commerce CAPTCHA-Modul.

Führen Sie die folgenden Befehle aus, um es zu installieren:

**Für Adobe Commerce On-Premise:**

```bash
composer require magento/module-paypal-captcha
bin/magento module:enable Magento_PaypalCaptcha
bin/magento setup:upgrade
bin/magento cache:clean
```

**Für Adobe Commerce auf Cloud-Infrastruktur:**

1. Führen Sie den folgenden Befehl aus:

   ```bash
   composer require magento/module-paypal-captcha
   ```

1. Änderungen übertragen und übertragen:

   ```bash
   git add -A && git commit -m "Install CAPTCHA"    git push origin %branch_name%
   ```

1. Warten Sie, bis die Bereitstellung abgeschlossen ist.

### Konfigurieren von Google reCAPTCHA oder CAPTCHA

Konfigurieren Sie nach der Installation des Pakets Google reCAPTCHA (empfohlen) oder CAPTCHA, wie in den folgenden Dokumenten beschrieben:

* [Google reCAPTCHA](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/captcha/security-google-recaptcha) in unserem Benutzerhandbuch.
* [CAPTCHA](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/captcha/security-captcha) in unserem Benutzerhandbuch.

Die neue Option Checkout-Formular ist:

* Google reCAPTCHA: Verwenden des Zahlungsformulars PayPal Payflow Pro
* CAPTCHA: Payflow Pro

## PayPal-Support und Kontakte

Wenden Sie sich an den PayPal Payflow-Support, um mehr über Betrugsschutzdienste zu erfahren. Sie können das PayPal-Supportteam bitten, Filter für [Standard-Betrugsschutz](https://developer.paypal.com/api/nvp-soap/payflow/fraud-protection/) zu aktivieren, um eine möglichst strenge Kontrolle über Zahlungen zu ermöglichen, sodass Sie automatisch Zahlungen ablehnen können, die wahrscheinlich zu betrügerischen Transaktionen führen, und Zahlungen akzeptieren können, die normalerweise kein Problem darstellen. Bitte beachten Sie, dass es nach dem Einschalten der PayPal-Filter für den Betrugsschutz bis zu 2 Stunden dauern kann, bis die Transaktionen abgewickelt sind.

>[!NOTE]
>
>Weitere Informationen finden Sie unter KB [&quot;Adobe von PayPal, der mich bezüglich meiner Payflow Pro-Integration kontaktiert hat. Was muss ich tun?“](https://www.paypal.com/us/smarthelp/article/ts2242).

**Details zum PayPal Payflow Merchant Support**

Die Geschäftszeiten des Payflow Merchant Supports sind von Montag bis Freitag von 7:00 bis 20:00 Uhr CST. Sie können sich telefonisch oder per E-Mail an den Payflow Merchant Support wenden, um Unterstützung zu erhalten:

* Telefon: 1-888-883-9770 (Eingabeaufforderung 2 auswählen)
* Internationale Kunden: 1-408-967-0191
* E-Mail: [payflow-support@paypal.com](mailto:payflow-support@paypal.com)

Australischer Support

* Montag-Freitag 8:00 - 19:00 Uhr (AU-Zeit)
* Tel.: +61 2 8288 0198
* E-Mail: [gateway-ausupport@paypal.com](mailto:gateway-ausupport@paypal.com)
