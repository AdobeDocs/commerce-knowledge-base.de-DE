---
title: Fehler beim Platzieren der Bestellung bei Authorize.net Sandbox-Konto (Auf dem Server ist ein Fehler aufgetreten)
description: Dieser Artikel enthält eine Fehlerbehebung für die Fehlermeldung "*Auf dem Server ist ein Fehler aufgetreten*", wenn Sie eine Bestellung mit Authorize.Net Direct Post aufgeben.
exl-id: 764a550a-3373-483c-843d-d8c848dcee35
feature: Compliance, Console, Customer Service, Orders, Payments
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Fehler beim Platzieren der Bestellung bei Authorize.net Sandbox-Konto (Auf dem Server ist ein Fehler aufgetreten)

Dieser Artikel enthält eine Fehlerbehebung für die Fehlermeldung &quot;*Ein Fehler ist auf dem Server*&quot;beim Platzieren einer Bestellung mit Authorize.Net Direct Post aufgetreten.

>[!WARNING]
>
>**Hinweis zur Einstellung der Verwendung**
>
>Aufgrund der Zahlungsdienstrichtlinie [PSD2](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/payments/compliance-payment-services-directive) und der kontinuierlichen Weiterentwicklung vieler APIs besteht die Gefahr, dass Authorize.Net veraltet wird und zukünftig nicht mehr sicherheitskonform ist. Aus diesem Grund wird sie jetzt nicht mehr unterstützt. Wir empfehlen Ihnen, sie in Ihrer Adobe Commerce-Konfiguration zu deaktivieren und zur entsprechenden [Commerce Marketplace-Erweiterung](https://marketplace.magento.com/extensions.html) zu wechseln.
>
>**Diese Integration wird aus der Adobe Commerce-Version 2.4.0 entfernt und ist von den aktuellen Versionen 2.3 entfernt.**
>
>Weitere Informationen zum Erstellen eines sicheren Übergangs von veralteten Zahlungsintegrationen finden Sie in unserem [DevBlog](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Magento-core-payment-integrations/ba-p/426445) .

## Problem

Wenn Sie eine Bestellung mit dem Sandbox-Konto [Authorize.Net Direct Post](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/payments/error-placing-order-with-authorize-net-sandbox-account-an-error-occurred-on-the-server) aufgeben, wird eine Fehlermeldung angezeigt:

>>
&quot;Auf dem Server ist ein Fehler aufgetreten. Versuchen Sie bitte, die Bestellung erneut aufzugeben.&quot;

## Ursache 1: Testmodus ist aktiviert

Es scheint nicht offensichtlich zu sein, aber die Einstellung **Testmodus** von Authorize.net muss auch beim Testen mit dem Sandbox-Konto auf **Nein** gesetzt werden.

## Lösung 1: Testmodus deaktivieren

1. Wechseln Sie zu **Geschäfte** > **Konfiguration** > **Verkauf** > **Zahlungsmethoden** > **Sonstige Zahlungsmethoden** > **Authorize.net Direkte Post**.
1. Setzen Sie **Testmodus** auf &quot;Nein&quot;(deaktivieren Sie **Systemwert verwenden** und wählen Sie dann im Menü &quot;Nein&quot; aus).
1. Klicken Sie auf **Konfiguration speichern**.

![authorize-net_test-mode_setting.png](/help/troubleshooting/miscellaneous/assets/authorize-net_test-mode_setting.png)

## Ursache 2: Falsche URLs

Die Einstellungen Authorize.net können falsche URL-Adressen für die kritischen Ressourcen Authorize.Net enthalten.

## Lösung 2: Stellen Sie die richtigen URLs bereit

* **Gateway-URL:**   `https://test.authorize.net/gateway/transact.dll`
* **Transaktionsdetails-URL:**   `https://apitest.authorize.net/xml/v1/request.api`
* **API-Referenz:**   `https://developer.authorize.net/api/reference/`

## Wenn nichts hilfreich ist: Debug-Informationen abrufen

Wenn die Platzierung einer Bestellung mit Authorize.net mit einem nicht informativen Fehler *&quot;Irgendetwas ist schief gegangen&quot;* fehlschlägt, überprüfen Sie die Adobe Commerce `debug.log`.

### Transact.dll

Wenn der `debug.log` leer ist, überprüfen Sie die Antwort **transact.dll** in der Konsole Ihres Webbrowsers:

1. Öffnen Sie die Konsole.
1. Bevor Sie eine Bestellung aufgeben, gehen Sie zur Registerkarte **Netzwerk** und wählen Sie **Protokoll beibehalten** aus.    ![web-console_network_preserve-log.png](assets/web-console_network_preserve-log.png)
1. Filtern Sie die Antworten nach **transact.dll**, um eine Antwortmeldung mit einem möglichen Fehler anzuzeigen.    ![transact-dll_web-console_response.png](assets/transact-dll_web-console_response.png)
