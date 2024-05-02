---
title: Adobe Commerce 2.4.1 Validierungsmeldung für Reklame-Adressen nach der Aktualisierung der Adresse
description: In diesem Artikel wird ein bekanntes Problem mit Adobe Commerce 2.4.1 beschrieben, bei dem die Überprüfung der Testadressen während des Zahlungsschritts nicht funktioniert, wenn eine Versandadresse verwendet wird, die sich von der Abrechnungsadresse unterscheidet. Das Problem soll in Adobe Commerce 2.4.2 behoben werden.
exl-id: c2abeb96-e837-4d16-92dd-82fea5661dd9
feature: Shipping/Delivery
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%

---

# Adobe Commerce 2.4.1 Validierungsmeldung für Reklame-Adressen nach der Aktualisierung der Adresse

In diesem Artikel wird ein bekanntes Problem mit Adobe Commerce 2.4.1 beschrieben, bei dem die Überprüfung der Testadressen während des Zahlungsschritts nicht funktioniert, wenn eine Versandadresse verwendet wird, die sich von der Abrechnungsadresse unterscheidet. Das Problem soll in Adobe Commerce 2.4.2 behoben werden.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premise 2.4.1 mit aktivierter Vertex-Integration
* Adobe Commerce in der Cloud-Infrastruktur 2.4.1 mit aktivierter Vertex-Integration

## Problem

Voraussetzungen:

Aktivieren **Reklamationsbereinigung**. Eine Anleitung finden Sie unter [Konfigurieren der Bereinigung der Storefront-Adresse](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/vertex-address-cleansing-different-addresses-not-allowed.html) in unserem Benutzerhandbuch.

<u>Zu reproduzierende Schritte:</u>

1. Erstellen Sie ein Konto und melden Sie sich an.
1. Hinzufügen eines Artikels zum Warenkorb durch Klicken auf **Zum Warenkorb hinzufügen**. Klicken Sie auf das Symbol Warenkorb und dann auf **Zur Kasse gehen**.
1. Geben Sie eine gültige Adresse in die **Versandadresse** -Feld.
1. Aktivieren Sie eine der Optionen unter **Versandmethoden**. Klicken Sie anschließend auf **Nächste**.
1. Wenn bei der Adressprüfung andere Adressinformationen vorgeschlagen werden, klicken Sie auf **Adresse aktualisieren** und klicken **Nächste**.
1. Deaktivieren Sie die **Meine Abrechnungs- und Lieferadresse sind identisch.** aktivieren.

<u>Erstes Szenario:</u>

Befolgen Sie die [über sechs Schritte](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md#first_sixth) und dann:

1. Geben Sie eine neue gültige Rechnungsadresse ein.
1. Klicken Sie auf **Aktualisieren** Schaltfläche. Sie zeigt die Nachricht/den Vorschlag wie folgt an: *Die Adresse ist ungültig.* Dies folgt mit einem Adressenvorschlag wie: *Postleitzahl: XXXXX- XXXX Street: XXX City street XXX*
1. Klicken Sie auf **Aktualisieren** Schaltfläche (klicken Sie nicht auf **Adresse aktualisieren** -Schaltfläche des Vorschlags für eine Adresse des Vertex).
1. Klicken Sie auf **Bearbeiten** Schaltfläche der aktualisierten Abrechnungsadresse.
1. Wählen Sie die Adresse aus der Dropdown-Liste Adresse aus.
1. Klicken Sie auf **Aktualisieren** Schaltfläche.

<u>Erwartetes Ergebnis:</u>

Die alte Validierungsmeldung/-empfehlung wird entfernt.

<u>Ergebnis:</u>

Überprüfungsmeldung/-vorschlag *&quot;Wir haben keine gültige Postleitzahl gefunden: XXXXX-XXXX Street: XXX City street XXX&quot;* Meldung ist **NOT** entfernt. Dasselbe Problem tritt auf, wenn Sie eine ungültige Adresse in das Formular eingeben.

<u>Zweites Szenario:</u>

Befolgen Sie die [über sechs Schritte](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md#first_sixth) und dann:

1. Füllen Sie das Adressformular mit einer gültigen Adresse aus.
1. Klicken Sie auf **Aktualisieren** Schaltfläche. Sie zeigt die Nachricht/den Vorschlag wie folgt an: *Die Adresse ist ungültig.* Dies folgt mit einem Adressenvorschlag wie: *Postleitzahl: XXXXX-XXXX Straße: XXX City Street XXX*.
1. Klicken Sie auf **Aktualisieren** Schaltfläche (klicken Sie nicht auf **Adresse aktualisieren** Schaltfläche der Empfehlung der vertex-Adresse).
1. Überprüfen Sie die ***Meine Abrechnungs- und Lieferadresse sind identisch.*** angezeigt.

<u>Erwartetes Ergebnis:</u>

Die alte Validierungsmeldung/-empfehlung wird entfernt.

<u>Ergebnis:</u>

Überprüfungsmeldung/-vorschlag *&quot;Wir haben keine gültige Postleitzahl gefunden: XXXXX-XXXX Street XXX City street XXX&quot;* Meldung ist **NOT** entfernt. Dasselbe Problem tritt auf, wenn Sie eine ungültige Adresse in das Formular eingeben.

## Verwandtes Lesen in unserer Wissensdatenbank:

[Bekanntes Problem in Adobe Commerce 2.3.6, 2.4.0-p1 und 2.4.1: Anmeldung bei dotdigital nicht möglich, wenn Konto aktiviert ist](/help/troubleshooting/miscellaneous/magento-2-3-6-2-4-0-p1-2-4-1-known-issue-dotdigital-login.md)
