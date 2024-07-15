---
title: Fehlermeldung beim Hinzufügen von Sites zum Sicherheitsscan
description: Dieser Artikel bietet mögliche Lösungen für das Problem, wenn ein Benutzer keine Sites zum [Commerce Security Scan] hinzufügen kann (https://account.magento.com/scanner/dashboard/).
exl-id: 8d000ca4-b977-432d-bb26-6ea320067a40
feature: Cache, Compliance, Console, Security
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# Fehlermeldung beim Hinzufügen von Sites zum Sicherheitsscan

Dieser Artikel bietet mögliche Lösungen für das Problem, wenn ein Benutzer keine Sites zum [Commerce Security Scan](https://account.magento.com/scanner/dashboard/) hinzufügen kann.

## Betroffene Produkte und Versionen

* Adobe Commerce (alle Bereitstellungsmethoden und -versionen)
* Magento Open Source

## Problem

Benutzer können keine Sites zum [Commerce-Sicherheitsscan](https://account.magento.com/scanner/dashboard/) hinzufügen. Die folgende Fehlermeldung wird angezeigt, wenn versucht wird, eine Site hinzuzufügen: *Site kann nicht zum Scannen übermittelt werden.*

## Lösung

1. Stellen Sie sicher, dass die folgenden IP-Adressen nicht auf den Ports 80 und 443 blockiert werden:
   * 52 87 98 44
   * 34 196 167 176
   * 3 218 25 102

1. Der Bestätigungscode ist zeitabhängig. Wenn mehr als 30 Minuten vergangen sind, nachdem auf den Link **Site hinzufügen** geklickt wurde, ist der Code wahrscheinlich abgelaufen.
1. Vergessen Sie nicht, den Cache zu leeren und sicherzustellen, dass der Validierungscode im Quelltext der Startseite angezeigt wird. Der Bestätigungscode sollte entsprechend den HTML Markup-Spezifikationen eingefügt werden: HTML-Kommentar kann in den Seitentext eingefügt werden (wir empfehlen, ihn in den Fußzeilenabschnitt einzufügen); das META-Tag sollte sich nur im Kopfabschnitt befinden.
1. Bevor Sie auf **Bestätigungscode überprüfen** klicken, öffnen Sie die Entwicklerkonsole des Browsers, klicken Sie auf die Registerkarte **Netzwerk** und überprüfen Sie die Antwort von magento.com. Es sollte HTTP 200 (OK) sein und der Antworttext sollte ein JSON-Objekt enthalten.
1. Wenn der Antwort-Code HTTP 200 ist und der Antworttext ein JSON-Objekt ist und der `verified`-Eigenschaftswert `false` lautet, bedeutet dies, dass der Code nicht auf der Seite gefunden wird. Der Eigenschaftswert `details` sollte die Erklärung enthalten. Wenn der Store beispielsweise ein selbstsigniertes SSL-Zertifikat verwendet, tritt wahrscheinlich ein Verbindungsfehler auf.

Wenn Sie weiterhin keine Sites hinzufügen können, führen Sie die folgenden Schritte aus:

1. Fügen Sie einen weiteren HTML-Kommentar auf der Seite ein:

   ```HTML
   <!-- MAGEID:Your magento.com ID, EMAIL:your email address -->
   ```

1. Senden Sie ein Support-Ticket und geben Sie die folgenden Informationen ein:
   * Adobe Commerce Store-URL
   * MAGEID + Magento.com Kontoemail
   * Vorname + Nachname
   * Firmenname
   * Kommagetrennte Benachrichtigungs-E-Mail-Liste

## Verwandtes Lesen

* [Sicherheitsscan](https://docs.magento.com/user-guide/magento/security-scan.html) in unserem Benutzerhandbuch.
