---
title: Magento Order Management System (OMS) für Adobe Commerce-Verarbeitungsfehler
description: Dieser Artikel bietet eine Lösung für das Problem, wenn Sie einen "getMode()"-Fehler in der CLI erhalten, der "bin/magento oms:messages:process"im Magento Order Management System (OMS) für Adobe Commerce ausführt.
exl-id: 83089465-f810-4a3b-bdb6-4720b44f0b49
feature: System
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# Magento Order Management System (OMS) für Adobe Commerce-Verarbeitungsfehler

Dieser Artikel bietet eine Lösung für das Problem, wenn in der CLI, in der `bin/magento oms:messages:process` im Magento Order Management System (OMS) für Adobe Commerce ausgeführt wird, ein `getMode()` -Fehler ausgegeben wird.

## Betroffene Produkte und Versionen

Dieser Fehler tritt bei der Verwendung der MCOM Connector-Versionen 3.1.1 und 3.2.0 auf. Es wurde in MCOM Connector 3.3.0 behoben. Sie ist nicht spezifisch für eine MDC- oder MOM-Version.

## Problem

Beim Ausführen des folgenden Befehls in der CLI:

`bin/magento oms:messages:process`

In der CLI wird eine Fehlermeldung ausgegeben, die der folgenden ähnelt:

```
<project-id>@<project-id>:~$ php bin/magento oms:messages:process

Processing messages...

PHP Fatal error:Uncaught Error: Call to a member function getMode()
on null in /app/<project-id>/vendor/magento/module-inventory-message-bus/Handler/OnAggregateStockUpdatedSubscriber.php:64

Stack trace:

  #0 [internal function]: Magento\InventoryMessageBus\Handler\OnAggregateStockUpdatedSubscriber->onUpdated(Object(Magento\InventoryMessageBus\Model\Event\OnAggregateStockUpdated))

  #1 /app/<project-id>/vendor/magento/module-service-bus/Message/SingleMessageProcessor.php(81):
  call_user_func(Array, Object(Magento\InventoryMessageBus\Model\Event\OnAggregateStockUpdated))

  #2 [internal function]: Magento\ServiceBus\Message\SingleMessageProcessor->Magento\ServiceBus\Message\\{closure}(Array)

  #3 /app/<project-id>/vendor/magento/module-service-bus/Message/SingleMessageProcessor.php(86):
  array_map(Object(Closure), Array)

  #4 /app/<project-id>/vendor/magento/module-service-bus/Message/Processor.php(110):
  Magento\ServiceBus\Message\SingleMessageProcessor->process(Object(Magento\CommonMessageBus\Message\Message))

  #5 /app/t in /app/<project-id>/vendor/magento/module-inventory-message-bus/Handler/OnAggregateStockUpdatedSubscriber.php
  on line 64
```

## Ursache

Â
Dies tritt auf, wenn der Connector versucht, `magento.inventory.source_management` -Nachrichten zu verarbeiten. Der Connector versucht, diese Nachrichten so zu verarbeiten, als wären sie eine `magento.inventory.source_stock_management.update` -Meldung, für die kein Moduswert erforderlich ist. Da in den `magento.inventory.source_mangement` -Nachrichten kein Modus vorhanden ist, tritt der Fehler auf.

## Lösung

Um das Problem zu beheben, führen Sie die folgende [!DNL SQL] -Anweisung in der CLI aus, die alle Datensätze in der `mcom_api_messages` -Tabelle löscht:

`delete from mcom_api_messages;`

## Verwandte Informationen

* OMS Docs [OMS Connector-Setup-Tutorial](https://commerce-docs.github.io/oms-documentation-archive/integration/connector/setup-tutorial/)
* [Best Practices für die Änderung von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Playbook für die Commerce-Implementierung
