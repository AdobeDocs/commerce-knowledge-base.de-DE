---
title: Aktivität "PayPal Payflow Pro"
description: AKTUALISIERT AM 2. April 2019
exl-id: 9fe73788-5b67-445a-9b0d-86489125d271
feature: Cache, Orders, Payments
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '665'
ht-degree: 0%

---

# Aktivität &quot;PayPal Payflow Pro&quot;

AKTUALISIERT AM 2. April 2019

Die PayPal Payflow Pro-Integration in Adobe Commerce wird aktiv in die Aktivität &quot;Carding&quot;einbezogen, bei der Angreifer versuchen, Hunderte von $0 Transaktionen mit gestohlenen Kreditkarten zu tätigen, um die Gültigkeit der Karte zu überprüfen.

Die Aktivität wendet sich derzeit an Versionen dieser Payflow Pro-Integration, die in Adobe Commerce 2.1.x, 2.2.x, 2.3.x für Magento Open Source und Commerce (lokal und in der Cloud) enthalten waren. Die Aktivität &quot;Warenkorb&quot;ist mit der Integration von Payflow Pro in Warenkörbe verknüpft.

>[!NOTE]
>
>Um diese Probleme zu beheben, haben wir neue Composer-Pakete bereitgestellt, um Google reCAPTCHA oder CAPTCHA zum Zahlungsformular von Payflow Pro hinzuzufügen. Es wird empfohlen, diese Pakete auf allen Adobe Commerce-Versionen und -Editionen zu installieren.

Das Problem betrifft die folgenden Adobe Commerce-Versionen:

* Adobe Commerce lokal, v2.1.x, 2.2.x, 2.3.x
* Adobe Commerce auf Cloud-Infrastruktur v2.1.x, 2.2.x, 2.3.x

## Problem

Zu den Symptomen dieser Angriffe gehören:

* Ihr PayPal Payflow Pro-Konto zeigt Hunderte von betrügerischen Transaktionen identifiziert
* PayPal kann ein Payflow Pro-Konto aufgrund eingehender Betrugsvorgänge aussetzen und erhebliche Gebühren erheben

## Lösung

Zum Schutz vor diesen Angriffen empfehlen wir, Google reCAPTCHA (empfohlen) oder CAPTCHA zum Checkout-Formular für Payflow Pro hinzuzufügen. Dazu gehört die Installation der Composer-Pakete und die Konfiguration von Google reCAPTCHA oder CAPTCHA in der Commerce Admin.

### Pakete installieren

Adobe hat zwei Paketoptionen erstellt, um Google reCAPTCHA und/oder CAPTCHA zum Zahlungsformular von Payflow Pro hinzuzufügen. Durch die Installation eines dieser Pakete werden die aktuellen Installationen aktualisiert und eine Option hinzugefügt, die dazu beiträgt, diese Sicherheit im Zahlungsformular von Payflow Pro zu verbessern.

Diese Pakete sind mit den folgenden Adobe Commerce-Implementierungen und -Versionen kompatibel:

Adobe Commerce (alle Bereitstellungsmethoden) und Magento Open Source 2.1.x, 2.2.x, 2.3.x

Für die Installation sind CLI-Befehle für Ihre Adobe Commerce-Instanz erforderlich. Möglicherweise ist Hilfe für Entwickler erforderlich.

>[!NOTE]
>
>Es wird empfohlen, Google reCAPTCHA zu installieren und zu konfigurieren und zusätzlich alle relevanten Payflow Pro Checkout-Formularaktualisierungen zu installieren. Diese Option bietet eine unsichtbare Prüfung und mehrere Konfigurationsoptionen.

#### Installieren von Google reCAPTCHA und Checkout-Formularaktualisierungen

Das Paket `magento/module-paypal-recaptcha` enthält die Integration in Google reCAPTCHA- und Payflow Pro-Zahlungsformularaktualisierungen. Selbst wenn Sie das reCAPTCHA-Modul installiert und konfiguriert haben, empfehlen wir Ihnen, dieses Paket zu installieren.

Führen Sie die folgenden Befehle aus, um sie zu installieren.

**Für Adobe Commerce vor Ort:**

