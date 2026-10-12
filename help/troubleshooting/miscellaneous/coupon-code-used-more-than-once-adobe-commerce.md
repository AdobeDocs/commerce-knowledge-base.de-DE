---
title: Coupons zur einmaligen Verwendung werden mehrmals verwendet, Adobe Commerce
description: Dieser Artikel bietet eine Lösung für das Problem, wenn Gutscheine für Warenkorbpreisregeln nicht richtig funktionieren. Händler richten einen Gutschein für den einmaligen Gebrauch ein und Kunden können ihn mehrmals verwenden.
exl-id: 9c81de40-65a3-422d-9053-3c894b863a0a
feature: Orders
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 0%
---
# Coupons zur einmaligen Verwendung werden mehrmals verwendet, Adobe Commerce

Dieser Artikel bietet eine Lösung für das Problem, wenn Gutscheine für Warenkorbpreisregeln nicht richtig funktionieren. Händler richten einen Gutschein für den einmaligen Gebrauch ein und Kunden können ihn mehrmals verwenden.


## Betroffene Produkte und Versionen

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 und höher

## Problem

Händler richten einen Gutschein für den einmaligen Gebrauch ein und Kunden können ihn mehrmals verwenden.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie einen Gutschein und konfigurieren Sie den Gutschein für die einmalige Verwendung.
1. Zur Kasse gehen.
1. Verwenden Sie den soeben erstellten Gutschein.
1. Wechseln Sie erneut zum Checkout und verwenden Sie denselben Gutschein.

<u>Erwartetes Ergebnis</u>:

Der Gutschein kann nur einmal verwendet werden. Daraufhin wird eine Meldung angezeigt *„Der Couponcode „COUPON_NAME“ ist ungültig*.

<u>Tatsächliches </u>:

Der Gutschein kann mehrmals verwendet werden.


## Ursache

Händler haben `sales.rule.update.coupon.usage` Verbraucher nicht eingerichtet und in Betrieb, was zu unangemessenem Verhalten führt.

## Lösung

Fügen Sie den `sales.rule.update.coupon.usage` Verbraucher zur `app/etc/env.php` hinzu.

```php
...
    'cron_consumers_runner' =>
    array [
        'cron_run' => true,
        'max_messages' => 20000,
        'consumers' =>
        array [
            'sales.rule.update.coupon.usage'
        ]
    ],
...
```

Detaillierte Anweisungen finden Sie unter [Verwalten von Nachrichtenwarteschlangen > Konfiguration](https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/message-queues/manage-message-queues#configuration) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

[Übersicht über Message Queues](https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/message-queues/message-queue-framework) in unserer Entwicklerdokumentation.
