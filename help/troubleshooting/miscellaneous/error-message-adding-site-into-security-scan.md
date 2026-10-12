---
title: Fehlermeldung beim Hinzufügen von Sites zur Sicherheitsprüfung
description: Dieser Artikel bietet mögliche Lösungen für das Problem, wenn Benutzende keine Websites zur [Commerce-Sicherheitsprüfung] hinzufügen können(https://account.magento.com/scanner/dashboard/).
exl-id: 8d000ca4-b977-432d-bb26-6ea320067a40
feature: Cache, Compliance, Console, Security
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
    internal-label: Compliance
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: c4af0798-d497-5e6b-8380-19812c26d00a
    internal-label: Console
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '367'
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

1. Fügen Sie einen weiteren HTML-Kommentar auf der Seite ein:

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

* [Security Scan](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/security/security-scan) in unserem Benutzerhandbuch.
