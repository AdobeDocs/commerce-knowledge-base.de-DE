---
title: Benutzer, die kein Produkt zum Warenkorb hinzufügen können, wenn in Länder zulassen nichts ausgewählt ist
description: Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce 2.4.4 mit PHP 8.1-Problem, bei dem Benutzer keine Produkte zum Warenkorb hinzufügen können, wenn die Option Länder zulassen deaktiviert ist.
exl-id: d05d1956-de23-496c-9234-c461a3cfdf36
feature: Orders, Products, Shopping Cart
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---

# Benutzer, die kein Produkt zum Warenkorb hinzufügen können, wenn in Länder zulassen nichts ausgewählt ist

Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce 2.4.4 mit PHP 8.1-Problem, bei dem Benutzer keine Produkte zum Warenkorb hinzufügen können, wenn die Option Länder zulassen deaktiviert ist.

## Betroffene Produkte und Versionen

Adobe Commerce 2.4.4 mit PHP 8.1

## Problem

Benutzer können keine Produkte zum Warenkorb hinzufügen, wenn die Option Länder zulassen deaktiviert ist.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich bei Commerce Admin an.
1. Wechseln Sie zu **Store** > **Konfiguration** > **Allgemein** > **Länderoptionen** .
1. Heben Sie die Auswahl aller Optionen im Feld **Länder zulassen** auf.
1. Klicken Sie auf **Konfiguration speichern** , um die Konfiguration zu speichern.
1. Gehen Sie zur Storefront und versuchen Sie, dem Warenkorb ein Produkt hinzuzufügen.

<u>Erwartetes Ergebnis:</u>

Sie können ein Produkt zum Warenkorb hinzufügen.

<u>Tatsächliches Ergebnis:</u>

Sie können dem Warenkorb kein Produkt hinzufügen. Sie erhalten den folgenden Konsolenfehler:

```bash
Failed to load resource: the server responded with a status of 400 (Bad Request)
customer-data.js:87 Uncaught Error: [object Object]
    at Object.<anonymous> (customer-data.js:87:23)
    at fire (jquery.js:3500:50)
    at Object.fireWith [as rejectWith] (jquery.js:3630:29)
    at done (jquery.js:9798:30)
    at XMLHttpRequest.<anonymous> (jquery.js:10057:37)
```

## Ursache

Die Adobe Commerce-Konfiguration ruft `null` ab, wenn in einer Multiselect-Konfiguration keine Elemente ausgewählt sind. Diese Konfiguration, wenn sie in PHP-Versionen vor 8.1 erfolgreich weiterverarbeitet wurde. In PHP 8.1 funktioniert es jedoch nicht richtig, da die Fehler durch die &quot;[Deprecate&quot;-Übergabe von null an nicht nullbare Argumente der internen Funktionen in PHP 8.1](https://wiki.php.net/rfc/deprecate_null_to_scalar_internal_arg) verursacht werden.

## Lösungen

Um das Problem zu beheben, wenden Sie den folgenden Patch an:

[AC-2655_2.4.4.patch.zip](assets/AC-2655_2.4.4.patch.zip)

## Anwenden des Pflasters

Anweisungen finden Sie unter [Anwenden eines von Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) bereitgestellten Composer-Patches in unserer Support-Wissensdatenbank.

## Nützliche Links

[Wenden Sie benutzerdefinierte Patches auf Adobe Commerce in der Cloud-Infrastruktur an](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.
