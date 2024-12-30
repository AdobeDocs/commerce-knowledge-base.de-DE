---
title: 'Bekanntes Problem in Adobe Commerce 2.3.6, 2.4.0-p1, 2.4.1: dotdigital login'
description: In diesem Artikel wird ein bekanntes Adobe Commerce 2.3.6-, 2.4.0-p1- und 2.4.1-Problem beschrieben, bei dem es nicht möglich ist, sich über das Admin-Bedienfeld bei [dotdigital](https://dotdigital.com/) anzumelden, wenn das dotdigital-Konto aktiviert ist.
exl-id: 427d895c-8c03-4ced-813a-eeaa67f1d1f0
feature: Configuration
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# Bekanntes Problem in Adobe Commerce 2.3.6, 2.4.0-p1, 2.4.1: dotdigital login

In diesem Artikel wird ein bekanntes Adobe Commerce 2.3.6-, 2.4.0-p1- und 2.4.1-Problem beschrieben, bei dem eine Anmeldung bei [dotdigital](https://dotdigital.com/) über das Admin Panel nicht möglich ist, wenn das dotdigital-Konto aktiviert ist.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur und Adobe Commerce On-Premises 2.3.6 (nur Safari-Browser)
* Adobe Commerce on Cloud Infrastructure und Adobe Commerce On-Premises 2.4.0-p1 (nur Safari-Browser)
* Adobe Commerce auf Cloud-Infrastruktur und Adobe Commerce On-Premises 2.4.1 (nur Safari-Browser)

## Problem

<u>Voraussetzungen</u>:

1. DotDigital-Konto vorhanden.
1. In Adobe Commerce sind gültige dotdigital API-Anmeldeinformationen vorhanden.

<u>Schritte zur Reproduktion</u>:

1. Gehen Sie zu **Stores** > **Configuration** > **DOTDIGITAL** > **Chat-Einstellungen** > **Enabled** ist auf *yes.*
1. Klicken Sie auf **Konfigurieren** in **Chat-Widget konfigurieren** oder **Chat-Teams konfigurieren**.

<u>Erwartete Ergebnisse</u>:

Die Seite mit den Chat-Einstellungen sollte erfolgreich über das Admin Panel geöffnet werden.

<u>Tatsächliche Ergebnisse</u>:

Anmeldung bei dotdigital nicht möglich.

## Lösung

Problemumgehung: Verwenden Sie für diese spezielle Situation einen alternativen Browser zu Safari.

## Verwandtes Lesen

[Bekanntes Problem mit Adobe Commerce 2.4.1 - Vertex-Adresse wird nicht mit verschiedenen Versand-/Rechnungsadressen ](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md) unserer Support-Wissensdatenbank validiert.
