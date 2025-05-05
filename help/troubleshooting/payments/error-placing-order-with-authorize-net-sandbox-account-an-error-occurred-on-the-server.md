---
title: Fehler beim Platzieren der Bestellung beim Sandbox-Konto Authorize.net (auf dem Server ist ein Fehler aufgetreten)
description: Dieser Artikel bietet eine Fehlerbehebung für die Fehlermeldung „Auf dem Server ist ein Fehler aufgetreten“, wenn eine Bestellung mit Authorize.Net Direct Post aufgegeben wird.
exl-id: 764a550a-3373-483c-843d-d8c848dcee35
feature: Compliance, Console, Customer Service, Orders, Payments
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Fehler beim Platzieren der Bestellung beim Sandbox-Konto Authorize.net (auf dem Server ist ein Fehler aufgetreten)

Dieser Artikel enthält eine Fehlerbehebung für die Fehlermeldung &quot;*Auf dem Server ist ein Fehler aufgetreten* beim Aufgeben einer Bestellung mit Authorize.Net Direct Post.

>[!WARNING]
>
>**Hinweis zu veralteten**
>
>Aufgrund der Zahlungsdiensterichtlinie [PSD2](https://experienceleague.adobe.com/de/docs/commerce-admin/start/compliance/payments/compliance-payment-services-directive) und der kontinuierlichen Weiterentwicklung vieler APIs besteht die Gefahr, dass Authorize.Net in Zukunft veraltet und nicht mehr sicherheitskonform ist. Aus diesem Grund wird sie jetzt nicht mehr unterstützt. Wir empfehlen, sie in Ihrer Adobe Commerce-Konfiguration zu deaktivieren und zur entsprechenden [Commerce Marketplace-Erweiterung zu ](https://marketplace.magento.com/extensions.html).
>
>**Diese Integration wurde aus der Adobe Commerce-Version 2.4.0 entfernt und ist seit der aktuellen Version 2.3.** veraltet
>
>Weitere Informationen zu einem sicheren Übergang von veralteten Zahlungsintegrationen finden Sie in unserem [DevBlog](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Magento-core-payment-integrations/ba-p/426445).

## Problem

Das Aufgeben einer Bestellung mit [Authorize.Net Direct Post](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/troubleshooting/payments/error-placing-order-with-authorize-net-sandbox-account-an-error-occurred-on-the-server) Sandbox-Konto verursacht eine Fehlermeldung:

&#x200B;>>
„Fehler auf dem Server. Bitte erneut versuchen, eine Bestellung aufzugeben“

## Ursache 1: Testmodus ist aktiviert

Es scheint nicht offensichtlich zu sein, aber die Einstellung **Testmodus“ von Authorize** net muss auf &quot;**&quot; gesetzt werden** auch beim Testen mit dem Sandbox-Konto.

## Lösung 1: Deaktivieren des Testmodus

1. Gehen Sie **Stores** > **Konfiguration** > **Verkauf** > **Zahlungsmethoden** > **Andere Zahlungsmethoden** > **Authorize.net Direct Post**.
1. Setzen Sie **Testmodus** auf „Nein“ (deaktivieren Sie **Systemwert verwenden** und wählen Sie dann im Menü „Nein“ aus).
1. Klicken Sie **Konfiguration speichern**.

![authorize-net_test-mode_setting.png](/help/troubleshooting/miscellaneous/assets/authorize-net_test-mode_setting.png)

## Ursache 2: Falsche URLs

Die Einstellungen unter Authorize.net enthalten möglicherweise falsche URL-Adressen für die kritischen Authorize.Net-Ressourcen.

## Lösung 2: Angeben der richtigen URLs

* **Gateway-URL:**   `https://test.authorize.net/gateway/transact.dll`
* **Transaktionsdetails-URL:**   `https://apitest.authorize.net/xml/v1/request.api`
* **API-Referenz:**   `https://developer.authorize.net/api/reference/`

## Wenn nichts half: Debugging-Informationen abrufen

Wenn die Bestellung bei Authorize.net mit dem Fehler „Irgendetwas ist schiefgelaufen“ fehlschlägt *überprüfen Sie* Adobe Commerce-`debug.log`.

### Transact.dll

Wenn die `debug.log` leer ist, überprüfen Sie die Antwort **transact.dll** in der Konsole Ihres Webbrowsers:

1. Öffnen Sie die Konsole.
1. Bevor Sie eine Bestellung aufgeben, wechseln Sie zur Registerkarte **Netzwerk** und wählen Sie **Protokoll beibehalten** aus.    ![web-console_network_preserve-log.png](assets/web-console_network_preserve-log.png)
1. Filtern Sie Antworten nach **transact.dll**, um eine Antwortmeldung mit einem möglichen Fehler anzuzeigen.    ![transact-dll_web-console_response.png](assets/transact-dll_web-console_response.png)