```bash
composer require magento/module-paypal-recaptcha
bin/magento module:enable Magento_PaypalReCaptcha
bin/magento setup:upgrade
bin/magento cache:clean
```

**Für Adobe Commerce in Cloud-Infrastruktur:**

1. Führen Sie den folgenden Befehl aus:

   ```bash
   composer require magento/module-paypal-recaptcha
   ```

1. Zusage und Push-Änderungen:

   ```bash
   git add -A && git commit -m "Install Google reCAPTCHA"    git push origin %branch_name%
   ```

1. Warten Sie, bis die Bereitstellung abgeschlossen ist.

#### Checkout-Formularaktualisierungen für CAPTCHA installieren

Das Paket `magento/module-paypal-captcha` enthält die Integration mit dem nativen Adobe Commerce CAPTCHA-Modul.

Führen Sie die folgenden Befehle aus, um sie zu installieren:

**Für Adobe Commerce vor Ort:**

```bash
composer require magento/module-paypal-captcha
bin/magento module:enable Magento_PaypalCaptcha
bin/magento setup:upgrade
bin/magento cache:clean
```

**Für Adobe Commerce in Cloud-Infrastruktur:**

1. Führen Sie den folgenden Befehl aus:

   ```bash
   composer require magento/module-paypal-captcha
   ```

1. Zusage und Push-Änderungen:

   ```bash
   git add -A && git commit -m "Install CAPTCHA"    git push origin %branch_name%
   ```

1. Warten Sie, bis die Bereitstellung abgeschlossen ist.

### Konfigurieren von Google reCAPTCHA oder CAPTCHA

Nachdem Sie das Paket installiert haben, konfigurieren Sie Google reCAPTCHA (empfohlen) oder CAPTCHA wie in den folgenden Dokumenten beschrieben:

* [Google reCAPTCHA](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/captcha/security-google-recaptcha) in unserem Benutzerhandbuch.
* [CAPTCHA](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/captcha/security-captcha) in unserem Benutzerhandbuch.

Die neue Option für das Checkout-Formular lautet:

* Google reCAPTCHA: Verwendung im PayPal Payflow Pro Zahlungsformular
* CAPTCHA: Payflow Pro

## PayPal-Unterstützung und -Kontakte

Wenden Sie sich an den PayPal Payflow Merchant Support , um mehr über Betrugsschutzdienste zu erfahren. Sie können das PayPal-Supportteam bitten, die Filter [Grundlegende Betrugsschutzdienste](https://developer.paypal.com/api/nvp-soap/payflow/fraud-protection/) zu aktivieren, um eine möglichst strenge Kontrolle über Zahlungen zu ermöglichen, sodass Sie Zahlungen, die zu betrügerischen Transaktionen führen können, automatisch ablehnen und Zahlungen akzeptieren können, die normalerweise kein Problem darstellen. Bitte beachten Sie, dass es nach der Aktivierung der PayPal Fraud Protection Services-Filter bis zu 2 Stunden dauern kann, bis Transaktionen abgewickelt werden.

>[!NOTE]
>
>Weitere Informationen finden Sie in der KB [-Adobe von PayPal, die mich über meine Payflow Pro-Integration kontaktiert hat. Was muss ich tun?&quot;](https://www.paypal.com/us/smarthelp/article/ts2242).

**Details zur Unterstützung des PayPal-Payflow-Händlers**

Die Geschäftszeiten des Payflow Merchant Supports sind Montag bis Freitag von 19:00 - 20:00 Uhr CST. Sie können sich an den Payflow Merchant-Support wenden, um Unterstützung per Telefon oder E-Mail zu erhalten:

* Telefon: 1-888-883-9770 (Wählen Sie die Eingabeaufforderung 2 aus)
* Internationale Kunden: 1-408-967-0191
* E-Mail: [payflow-support@paypal.com](mailto:payflow-support@paypal.com)

Australische Unterstützung

* Montag bis Freitag 8:00 - 19:00 Uhr (AU-Zeit)
* Tel.: +61 2 8288 0198
* E-Mail: [gateway-ausupport@paypal.com](mailto:gateway-ausupport@paypal.com)
