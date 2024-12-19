---
title: Von der Server-E-Mail-Adresse gesendete Auftrags-E-Mail
description: Dieser Artikel enthält einen Patch für das bekannte Problem Adobe Commerce on Cloud Infrastructure 2.2.4 im Zusammenhang mit E-Mails zu Bestellungen, die von der Server-E-Mail-Adresse gesendet werden.
exl-id: f32e0c09-e19e-4269-bbba-0533d74a7f49
feature: Communications
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# Von der Server-E-Mail-Adresse gesendete Auftrags-E-Mail

Dieser Artikel enthält einen Patch für das bekannte Problem Adobe Commerce on Cloud Infrastructure 2.2.4 im Zusammenhang mit E-Mails zu Bestellungen, die von der Server-E-Mail-Adresse gesendet werden.

## Problem

Bestätigungs-E-Mails für Bestellungen werden von der E-Mail-Adresse des Apache-Servers gesendet. Andere E-Mails (vergessenes Kennwort usw.) werden von den konfigurierten E-Mail-Adressen gesendet.

<u>Schritte zur Reproduktion</u>:

1. Geben Sie eine Bestellung auf **wenn das Kontrollkästchen „Bestellbestätigung senden** aktiviert ist.
1. E-Mail überprüfen.

<u>Erwartetes Ergebnis</u>:

Die E-Mail wurde von der in Adobe Commerce konfigurierten Versandadresse gesendet.

<u>Tatsächliches </u>:

Die E-Mail wurde von der E-Mail-Adresse gesendet, die im verwendeten Apache-Server konfiguriert ist.

## Fleck

Der Patch ist diesem Artikel beigefügt. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link:

[MDVA-10993\_EE\_2.2.4\_v1.composer.patch herunterladen](assets/MDVA-10993_EE_2.2.4_v1.composer.patch.zip)

### Kompatible Adobe Commerce-Versionen:

Der Patch wurde erstellt für:

* Adobe Commerce auf Cloud-Infrastruktur 2.2.4

Der Patch ist auch mit den folgenden Adobe Commerce-Versionen und -Editionen kompatibel (kann das Problem jedoch nicht beheben):

* Adobe Commerce auf Cloud-Infrastruktur 2.2.5
* Adobe Commerce auf Cloud-Infrastruktur 2.2.6
* Adobe Commerce auf Cloud-Infrastruktur 2.2.7
* Adobe Commerce auf Cloud-Infrastruktur 2.2.8
* Adobe Commerce On-Premises 2.2.4
* Adobe Commerce On-Premises 2.2.5
* Adobe Commerce On-Premises 2.2.6
* Adobe Commerce On-Premises 2.2.7
* Adobe Commerce On-Premises 2.2.8
* Adobe Commerce On-Premises 2.3.0

## Anbringen des Pflasters

Anweisungen finden Sie unter [So wenden Sie einen von Adobe bereitgestellten Composer-Patch ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) unserer Support-Wissensdatenbank an.

## Angehängte Dateien
