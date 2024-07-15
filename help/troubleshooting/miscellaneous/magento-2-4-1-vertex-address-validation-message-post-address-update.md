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

Aktivieren Sie die **Vertex-Adressenbereinigung**. Anweisungen finden Sie unter [Konfigurieren der Bereinigung der Storefront-Adresse](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/vertex-address-cleansing-different-addresses-not-allowed.html) in unserem Benutzerhandbuch.

<u>Zu reproduzierende Schritte:</u>

1. Erstellen Sie ein Konto und melden Sie sich an.
1. Fügen Sie dem Warenkorb ein Element hinzu, indem Sie auf **Zum Warenkorb hinzufügen** klicken. Klicken Sie auf das Warenkorbsymbol und dann auf **Fahren Sie mit dem Checkout fort**.
1. Geben Sie eine gültige Adresse in das Feld **Versandadresse** ein.
1. Aktivieren Sie eine der Optionen unter **Versandmethoden**. Klicken Sie dann auf **Weiter**.
1. Wenn bei der Überprüfung der Adresse andere Adressinformationen angezeigt werden, klicken Sie auf **Adresse aktualisieren** und dann auf **Weiter**.
1. Deaktivieren Sie das Kontrollkästchen **Meine Abrechnungs- und Lieferadresse sind dieselben**.

<u>Erstes Szenario:</u>

Führen Sie die obigen [ sechs Schritte ](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md#first_sixth) aus und dann:

1. Geben Sie eine neue gültige Rechnungsadresse ein.
1. Klicken Sie auf die Schaltfläche **Aktualisieren** . Es wird die Nachricht/der Vorschlag wie folgt angezeigt: *Die Adresse ist ungültig.* Dies folgt mit einem Adressenvorschlag wie: *Postcode : XXXXX- XXXX Street : XXX City street XXX*
1. Klicken Sie auf die Schaltfläche **Aktualisieren** (klicken Sie nicht auf die Schaltfläche **Adresse aktualisieren** des Vorschlags für eine Adresse im Text).
1. Klicken Sie auf die Schaltfläche **Bearbeiten** der aktualisierten Abrechnungsadresse.
1. Wählen Sie die Adresse aus der Dropdown-Liste Adresse aus.
1. Klicken Sie auf die Schaltfläche **Aktualisieren** .

<u>Erwartetes Ergebnis:</u>

Die alte Validierungsmeldung/-empfehlung wird entfernt.

<u>Tatsächliches Ergebnis:</u>

Die Validierungsmeldung/Empfehlung *&quot;Wir haben keine gültige Postleitzahl gefunden: XXXXX-XXXX Street: XXX City street XXX&quot;* Meldung ist **NOT** entfernt. Dasselbe Problem tritt auf, wenn Sie eine ungültige Adresse in das Formular eingeben.

<u>Zweites Szenario:</u>

Führen Sie die obigen [ sechs Schritte ](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md#first_sixth) aus und dann:

1. Füllen Sie das Adressformular mit einer gültigen Adresse aus.
1. Klicken Sie auf die Schaltfläche **Aktualisieren** . Es wird die Nachricht/der Vorschlag wie folgt angezeigt: *Die Adresse ist ungültig.* Dies folgt mit einem Adressenvorschlag wie: *Postcode : XXXXX-XXXX Street : XXX City street XXX*.
1. Klicken Sie auf die Schaltfläche **Aktualisieren** (klicken Sie nicht auf die Schaltfläche **Adresse aktualisieren** des Vertex-Adressenvorschlags).
1. Überprüfen Sie, ob die Dropdown-Liste ***Meine Abrechnungs- und Lieferadresse dieselbe ist.***

<u>Erwartetes Ergebnis:</u>

Die alte Validierungsmeldung/-empfehlung wird entfernt.

<u>Tatsächliches Ergebnis:</u>

Die Validierungsmeldung/-vorschlag *&quot;Wir haben keine gültige Postleitzahl gefunden: Die Meldung XXXXX-XXXX Street XXX City street XXX&quot;* ist **NOT** entfernt. Dasselbe Problem tritt auf, wenn Sie eine ungültige Adresse in das Formular eingeben.

## Verwandtes Lesen in unserer Wissensdatenbank:

[Bekanntes Problem in Adobe Commerce 2.3.6, 2.4.0-p1 und 2.4.1: Anmeldung bei dotdigital nicht möglich, wenn Konto aktiviert ist](/help/troubleshooting/miscellaneous/magento-2-3-6-2-4-0-p1-2-4-1-known-issue-dotdigital-login.md)
