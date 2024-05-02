---
title: E-Mail-Adresse des Servers bestellen
description: Diese Artikel enthalten einen Patch für das bekannte Adobe Commerce-Problem in der Cloud-Infrastruktur 2.2.4, das sich auf die E-Mail-Adresse des Servers bezieht, über die E-Mails bestellt werden.
exl-id: f32e0c09-e19e-4269-bbba-0533d74a7f49
feature: Communications
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# E-Mail-Adresse des Servers bestellen

Diese Artikel enthalten einen Patch für das bekannte Adobe Commerce-Problem in der Cloud-Infrastruktur 2.2.4, das sich auf die E-Mail-Adresse des Servers bezieht, über die E-Mails bestellt werden.

## Problem

Bestellbestätigungs-E-Mails werden von der Apache-Server-E-Mail-Adresse gesendet. Andere E-Mails (Kennwort vergessen usw.) werden von den konfigurierten E-Mail-Adressen gesendet.

<u>Zu reproduzierende Schritte</u>:

1. Platzieren Sie eine Bestellung bei der **Bestellbestätigung senden** aktiviert ist.
1. Prüfen Sie E-Mail.

<u>Erwartetes Ergebnis</u>:

Die E-Mail wurde von der von Adobe Commerce konfigurierten Versandadresse gesendet.

<u>Tatsächliches Ergebnis</u>:

Die E-Mail wurde von der E-Mail-Adresse gesendet, die auf dem verwendeten Apache-Server konfiguriert wurde.

## Patch

Der Patch ist an diesen Artikel angehängt. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link:

[MDVA-10993\_EE\_2.2.4\_v1.composer.patch herunterladen](assets/MDVA-10993_EE_2.2.4_v1.composer.patch.zip)

### Kompatible Adobe Commerce-Versionen:

Der Patch wurde für erstellt:

* Adobe Commerce in Cloud-Infrastruktur 2.2.4

Der Patch ist auch mit den folgenden Adobe Commerce-Versionen und -Editionen kompatibel (löst das Problem jedoch möglicherweise nicht):

* Adobe Commerce on Cloud Infrastructure 2.2.5
* Adobe Commerce on Cloud Infrastructure 2.2.6
* Adobe Commerce on Cloud Infrastructure 2.2.7
* Adobe Commerce on Cloud Infrastructure 2.2.8
* Adobe Commerce vor Ort 2.2.4
* Adobe Commerce vor Ort 2.2.5
* Adobe Commerce vor Ort 2.2.6
* Adobe Commerce vor Ort 2.2.7
* Adobe Commerce vor Ort 2.2.8
* Adobe Commerce vor Ort 2.3.0

## Anwenden des Pflasters

Anweisungen finden Sie unter [Anwenden eines von Adobe bereitgestellten Composer-Patches](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in unserer Wissensdatenbank.

## Attached Files
