---
title: Der Administrator kann keine Bestellung/Neuanordnung erstellen, wenn die Braintree-Zahlung aktiviert ist
description: Dieser Artikel enthält einen Patch für die Adobe Commerce-Ausgabe 2.4.5, in der ein Admin-Benutzer keine Bestellungen erstellen und keine Neubestellungen für Kunden erstellen kann, wenn die Braintree-Zahlungsmethode aktiviert ist.
exl-id: 8840aecb-21d9-4965-8c09-395e2d263aaa
feature: Admin Workspace, Native Luma Frontend Development, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# Der Administrator kann keine Bestellung/Neuanordnung erstellen, wenn die Braintree-Zahlung aktiviert ist

Dieser Artikel enthält einen Patch für die Adobe Commerce-Ausgabe 2.4.5, in der ein Admin-Benutzer keine Bestellungen erstellen und keine Neubestellungen für Kunden erstellen kann, wenn die Braintree-Zahlungsmethode aktiviert ist.

## Betroffene Produkte und Versionen

* Adobe Commerce in Cloud-Infrastruktur 2.4.5
* Adobe Commerce vor Ort 2.4.5
* Magento Open Source 2.4.5

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Die Core-Braintree-Integration wird verwendet (**Speicher** > **Konfigurationen** > **Verkauf** > **Zahlungsmethode** > **Braintree**).
1. Platzieren Sie eine Bestellung über die Storefront von Luma.
1. Wechseln Sie zu Admin-Benutzeroberfläche > **Vertrieb**.
1. Versuchen Sie entweder, eine neue Bestellung für einen Kunden zu erstellen, oder gehen Sie zu einer zuvor platzierten Bestellung und klicken Sie auf **Neu anordnen**.

<u>Erwartetes Ergebnis</u>:

Administratoren können bei Aktivierung der Braintree-Zahlungsmethode erfolgreich Bestellungen und Neubestellungen für Kunden erstellen.

<u>Tatsächliches Ergebnis</u>:

Admin-Benutzer können keine Bestellungen oder Neuaufträge für Kunden erstellen, wenn die Braintree-Zahlungsmethode aktiviert ist, und gibt den folgenden Fehler zurück:

```bash
report.CRITICAL: Error: Call to a member function getMethodInstance() on null in /app/vendor/paypal/module-braintree-core/Block/Form.php:174
```

## Ursache

Falsche Klassenabhängigkeiten (`vendor/paypal/module-braintree-core/Block/Form.php`)

## Lösung

Wenden Sie den in diesem Artikel bereitgestellten Patch an.

## Patch

Der Patch ist an diesen Artikel angehängt. Um es herunterzuladen, klicken Sie auf den folgenden Link:

[BUNDLE-3137-composer.patch.zip](assets/BUNDLE-3137-composer.patch.zip)

>[!NOTE]
>
>Zusätzlich zu Adobe Commerce für Cloud-Infrastruktur-Händler: Adobe hat die Fehlerbehebung in den Cloud-Patches für Commerce-Version 1.0.18 enthalten. Anweisungen zum Anwenden des neuesten Pakets finden Sie in der Entwicklerdokumentation unter [Cloud-Patches für Commerce-Versionshinweise](https://devdocs.magento.com/cloud/release-notes/mcp-release-notes.html) .

### Kompatible Adobe Commerce-Versionen:

Der Patch wurde für erstellt:

* Adobe Commerce in Cloud-Infrastruktur 2.4.5
* Adobe Commerce vor Ort 2.4.5
* Magento Open Source 2.4.5

>[!NOTE]
>
>Der Patch ist nicht mit anderen Adobe Commerce- und Magento Open Source-Versionen und -Editionen kompatibel.

## Anwenden des Pflasters

Anweisungen finden Sie unter [Anwenden eines von Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) bereitgestellten Composer-Patches in unserer Support-Wissensdatenbank.
