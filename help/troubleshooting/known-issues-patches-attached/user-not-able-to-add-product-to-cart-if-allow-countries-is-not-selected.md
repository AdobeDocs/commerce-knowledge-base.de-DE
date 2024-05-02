---
title: Benutzer, die kein Produkt zum Warenkorb hinzufügen können, wenn in Länder zulassen nichts ausgewählt ist
description: Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce 2.4.4 mit PHP 8.1-Problem, bei dem Benutzer keine Produkte zum Warenkorb hinzufügen können, wenn die Option Länder zulassen deaktiviert ist.
exl-id: d05d1956-de23-496c-9234-c461a3cfdf36
feature: Orders, Products, Shopping Cart
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
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
1. Navigieren Sie zu **Store** > **Konfiguration** > **Allgemein** > **Länderoptionen**
1. Aufheben der Auswahl aller Optionen unter **Länder zulassen** -Feld.
1. Klicks **Konfiguration speichern** , um die Konfiguration zu speichern.
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

Die Adobe Commerce-Konfiguration ruft ab `null` , wenn eine Mehrfachauswahl-Konfiguration keine ausgewählten Elemente enthält. Diese Konfiguration, wenn sie in PHP-Versionen vor 8.1 erfolgreich weiterverarbeitet wurde. In PHP 8.1 funktioniert es jedoch aufgrund der Fehler, die durch die &quot;[Veraltete Übergabe von null an nicht nullbare Argumente interner Funktionen in PHP 8.1](https://wiki.php.net/rfc/deprecate_null_to_scalar_internal_arg)&quot;.

## Lösungen

Um das Problem zu beheben, wenden Sie den folgenden Patch an:

[AC-2655_2.4.4.patch.zip](assets/AC-2655_2.4.4.patch.zip)

## Anwenden des Pflasters

Siehe [Anwenden eines von Adobe Commerce bereitgestellten Komponentenpatches](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in unserer Support-Wissensdatenbank für Anleitungen.

## Nützliche Links

[Anwenden benutzerdefinierter Patches auf Adobe Commerce in der Cloud-Infrastruktur](https://devdocs.magento.com/guides/v2.3/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.
