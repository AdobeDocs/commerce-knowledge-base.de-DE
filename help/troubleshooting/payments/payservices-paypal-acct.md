---
title: PayPal-Sandbox-Konto nicht verifiziert
description: In diesem Artikel wird erläutert, warum Ihr PayPal-Sandbox-Konto für Zahlungsdienste möglicherweise nicht verifiziert wird, sodass Sie das Sandbox-Onboarding nicht abschließen können.
exl-id: 05ce130d-6dfe-4834-bdfc-837902100118
feature: Customer Service, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# PayPal-Sandbox-Konto nicht verifiziert

In diesem Artikel wird erläutert, warum Ihr PayPal-Sandbox-Konto für Zahlungsdienste möglicherweise nicht verifiziert wird, sodass Sie das Sandbox-Onboarding nicht abschließen können.

## Betroffene Produkte und Versionen

* [Payment Services](https://marketplace.magento.com/magento-payment-services.html) ist jetzt mit den Adobe Commerce-Versionen 2.4.0 bis 2.4.4 kompatibel.

## Problem

In [ Onboarding-](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/onboard.html) werden Sie aufgefordert, sich für ein PayPal-Konto anzumelden, sich beim PayPal-Entwicklerkonto anzumelden und dann ein Sandbox-Konto zu erstellen. Wenn Sie im Popup-Fenster „PayPal-Onboarding“ auswählen, ein neues Konto beim Onboarding zu erstellen, kann PayPal Ihr Sandbox-Konto nicht verifizieren und Sie können das Onboarding nicht abschließen.

<u>Schritte zur Reproduktion</u>:

1. Sie [Payment Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html) installieren und [Commerce Services konfigurieren](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#configure-commerce-services).
1. Navigieren Sie in **Admin zu** Zahlungsdienste“ und [ Sie „Sandbox-Onboarding](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/onboard.html).
1. Im angezeigten Popup-Fenster PayPal-Onboarding erstellen Sie während des Onboarding ein neues Geschäftskonto (anstelle [sich mit einem zuvor erstellten PayPal-Sandbox-Konto ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html#test-in-sandbox-environment)).
1. Sie haben das Onboarding von PayPal erfolgreich abgeschlossen.
1. Im Admin wird eine Benachrichtigung angezeigt, dass Ihre Sandbox-Zahlungen ausstehen und Sie Ihre E-Mail-Adresse mit PayPal bestätigen müssen, um das Onboarding abzuschließen.

   Sie haben keine Bestätigungs-E-Mail erhalten, da PayPal Ihre E-Mail-Adresse nicht verifizieren konnte.

## Ursache

PayPal kann Ihr Sandbox-Konto nicht verifizieren und Sie können das Sandbox-Onboarding nicht abschließen (was bedeutet, dass Sie keine Zahlungen akzeptieren oder Ihren Sandbox-Modus testen können), wenn Sie Ihr Sandbox-Konto vor Ihrem PayPal-Konto erstellen.

## Lösung

1. Verwenden eines im [PayPal-Entwicklerportal ](https://developer.paypal.com/docs/api-basics/sandbox/accounts/#create-a-business-sandbox-account) Sandbox-Kontos
1. Klicken Sie auf [Sandbox zurücksetzen](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html#test-in-sandbox-environment) und starten Sie das Sandbox-Onboarding neu.
1. [Wenden Sie sich an den ](mailto:payment-services-support@adobe.com), wenn Sie Ihre Kontoprobleme nicht beheben können, damit Sie das Onboarding fortsetzen und Zahlungen akzeptieren können.
