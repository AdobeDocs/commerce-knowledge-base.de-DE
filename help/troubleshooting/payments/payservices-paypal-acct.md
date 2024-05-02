---
title: PayPal-Sandbox-Konto nicht verifiziert
description: In diesem Artikel wird erläutert, warum Ihr PayPal-Sandbox-Konto für Zahlungsdienste möglicherweise nicht verifiziert wird. Dadurch wird verhindert, dass Sie das Onboarding von Sandboxes durchführen.
exl-id: 05ce130d-6dfe-4834-bdfc-837902100118
feature: Customer Service, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# PayPal-Sandbox-Konto nicht verifiziert

In diesem Artikel wird erläutert, warum Ihr PayPal-Sandbox-Konto für Zahlungsdienste möglicherweise nicht verifiziert wird. Dadurch wird verhindert, dass Sie das Onboarding von Sandboxes durchführen.

## Betroffene Produkte und Versionen

* [Zahlungsdienste](https://marketplace.magento.com/magento-payment-services.html) ist jetzt mit den Adobe Commerce-Versionen 2.4.0 bis 2.4.4 kompatibel.

## Problem

Unsere [Onboarding-Dokumentation](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/onboard.html) weist Sie an, sich für ein PayPal-Konto anzumelden, sich beim PayPal-Entwicklerkonto anzumelden und dann ein Sandbox-Konto zu erstellen. Wenn Sie im Popup-Fenster für das PayPal-Onboarding ein neues Konto beim Onboarding erstellen, kann PayPal Ihr Sandbox-Konto nicht überprüfen und Sie können das Onboarding nicht abschließen.

<u>Zu reproduzierende Schritte</u>:

1. You [Installieren von Zahlungsdiensten](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html) und [Commerce Services konfigurieren](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#configure-commerce-services).
1. Sie navigieren zu **Zahlungsdienste** im Admin und [Start-Sandbox-Onboarding](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/onboard.html).
1. Im angezeigten Popup PayPal-Onboarding erstellen Sie ein neues Geschäftskonto (anstelle von [Anmelden mit einem zuvor erstellten PayPal-Sandbox-Konto](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html#test-in-sandbox-environment) während des Onboarding.
1. Sie haben das Onboarding von PayPal erfolgreich abgeschlossen.
1. In Admin wird Ihnen eine Benachrichtigung angezeigt, dass Ihre Sandbox-Zahlungen ausstehen und Sie Ihre E-Mail-Adresse mit PayPal bestätigen müssen, um das Onboarding abzuschließen.

   Sie haben keine Bestätigungs-E-Mail erhalten, da PayPal Ihre E-Mail-Adresse nicht verifizieren konnte.

## Ursache

PayPal kann Ihr Sandbox-Konto nicht überprüfen und Sie können das Sandbox-Onboarding nicht beenden (d. h., Sie können keine Zahlungen annehmen oder Ihren Sandbox-Modus testen), wenn Sie Ihr Sandbox-Konto vor Ihrem PayPal-Konto erstellen.

## Lösung

1. Verwenden eines Sandbox-Kontos, das im [PayPal-Entwickler](https://developer.paypal.com/docs/api-basics/sandbox/accounts/#create-a-business-sandbox-account) Portal.
1. Klicks [Sandbox zurücksetzen](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html#test-in-sandbox-environment) und starten Sie das Onboarding Ihrer Sandbox neu.
1. [Support kontaktieren](mailto:payment-services-support@adobe.com) wenn Sie Ihre Kontoprobleme nicht beheben können, sodass Sie das Onboarding fortsetzen und Zahlungen annehmen können.
