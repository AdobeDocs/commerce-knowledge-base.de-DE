---
title: MwSt-Nummer kann nicht validiert werden - Adobe Commerce in Cloud-Infrastruktur
description: Dieser Artikel enthält einen Patch für das Problem, bei dem bei der Überprüfung der MwSt-Nummer ein Fehler auftritt.
exl-id: 9868e888-bad8-4823-acab-4b3804933cb0
feature: Cloud, Customer Service, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# MwSt-Nummer kann nicht validiert werden - Adobe Commerce in Cloud-Infrastruktur

Dieser Artikel enthält einen Patch für das Problem, bei dem bei der Überprüfung der MwSt-Nummer ein Fehler auftritt.

## Betroffene Produkte und Versionen

Alle lokalen Adobe Commerce- und Adobe Commerce-Versionen von Cloud-Infrastruktur bis 2.3.6 (einschließlich 2.3.5-p1) waren betroffen, einschließlich der bereits veröffentlichten Versionen p1 und p2. Dazu gehören:

* 2.3.5-p1
* 2,3,5
* 2.3.4 - 2.3.4 - p2
* 2.3.3 - 2.3.3 - p1
* 2.3.2 -2.3.2-p2
* 2.0.0 - 2.3.1

## Problem

<u>Zu reproduzierende Schritte:</u>

1. Wechseln Sie zu **Stores** > **Konfiguration** > **Kunden** > **Kundenkonfiguration** > **Neue Kontooptionen erstellen** und legen Sie **Automatische Zuweisung aktivieren** auf **Kundengruppe** auf *Ja* fest.
1. Wechseln Sie zu **Allgemein** > **Store-Informationen** > und legen Sie ein gültiges Land und eine gültige MwSt.-Nummer fest.
1. Klicken Sie auf **MwSt.-Nummer überprüfen**.

<u>Erwartetes Ergebnis:</u>

Die Validierung ist erfolgreich.

<u>Tatsächliches Ergebnis:</u>

Der folgende Fehler wird angezeigt: &quot;*Fehler bei Überprüfung der MwSt.-Nummer.*&quot;

## Lösung

Wenden Sie den in diesem Artikel angegebenen [Patch](assets/MDVA-27623_EE_2.3.2-p2_COMPOSER_v1.patch.zip) an.

## Patch

Der Patch ist an diesen Artikel angehängt. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link:

[MDVA-27623\_EE\_2.3.2-p2\_COMPOSER\_v1.patch](assets/MDVA-27623_EE_2.3.2-p2_COMPOSER_v1.patch.zip)

## Anwenden des Pflasters

Anweisungen finden Sie unter [Anwenden eines von Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) bereitgestellten Composer-Patches.

## Attached Files
