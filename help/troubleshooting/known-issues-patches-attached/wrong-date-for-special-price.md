---
title: Falsches Datum für Sonderpreis
description: Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce 2.2.2-Problem, das damit zusammenhängt, dass das Produktspezialpreisdatum "ab"falsch ist, wenn der Wert durch den Administrator geändert wird, dessen Gebietsschema für die Benutzeroberfläche unterschiedlich ist.
exl-id: fc109550-951e-4900-97e3-4ff3e7e5a395
feature: Orders, Personalization, User Account
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# Falsches Datum für Sonderpreis

Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce 2.2.2-Problem, das damit zusammenhängt, dass das Produktspezialpreisdatum &quot;ab&quot;falsch ist, wenn der Wert durch den Administrator geändert wird, dessen Gebietsschema für die Benutzeroberfläche unterschiedlich ist.

## Problem

Wenn Sie den Sonderpreis für ein Produkt festlegen/ändern, werden das aktuelle Datum und die aktuelle Uhrzeit in der Datenbank als Wert für `special_from_date` -Attribut (nicht sichtbar beim Bearbeiten eines Produkts). Wenn Sie den Sonderpreis bearbeiten und Ihr Admin-Benutzerkonto auf ein anderes Gebietsschema der Benutzeroberfläche festgelegt ist, kann ein falscher Wert auf `special_from_date` aufgrund der Probleme beim Parsen des Datumsformats für verschiedene Gebietsschemas.

<u>Zu reproduzierende Schritte</u>:

Voraussetzungen: Das Gebietsschema des Admin-Benutzers ist Englisch (USA).

1. Melden Sie sich bei Commerce Admin an.
1. Gehen Sie zu den Einstellungen für das Admin-Benutzerkonto .
1. Setzen Sie &quot;Interface Locale&quot;auf Ukrainisch.
1. Klicks **Konto speichern**.
1. Navigieren Sie zu **Katalog** > **Produkt**.
1. Wählen Sie ein beliebiges Produkt aus.
1. Klicken Sie auf der Produktseite auf **Erweiterte Preise**.
1. Fügen Sie einen Sonderpreis hinzu.
1. Speichern Sie das Produkt.
1. Wiederholen Sie die Schritte 7 bis 9.
1. Navigieren Sie zu **System** > **Aktionsprotokolle**.
1. Überprüfen Sie das Protokoll auf Produktaktualisierung.

<u>Erwartete Ergebnisse</u>:

Das Startdatum für den Sonderpreis sollte das aktuelle Datum sein.

<u>Tatsächliche Ergebnisse</u>:

Das Startdatum für den Sonderpreis ist ein Datum, das einige Jahre in der Zukunft liegt und verhindert, dass der Sonderpreis aktiv ist.

## Lösung

Durch Anwendung des Patches wird verhindert, dass das Problem erneut auftritt. Um die Daten für die Produkte zu korrigieren, bei denen das Datum falsch festgelegt wurde, setzen Sie den Sonderpreis nach der Anwendung des Pflasters neu.

## Patch

Der Patch ist an diesen Artikel angehängt. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link:

[MDVA-11605\_EE\_2.2.2\_COMPOSER\_v1.patch herunterladen](assets/MDVA-11605_EE_2.2.2_COMPOSER_v1.patch.zip)

### Kompatible Adobe Commerce-Versionen:

Der Patch wurde für erstellt:

* Adobe Commerce (alle Bereitstellungsmethoden) 2.2.2

Der Patch ist auch mit den folgenden Adobe Commerce-Versionen und -Editionen kompatibel (löst das Problem jedoch möglicherweise nicht):

* Adobe Commerce vor Ort 2.1.0-2.1.18, 2.2.0-2.2.5
* Adobe Commerce auf Cloud-Infrastruktur 2.1.11-2.1.18, 2.2.0-2.2.5

## Anwenden des Pflasters

Siehe [Anwenden eines von Adobe Commerce bereitgestellten Komponentenpatches](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) für Anweisungen.

## Attached Files
