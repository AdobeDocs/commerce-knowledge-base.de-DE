---
title: Fehlermeldung beim Hinzufügen von Sites zur Sicherheitsprüfung
description: Dieser Artikel bietet mögliche Lösungen für das Problem, wenn Benutzende keine Websites zur [Commerce-Sicherheitsprüfung] hinzufügen können(https://account.magento.com/scanner/dashboard/).
exl-id: 8d000ca4-b977-432d-bb26-6ea320067a40
feature: Cache, Compliance, Console, Security
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# Fehlermeldung beim Hinzufügen von Sites zur Sicherheitsprüfung

Dieser Artikel bietet mögliche Lösungen für das Problem, wenn Benutzende keine Websites zur [Commerce-Sicherheitsprüfung hinzufügen können](https://account.magento.com/scanner/dashboard/).

## Betroffene Produkte und Versionen

* Adobe Commerce (alle Bereitstellungsmethoden und -versionen)
* Magento Open Source

## Problem

Der Benutzer kann keine Websites zur [Commerce-Sicherheitsprüfung hinzufügen](https://account.magento.com/scanner/dashboard/). Beim Versuch, eine Site hinzuzufügen, wird die folgende Fehlermeldung angezeigt: *Website kann nicht zum Scannen übermittelt werden.*

## Lösung

1. Stellen Sie sicher, dass die folgenden IP-Adressen an den Ports 80 und 443 nicht blockiert sind:
   * 52.87.98.44
   * 34.196.167.176
   * 3.218.25.102

1. Der Bestätigungscode ist zeitkritisch. Wenn mehr als 30 Minuten nach dem Klicken auf den Link **Website hinzufügen** vergangen sind, ist der Code wahrscheinlich abgelaufen.
1. Vergessen Sie nicht, den Cache zu bereinigen und stellen Sie sicher, dass der Validierungs-Code im Quelltext der Startseite angezeigt wird. Der Bestätigungs-Code sollte gemäß den HTML-Markup-Spezifikationen eingefügt werden: HTML-Kommentar kann in den Seitentext eingefügt werden (wir empfehlen, ihn in den Fußzeilenabschnitt einzufügen); das META-Tag sollte nur im Kopfabschnitt sein.
1. Bevor Sie auf **Bestätigungs-Code überprüfen** klicken, öffnen Sie die Entwicklerkonsole des Browsers, klicken Sie auf die Registerkarte **Netzwerk** und überprüfen Sie die Antwort von magento.com. Es sollte HTTP 200 (OK) sein und der Antworttext sollte ein JSON-Objekt enthalten.
1. Wenn der Antwort-Code HTTP 200 lautet und der Antworttext ein JSON-Objekt ist und der Wert der `verified`-Eigenschaft `false` ist, bedeutet dies, dass der Code nicht auf der Seite gefunden wird. Der Wert der `details`-Eigenschaft sollte die Erklärung enthalten. Wenn der Store beispielsweise ein selbstsigniertes SSL-Zertifikat verwendet, liegt wahrscheinlich ein Verbindungsfehler vor.

Wenn Sie weiterhin keine Sites hinzufügen können, führen Sie die folgenden Schritte aus:

1. Platzieren Sie einen weiteren HTML-Kommentar auf der Seite:

   ```HTML
   <!-- MAGEID:Your magento.com ID, EMAIL:your email address -->
   ```

1. Senden Sie ein Support-Ticket und geben Sie die folgenden Informationen ein:
   * Adobe Commerce Store-URL
   * MAGEID + Magento.com Konto-E-Mail
   * Vorname + Nachname
   * Firmenname
   * E-Mail-Benachrichtigungsliste, durch Kommata getrennt

## Verwandtes Lesen

* [Security Scan](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan) in unserem Benutzerhandbuch.
