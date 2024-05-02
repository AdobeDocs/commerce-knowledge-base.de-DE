---
title: Adobe Commerce 2.4.1 und 2.3.6 erstellen eine Kontoschaltfläche mit deaktiviertem Hotfix
description: Dieser Artikel enthält einen Hotfix für das Problem, wenn Sie Schwierigkeiten haben, ein neues Konto zu erstellen, nachdem Sie in ein Feld im Formular einen falschen Wert eingegeben haben. Wenn Sie beispielsweise eine E-Mail-Adresse im falschen Format eingeben oder die Felder für Vor- oder Nachname leer lassen oder keinen Wert eingeben, der die Passwortanforderungen erfüllt. In den Versionen Q1 (2.4.2, 2.4.1-p1 und 2.3.6-p1) wird eine permanente Korrektur vorgenommen.
exl-id: e6e65ede-8156-4e2b-b369-b18395bb3dbf
feature: Customer Service
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# Adobe Commerce 2.4.1 und 2.3.6 erstellen eine Kontoschaltfläche mit deaktiviertem Hotfix

Dieser Artikel enthält einen Hotfix für das Problem, wenn Sie Schwierigkeiten haben, ein neues Konto zu erstellen, nachdem Sie in ein Feld im Formular einen falschen Wert eingegeben haben. Wenn Sie beispielsweise eine E-Mail-Adresse im falschen Format eingeben oder die Felder für Vor- oder Nachname leer lassen oder keinen Wert eingeben, der die Passwortanforderungen erfüllt. In den Versionen Q1 (2.4.2, 2.4.1-p1 und 2.3.6-p1) wird eine permanente Korrektur vorgenommen.

## Problem

Die **Konto erstellen** Schaltfläche auf der **Neues Konto erstellen** bleibt deaktiviert, wenn ein Käufer ungültige Daten eingegeben hat. Dadurch wird verhindert, dass Käufer nach einem Fehler erneut versuchen, ein Konto zu erstellen.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zu **Neues Kundenkonto erstellen**.
1. Füllen Sie die Formularfelder aus. Im **Passwort** -Feld, Eingabewerte, die nicht den Kennwortanforderungen entsprechen. Beispiel:
   * Die Kennwörter im **Passwort** und **Kennwort bestätigen** -Felder stimmen nicht überein.
   * Die Kennwörter im **Passwort** und **Kennwort bestätigen** -Felder sind nicht lang genug.
1. Klicken Sie auf **Konto erstellen** Schaltfläche.

<u>Erwartete Ergebnisse</u>:

* **Konto erstellen** -Schaltfläche aktiv/aktiviert bleiben.
* Der Benutzer sollte in der Lage sein, ein neues Konto zu erstellen.

<u>Tatsächliche Ergebnisse</u>:

* **Konto erstellen** Schaltfläche bleibt deaktiviert, auch wenn alle erforderlichen Felder mit gültigen/korrekten Daten ausgefüllt wurden.
* Der Kunde kann kein neues Konto erstellen.

## Patch

Der Patch ist an diesen Artikel angehängt. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link: [MC-38509-composer.patch herunterladen](assets/MC-38509-composer.patch.zip)

## Kompatible Adobe Commerce-Versionen:

Der Patch wurde für erstellt:

* Adobe Commerce auf Cloud-Infrastruktur 2.3.6 und 2.4.1.
* Adobe Commerce vor Ort 2.3.6 und 2.4.1.

Der Patch ist nicht mit anderen Adobe Commerce-Versionen und -Editionen kompatibel.

## Anwenden des Pflasters

Siehe [Anwenden eines von Adobe bereitgestellten Composer-Patches](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) für Anweisungen.

## Verwandtes Lesen

* [GitHub Adobe Commerce > Ungültiges Formular zur Kontoerstellung übermitteln lässt die Senden-Schaltfläche deaktiviert](https://github.com/magento/magento2/issues/30513)
* [Adobe Commerce-Benutzerhandbuch > Erste Schritte > Konto erstellen](https://docs.magento.com/user-guide/magento/magento-account-create.html)
