---
title: Fehler beim Platzieren der Bestellung bei Authorize.net Sandbox-Konto (Auf dem Server ist ein Fehler aufgetreten)
description: Dieser Artikel enthält eine Fehlerbehebung für die Fehlermeldung "*Auf dem Server ist ein Fehler aufgetreten*", wenn Sie eine Bestellung mit Authorize.Net Direct Post aufgeben.
exl-id: 764a550a-3373-483c-843d-d8c848dcee35
feature: Compliance, Console, Customer Service, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Fehler beim Platzieren der Bestellung bei Authorize.net Sandbox-Konto (Auf dem Server ist ein Fehler aufgetreten)

Dieser Artikel enthält eine Korrektur für *Auf dem Server ist ein Fehler aufgetreten.*&quot; Fehlermeldung bei der Bestellung mit Authorize.Net Direct Post.

>[!WARNING]
>
>**Hinweis zu veralteten Versionen**
>
>Aufgrund der Zahlungsdienstrichtlinie [PSD2](https://docs.magento.com/user-guide/v2.3/stores/compliance-payment-services-directive.html) Aufgrund der kontinuierlichen Weiterentwicklung vieler APIs besteht die Gefahr, dass Authorize.Net veraltet wird und in Zukunft nicht mehr sicherheitskonform ist. Aus diesem Grund wird sie jetzt nicht mehr unterstützt. Wir empfehlen Ihnen, sie in Ihrer Adobe Commerce-Konfiguration zu deaktivieren und zum entsprechenden [Commerce Marketplace-Erweiterung](https://marketplace.magento.com/extensions.html).
>
>**Diese Integration wird aus der Adobe Commerce-Version 2.4.0 entfernt und ist von den aktuellen Versionen 2.3 veraltet.**
>
>Weitere Informationen zum sicheren Übergang von veralteten Zahlungsintegrationen finden Sie in der [DevBlog](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Magento-core-payment-integrations/ba-p/426445).

## Problem

Platzieren einer Bestellung mithilfe von [Authorize.Net Direct Post](https://docs.magento.com/user-guide/v2.3/payment/authorize-net-direct-post.html) Sandbox-Konto verursacht eine Fehlermeldung:

>>
&quot;Auf dem Server ist ein Fehler aufgetreten. Versuchen Sie bitte, die Bestellung erneut aufzugeben.&quot;

## Ursache 1: Testmodus ist aktiviert

Es scheint nicht offensichtlich zu sein, aber die **Testmodus** muss auf **Nein** auch beim Testen mit dem Sandbox-Konto.

## Lösung 1: Testmodus deaktivieren

1. Navigieren Sie zu **Stores** > **Konfiguration** > **Vertrieb** > **Zahlungsmethoden** > **Andere Zahlungsmethoden** > **Authorize.net Briefpost**.
1. Satz **Testmodus** auf &quot;Nein&quot;(Deaktivieren) **Systemwert verwenden** und wählen Sie dann im Menü &quot;Nein&quot; aus).
1. Klicks **Konfiguration speichern**.

![authorize-net_test-mode_setting.png](/help/troubleshooting/miscellaneous/assets/authorize-net_test-mode_setting.png)

## Ursache 2: Falsche URLs

Die Einstellungen Authorize.net können falsche URL-Adressen für die kritischen Ressourcen Authorize.Net enthalten.

## Lösung 2: Stellen Sie die richtigen URLs bereit

* **Gateway-URL:**   `https://test.authorize.net/gateway/transact.dll`
* **Transaktionsdetails-URL:**   `https://apitest.authorize.net/xml/v1/request.api`
* **API-Referenz:**   `https://developer.authorize.net/api/reference/`

## Wenn nichts hilfreich ist: Debug-Informationen abrufen

Wenn die Platzierung einer Bestellung mit Authorize.net mit einem nicht informativen Fehler fehlschlägt *&quot;Irgendetwas ist schiefgelaufen&quot;* Fehler, überprüfen Sie die Adobe Commerce `debug.log`.

### Transact.dll

In diesem Fall `debug.log` leer ist, überprüfen Sie die **transact.dll** Antwort in der Konsole Ihres Webbrowsers:

1. Öffnen Sie die Konsole.
1. Bevor Sie eine Bestellung aufgeben, gehen Sie zu **Netzwerk** Registerkarte und wählen Sie **Protokoll beibehalten**.    ![web-console_network_preserve-log.png](assets/web-console_network_preserve-log.png)
1. Antworten filtern nach **transact.dll** um eine Antwortmeldung mit einem möglichen Fehler anzuzeigen.    ![transact-dll_web-console_response.png](assets/transact-dll_web-console_response.png)
