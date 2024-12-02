---
title: 'Adobe Commerce 2.3.6, 2.4.0-p1, 2.4.1 Bekanntes Problem: dotdigital login'
description: In diesem Artikel wird ein bekanntes Problem mit Adobe Commerce 2.3.6, 2.4.0-p1 und 2.4.1 beschrieben, bei dem es nicht möglich ist, sich über das Admin Panel bei [dotdigital](https://dotdigital.com/) anzumelden, wenn das digitale Konto aktiviert ist.
exl-id: 427d895c-8c03-4ced-813a-eeaa67f1d1f0
feature: Configuration
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# Adobe Commerce 2.3.6, 2.4.0-p1, 2.4.1 Bekanntes Problem: dotdigital login

In diesem Artikel wird ein bekanntes Problem mit Adobe Commerce 2.3.6, 2.4.0-p1 und 2.4.1 beschrieben, bei dem es nicht möglich ist, sich über das Admin Panel bei [dotdigital](https://dotdigital.com/) anzumelden, wenn das digitale Konto aktiviert ist.

## Betroffene Produkte und Versionen

* Adobe Commerce über Cloud-Infrastruktur und Adobe Commerce On-Premise 2.3.6 (nur Safari-Browser)
* Adobe Commerce für Cloud-Infrastruktur und Adobe Commerce On-Premise 2.4.0-p1 (nur Safari-Browser)
* Adobe Commerce für Cloud-Infrastruktur und Adobe Commerce On-Premise 2.4.1 (nur Safari-Browser)

## Problem

<u>Voraussetzungen</u>:

1. dotdigital -Konto vorhanden ist.
1. In Adobe Commerce sind gültige dotdigital-API-Anmeldeinformationen vorhanden.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zu **Stores** > **Konfiguration** > **DOTDIGITAL** > **Chat-Einstellungen** > **Aktiviert** ist auf *Ja* eingestellt.
1. Klicken Sie auf **Konfigurieren** in **Chat-Widget konfigurieren** oder **Chat-Teams konfigurieren** .

<u>Erwartete Ergebnisse</u>:

Die Seite mit den Chat-Einstellungen sollte erfolgreich über das Admin Panel geöffnet werden.

<u>Tatsächliche Ergebnisse</u>:

Anmeldung bei dotdigital nicht möglich.

## Lösung

Problemumgehung: Verwenden Sie für diese spezielle Situation einen alternativen Browser zu Safari.

## Verwandte Informationen

[Bekanntes Problem mit Adobe Commerce 2.4.1 - Testadresse, die nicht mit verschiedenen Versand-/Rechnungsadressen validiert wurde](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md) in unserer Support-Wissensdatenbank.
