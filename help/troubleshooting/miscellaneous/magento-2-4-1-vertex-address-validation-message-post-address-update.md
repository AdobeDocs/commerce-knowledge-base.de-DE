---
title: Adobe Commerce 2.4.1 Vertex-Adressvalidierungsmeldung nach Aktualisierung der Adresse
description: In diesem Artikel wird ein bekanntes Adobe Commerce 2.4.1-Problem beschrieben, bei dem die Überprüfung der Vertex-Adresse während des Zahlungsschritts nicht funktioniert, wenn eine Versandadresse verwendet wird, die sich von der Rechnungsadresse unterscheidet. Das Problem wird voraussichtlich in Adobe Commerce 2.4.2 behoben.
exl-id: c2abeb96-e837-4d16-92dd-82fea5661dd9
feature: Shipping/Delivery
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%

---

# Adobe Commerce 2.4.1 Vertex-Adressvalidierungsmeldung nach Aktualisierung der Adresse

In diesem Artikel wird ein bekanntes Adobe Commerce 2.4.1-Problem beschrieben, bei dem die Überprüfung der Vertex-Adresse während des Zahlungsschritts nicht funktioniert, wenn eine Versandadresse verwendet wird, die sich von der Rechnungsadresse unterscheidet. Das Problem wird voraussichtlich in Adobe Commerce 2.4.2 behoben.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premise 2.4.1 mit aktivierter Vertex-Integration
* Adobe Commerce auf Cloud-Infrastruktur 2.4.1 mit aktivierter Vertex-Integration

## Problem

Voraussetzungen:

Aktivieren **Vertex-Adressbereinigung**. Anweisungen hierzu finden Sie [Konfigurieren der Adressbereinigung für Storefronts](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/vertex-address-cleansing-different-addresses-not-allowed.html?lang=de) in unserem Benutzerhandbuch.

<u>Schritte zur Reproduktion:</u>

1. Konto erstellen und anmelden.
1. Fügen Sie einen Artikel zum Warenkorb hinzu, indem **Zum Warenkorb hinzufügen** klicken. Klicken Sie auf das Symbol Warenkorb und dann auf **Zur Kasse wechseln**.
1. Geben Sie eine gültige Adresse in das Feld **Lieferadresse** ein.
1. Aktivieren Sie eine der Optionen unter **Versandmethoden**. Klicken Sie dann auf **Weiter**.
1. Wenn die Adressenvalidierung unterschiedliche Adressinformationen anzeigt, klicken Sie auf **Adresse aktualisieren** und anschließend auf **Weiter**.
1. Deaktivieren Sie das **Meine Rechnungs- und Lieferadresse sind identisch**.

<u>Erstes Szenario:</u>

Führen Sie die [&#x200B; sechs Schritte aus](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md#first_sixth) und dann:

1. Geben Sie eine neue gültige Rechnungsadresse ein.
1. Klicken Sie auf die Schaltfläche **Aktualisieren**. Die Nachricht/der Vorschlag wird wie folgt angezeigt: *Die Adresse ist ungültig.* Es folgt ein Adressenvorschlag wie: *Postleitzahl : XXXXX- XXXX Straße : XXX City Street XXX*
1. Klicken Sie auf die Schaltfläche **Aktualisieren** (nicht auf die Schaltfläche **Adresse aktualisieren** des Vertex-Adressvorschlags).
1. Klicken Sie auf die **Bearbeiten** der aktualisierten Rechnungsadresse.
1. Wählen Sie die Adresse aus dem Dropdown-Menü Adresse aus.
1. Klicken Sie auf die Schaltfläche **Aktualisieren**.

<u>Erwartetes Ergebnis:</u>

Die alte Validierungsmeldung/Empfehlungsnachricht wird entfernt.

<u>Tatsächliches Ergebnis:</u>

Die Überprüfungsmeldung/Empfehlung *Wir haben keine gültige Adresse gefunden Postleitzahl: XXXXX-XXXX Straße: XXX City Street XXX“* Nachricht wurde **NICHT** entfernt. Dasselbe Problem tritt auf, wenn Sie eine ungültige Adresse in das Formular eingeben.

<u>Zweites Szenario:</u>

Führen Sie die [&#x200B; sechs Schritte aus](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md#first_sixth) und dann:

1. Füllen Sie das Adressformular mit einer gültigen Adresse aus.
1. Klicken Sie auf die Schaltfläche **Aktualisieren**. Die Nachricht/der Vorschlag wird wie folgt angezeigt: *Die Adresse ist ungültig.* Es folgt ein Adressenvorschlag wie: *Postleitzahl : XXXXX-XXXX Straße : XXX City Street XXX*.
1. Klicken Sie auf die Schaltfläche **Aktualisieren** (nicht auf die Schaltfläche **Adresse aktualisieren** des Vertex-Adressvorschlags).
1. Überprüfen Sie die ***Meine Rechnungs- und Lieferadresse sind identisch*** Dropdown.

<u>Erwartetes Ergebnis:</u>

Die alte Validierungsmeldung/Empfehlungsnachricht wird entfernt.

<u>Tatsächliches Ergebnis:</u>

Die Überprüfungsmeldung/Empfehlung *Wir haben keine gültige Adresse gefunden Postleitzahl: XXXXX-XXXX Street XXX City Street XXX“* Nachricht wurde **NICHT** entfernt. Dasselbe Problem tritt auf, wenn Sie eine ungültige Adresse in das Formular eingeben.

## Weiterführende Informationen finden Sie in unserer Support-Wissensdatenbank:

[Bekanntes Problem in Adobe Commerce 2.3.6, 2.4.0-p1 und 2.4.1: Anmeldung bei dotdigital nicht möglich, wenn das Konto aktiviert ist](/help/troubleshooting/miscellaneous/magento-2-3-6-2-4-0-p1-2-4-1-known-issue-dotdigital-login.md)
