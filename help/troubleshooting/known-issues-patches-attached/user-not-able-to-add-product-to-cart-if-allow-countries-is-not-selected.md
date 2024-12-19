---
title: Benutzende können kein Produkt in den Warenkorb legen, wenn in „Länder zulassen“ nichts ausgewählt ist.
description: Dieser Artikel enthält einen Patch für das bekannte Problem Adobe Commerce 2.4.4 mit PHP 8.1, bei dem Benutzende keine Produkte zum Warenkorb hinzufügen können, wenn die Option Länder zulassen deaktiviert ist.
exl-id: d05d1956-de23-496c-9234-c461a3cfdf36
feature: Orders, Products, Shopping Cart
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---

# Benutzende können kein Produkt in den Warenkorb legen, wenn in „Länder zulassen“ nichts ausgewählt ist.

Dieser Artikel enthält einen Patch für das bekannte Problem Adobe Commerce 2.4.4 mit PHP 8.1, bei dem Benutzende keine Produkte zum Warenkorb hinzufügen können, wenn die Option Länder zulassen deaktiviert ist.

## Betroffene Produkte und Versionen

Adobe Commerce 2.4.4 mit PHP 8.1

## Problem

Benutzende können keine Produkte in den Warenkorb legen, wenn die Option „Länder zulassen“ deaktiviert ist.

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich beim Commerce Admin an.
1. Wechseln Sie **Store** > **Configuration** > **General** > **country options**
1. Deaktivieren Sie alle Optionen im Feld **Länder zulassen**.
1. Klicken Sie **Konfiguration speichern** um die Konfiguration zu speichern.
1. Gehen Sie zur Storefront und versuchen Sie, ein Produkt zum Warenkorb hinzuzufügen.

<u>Erwartetes Ergebnis:</u>

Sie können ein Produkt zum Warenkorb hinzufügen.

<u>Tatsächliches Ergebnis:</u>

Sie können kein Produkt zum Warenkorb hinzufügen. Es wird der folgende Konsolenfehler angezeigt:

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

Die Adobe Commerce-Konfiguration ruft `null` ab, wenn in einer Mehrfachauswahl-Konfiguration keine ausgewählten Elemente vorhanden sind. Diese Konfiguration wird weiterverarbeitet, wenn sie in PHP-Versionen vor 8.1 erfolgreich weiterverarbeitet wurde. In PHP 8.1 funktioniert es jedoch aufgrund der Fehler, die durch &quot;[Deprecate übergibt null an nicht-löschbare Argumente interner Funktionen in PHP 8.1“ verursacht ](https://wiki.php.net/rfc/deprecate_null_to_scalar_internal_arg), nicht richtig.

## Lösungen

Um das Problem zu beheben, führen Sie den folgenden Patch durch:

[AC-2655_2.4.4.patch.zip](assets/AC-2655_2.4.4.patch.zip)

## Anbringen des Pflasters

Anweisungen [ Sie in unserer Support](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)Wissensdatenbank unter „Anwenden eines von Adobe Commerce bereitgestellten Composer-Patches“.

## Nützliche Links

[Wenden Sie benutzerdefinierte Patches auf Adobe Commerce in der Cloud-](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) an“ in unserer Entwicklerdokumentation.
