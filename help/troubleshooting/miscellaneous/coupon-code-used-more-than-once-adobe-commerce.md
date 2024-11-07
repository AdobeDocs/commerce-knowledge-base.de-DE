---
title: Der Coupon für die einmalige Verwendung wird mehrmals verwendet, Adobe Commerce
description: Dieser Artikel bietet eine Lösung für das Problem, wenn Warenkorbpreisregelgutscheine nicht ordnungsgemäß funktionieren. Händler richten einen Gutschein für die einmalige Verwendung ein und Kunden können ihn mehrmals verwenden.
exl-id: 9c81de40-65a3-422d-9053-3c894b863a0a
feature: Orders
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# Der Coupon für die einmalige Verwendung wird mehrmals verwendet, Adobe Commerce

Dieser Artikel bietet eine Lösung für das Problem, wenn Warenkorbpreisregelgutscheine nicht ordnungsgemäß funktionieren. Händler richten einen Gutschein für die einmalige Verwendung ein und Kunden können ihn mehrmals verwenden.


## Betroffene Produkte und Versionen

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 und höher

## Problem

Händler richten einen Gutschein für die einmalige Verwendung ein und Kunden können ihn mehrmals verwenden.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie einen Gutschein und konfigurieren Sie den Gutschein für die einmalige Verwendung.
1. Fahren Sie mit dem Checkout fort.
1. Verwenden Sie den soeben erstellten Gutschein.
1. Fahren Sie mit dem Kassengang fort und verwenden Sie denselben Gutschein.

<u>Erwartetes Ergebnis</u>:

Der Gutschein kann nur einmal verwendet werden. Eine Meldung wird angezeigt: *Der Couponcode &quot;COUPON_NAME&quot;ist ungültig*.

<u>Tatsächliches Ergebnis</u>:

Der Gutschein kann mehrmals verwendet werden.


## Ursache

Merchants verfügen nicht über `sales.rule.update.coupon.usage` Verbraucherrechte, die zu unangemessenem Verhalten führen.

## Lösung

Fügen Sie den `sales.rule.update.coupon.usage` -Verbraucher zur Datei `app/etc/env.php` hinzu.

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

Ausführliche Anweisungen finden Sie unter [Verwalten von Nachrichtenwarteschlangen > Konfiguration](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/message-queues/manage-message-queues#configuration) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

[Übersicht über Nachrichtenwarteschlangen](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/message-queues/message-queue-framework) in unserer Entwicklerdokumentation.
