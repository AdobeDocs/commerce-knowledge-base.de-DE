---
title: "Adobe Commerce 2.4.1-Problem: Amazon-Konto in Chrome kann nicht geändert werden"
description: In diesem Artikel wird ein bekanntes Problem mit Adobe Commerce 2.4.1 beschrieben, bei dem Kunden sich bei den zuvor verwendeten Amazon-Konten anmelden, anstatt sich anzumelden, wenn sie die Amazon-Zahlung während des Checkouts verwenden.
exl-id: 8acffe99-b3ec-4b45-9434-61b66e963838
feature: Customer Service
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# Problem mit Adobe Commerce 2.4.1: Amazon-Konto in Chrome kann nicht geändert werden

In diesem Artikel wird ein bekanntes Problem mit Adobe Commerce 2.4.1 beschrieben, bei dem Kunden sich bei den zuvor verwendeten Amazon-Konten anmelden, anstatt sich anzumelden, wenn sie die Amazon-Zahlung während des Checkouts verwenden.

## Betroffene Produkte und Versionen

* Adobe Commerce vor Ort 2.4.1
* Adobe Commerce in Cloud-Infrastruktur 2.4.1

## Problem

Kunden können sich bei den zuvor verwendeten Amazon-Konten anmelden, anstatt sich bei der Verwendung von Amazon Pay während des Checkout anzumelden.

<u>Zu reproduzierende Schritte:</u>

1. Fügen Sie in der Storefront einen Artikel zum Warenkorb hinzu und fahren Sie mit dem Checkout fort.
1. Klicken Sie auf die Schaltfläche **Amazon Pay** . Amazon.com Anmeldung wird angezeigt.
1. Melden Sie sich beim Amazon-Konto an.
1. Wählen Sie eine Adresse aus und klicken Sie auf **Weiter**.
1. Wählen Sie die Zahlungsmethode aus.
1. Klicken Sie auf **Bestellung platzieren**.
1. Gehen Sie zurück zur Startseite und melden Sie sich beim Store-Konto an.
1. Fügen Sie dem Warenkorb erneut einen Artikel hinzu und fahren Sie mit dem Checkout fort.
1. Klicken Sie auf die Schaltfläche **Amazon Pay** .

<u>Tatsächliches Ergebnis:</u>

Sie werden automatisch erneut beim zuvor verwendeten Amazon-Konto (Schritt 3) angemeldet.

<u>Erwartetes Ergebnis:</u>

Amazon.com Melden Sie sich in einem Popup an und Sie können sich anmelden oder ein neues Konto für Amazon Pay erstellen.

## Ursache

Das Problem kann in einer der folgenden Situationen auftreten:

* Wenn der Cookie-Wert `SameSite` den Wert `LAX` aufweist, wird das Cookie nicht als Teil von Aufrufen von Drittanbietern gesendet.
* Die Mozilla Firefox-Funktion zur Inhaltsblockierung verhindert, dass Drittanbieter die Aktivitäten von Browserbenutzern verfolgen, indem sie die Nutzung von Skripten und clientseitigen Speichermechanismen blockiert. Firefox verwendet einen externen Anbieter, &quot;Disconnect.me&quot;, um eine Liste der zu blockierenden Tracking-Sites bereitzustellen. Amazon Pay verwendet einen iframe auf einer Drittanbieter-Website, um nach der Anmeldung ein Zugriffstoken zurückzugeben und das Widget Adresse und Geldbörse anzuzeigen. Mit der Funktion zur Inhaltsblockierung werden iFrame-Ladeanfragen für Amazon Pay als Tracking-Anfragen von Drittanbietern betrachtet und blockiert, sodass der Käufer mit dem Checkout nicht fortfahren kann.
* Situationen, in denen Drittanbieter-Cookies oder JS explizit vom Browser blockiert werden.

## Lösung

Stellen Sie sicher, dass Amazon Pay iFrame-Anforderungen nicht von Browsern blockiert werden.
