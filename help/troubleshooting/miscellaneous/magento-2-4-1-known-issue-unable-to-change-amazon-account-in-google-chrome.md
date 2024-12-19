---
title: 'Adobe Commerce 2.4.1 Problem: Amazon-Konto kann in Chrome nicht geändert werden'
description: In diesem Artikel wird ein bekanntes Adobe Commerce 2.4.1-Problem beschrieben, bei dem Kundinnen und Kunden bei den zuvor verwendeten Amazon-Konten angemeldet werden, anstatt zur Anmeldung vorgeschlagen zu werden, wenn sie beim Checkout Amazon Pay verwenden.
exl-id: 8acffe99-b3ec-4b45-9434-61b66e963838
feature: Customer Service
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# Adobe Commerce 2.4.1 Problem: Amazon-Konto kann in Chrome nicht geändert werden

In diesem Artikel wird ein bekanntes Adobe Commerce 2.4.1-Problem beschrieben, bei dem Kundinnen und Kunden bei den zuvor verwendeten Amazon-Konten angemeldet werden, anstatt zur Anmeldung vorgeschlagen zu werden, wenn sie beim Checkout Amazon Pay verwenden.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premises 2.4.1
* Adobe Commerce auf Cloud-Infrastruktur 2.4.1

## Problem

Kunden werden bei den zuvor verwendeten Amazon-Konten angemeldet, anstatt zur Anmeldung vorgeschlagen zu werden, wenn sie während des Checkouts Amazon Pay verwenden.

<u>Schritte zur Reproduktion:</u>

1. Fügen Sie in der Storefront einen beliebigen Artikel zum Warenkorb hinzu und fahren Sie mit dem Gast-Checkout fort.
1. Klicken Sie auf die Schaltfläche **Amazon Pay**. Amazon.com Anmelde-Popup wird angezeigt.
1. Melden Sie sich beim Amazon-Konto an.
1. Wählen Sie eine Adresse aus und klicken Sie auf **Weiter**.
1. Wählen Sie die Zahlungsmethode aus.
1. Klicken Sie **Bestellung aufgeben**.
1. Gehen Sie zurück zur Startseite und melden Sie sich beim Store-Konto an.
1. Fügen Sie einen beliebigen Artikel erneut zum Warenkorb hinzu und fahren Sie mit dem Checkout fort.
1. Klicken Sie auf die Schaltfläche **Amazon Pay**.

<u>Tatsächliches Ergebnis:</u>

Sie werden automatisch wieder in das zuvor verwendete (Schritt 3) Amazon-Konto eingeloggt.

<u>Erwartetes Ergebnis:</u>

Amazon.com Anmelde-Popup erscheint und Sie können sich anmelden oder ein neues Konto für Amazon Pay erstellen.

## Ursache

Das Problem kann in einer der folgenden Situationen auftreten:

* Wenn der `SameSite` Cookie-Wert `LAX` ist, wird das Cookie nicht im Rahmen von Aufrufen von Drittanbietern gesendet.
* Die Inhaltsblockierungsfunktion von Mozilla Firefox verhindert, dass Drittanbieter die Aktivitäten von Browser-Benutzern verfolgen, indem sie die Verwendung von Skripten und Client-seitigen Speichermechanismen blockieren. Firefox verwendet einen externen Anbieter, Disconnect.me , um eine Liste der Tracking-Sites bereitzustellen, die blockiert werden sollen. Amazon Pay verwendet einen iframe auf einer Website eines Drittanbieters, um nach der Anmeldung ein Zugriffstoken zurückzugeben und Widget für Adresse und Brieftasche zu rendern. Mit der Inhaltsblockierungsfunktion werden Amazon Pay iFrame-Ladeanfragen als Tracking-Anfragen von Drittanbietern betrachtet und blockiert, sodass der Käufer nicht mit dem Checkout fortfahren kann.
* Jede Situation, in der Drittanbieter-Cookies oder JS vom Browser explizit blockiert werden.

## Lösung

Stellen Sie sicher, dass Amazon Pay iFrame-Anforderungen nicht von Browsern blockiert werden.
