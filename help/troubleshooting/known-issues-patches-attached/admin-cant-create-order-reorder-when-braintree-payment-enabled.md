---
title: Der Administrator kann keine Bestellung/Neuanordnung erstellen, wenn die Braintree-Zahlung aktiviert ist
description: Dieser Artikel enthält einen Patch für das Problem Adobe Commerce 2.4.5, bei dem ein Admin-Benutzer keine Bestellungen erstellen oder für Kunden neu bestellen kann, wenn die Braintree-Zahlungsmethode aktiviert ist.
exl-id: 8840aecb-21d9-4965-8c09-395e2d263aaa
feature: Admin Workspace, Native Luma Frontend Development, Orders, Payments
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# Der Administrator kann keine Bestellung/Neuanordnung erstellen, wenn die Braintree-Zahlung aktiviert ist

Dieser Artikel enthält einen Patch für das Problem Adobe Commerce 2.4.5, bei dem ein Admin-Benutzer keine Bestellungen erstellen oder für Kunden neu bestellen kann, wenn die Braintree-Zahlungsmethode aktiviert ist.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.4.5
* Adobe Commerce On-Premises 2.4.5
* Magento Open Source 2.4.5

## Problem

<u>Schritte zur Reproduktion</u>:

1. Die Braintree-Kernintegration wird verwendet (**Stores** > **Configurations** > **Sales** > **Payment Method** > **Braintree**).
1. Geben Sie mit der Luma-Storefront eine Bestellung auf.
1. Gehen Sie zu Admin UI > **Sales**.
1. Versuchen Sie entweder, eine neue Bestellung für einen Kunden zu erstellen, oder gehen Sie zu einer zuvor aufgegebenen Bestellung und klicken Sie auf **Neu**.

<u>Erwartetes Ergebnis</u>:

Admin-Benutzer können erfolgreich Bestellungen und Neubestellungen für Kunden erstellen, wenn die Braintree-Zahlungsmethode aktiviert ist.

<u>Tatsächliches </u>:

Admin-Benutzer können keine Bestellungen oder Neubestellungen für Kunden erstellen, wenn die Braintree-Zahlungsmethode aktiviert ist, und gibt den folgenden Fehler zurück:

```bash
report.CRITICAL: Error: Call to a member function getMethodInstance() on null in /app/vendor/paypal/module-braintree-core/Block/Form.php:174
```

## Ursache

Falsche Klassenabhängigkeiten (`vendor/paypal/module-braintree-core/Block/Form.php`)

## Lösung

Wenden Sie das in diesem Artikel vorgesehene Patch an.

## Fleck

Der Patch ist diesem Artikel beigefügt. Um ihn herunterzuladen, klicken Sie auf den folgenden Link:

[BUNDLE-3137-composer.patch.zip](assets/BUNDLE-3137-composer.patch.zip)

>[!NOTE]
>
>Zusätzlich für Händler, die mit Adobe Commerce in der Cloud-Infrastruktur arbeiten: Adobe hat die Fehlerbehebung in die Cloud-Patches für Commerce Version 1.0.18 aufgenommen. Siehe [Cloud-Patches für Commerce](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches) in unserer Entwicklerdokumentation, um Anweisungen zum Anwenden des neuesten Pakets zu erhalten.

### Kompatible Adobe Commerce-Versionen:

Der Patch wurde erstellt für:

* Adobe Commerce auf Cloud-Infrastruktur 2.4.5
* Adobe Commerce On-Premises 2.4.5
* Magento Open Source 2.4.5

>[!NOTE]
>
>Der Patch ist mit keiner anderen Adobe Commerce- und Magento Open Source-Version kompatibel.

## Anbringen des Pflasters

Anleitungen finden [ in unserer Support](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)Wissensdatenbank unter „So wenden Sie einen Composer-Patch an, der von Adobe bereitgestellt wird“.
