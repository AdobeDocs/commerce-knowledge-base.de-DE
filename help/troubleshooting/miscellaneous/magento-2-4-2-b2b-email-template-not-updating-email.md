---
title: 'Adobe Commerce 2.4.2 B2B: E-Mail-Vorlage wird nicht aktualisiert'
description: In diesem Artikel wird ein bekanntes Adobe Commerce 2.4.2 B2B-Problem beschrieben, bei dem das Aktualisieren einiger Informationen in einer E-Mail-Vorlage nicht in E-Mails aktualisiert wird. Dieses Problem wirkt sich auf E-Mail-Inhalte wie Kundeninformationen, Währungskurse, Währungssymbole, E-Mail-Vorlagenänderungen usw. aus. Derzeit ist keine Lösung verfügbar. Am Ende dieses Artikels gibt es jedoch eine Problemumgehung.
exl-id: 31b7086f-a941-4682-aa07-301ac31d543b
feature: B2B, Communications
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# Adobe Commerce 2.4.2 B2B: E-Mail-Vorlage wird nicht aktualisiert

In diesem Artikel wird ein bekanntes Adobe Commerce 2.4.2 B2B-Problem beschrieben, bei dem das Aktualisieren einiger Informationen in einer E-Mail-Vorlage nicht in E-Mails aktualisiert wird. Dieses Problem wirkt sich auf E-Mail-Inhalte wie Kundeninformationen, Währungskurse, Währungssymbole, E-Mail-Vorlagenänderungen usw. aus. Derzeit ist keine Lösung verfügbar. Am Ende dieses Artikels gibt es jedoch eine Problemumgehung.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premises 2.4.2
* Adobe Commerce Cloud-Infrastruktur 2.4.2
* B2B 1.3.1

## Problem

<u>Schritte zur Reproduktion</u>:

1. Der Unternehmensadministrator erstellt eine Bestellung (Bestellung) im Frontend.
1. Überprüfen Sie die automatisch genehmigte E-Mail. Der **Kundenname**/**Währungskurs** sollte erwartete Werte sein.
1. Währungssymbol ändern (**Stores > Konfiguration > Währungseinstellungen > Währungsoptionen**) in Admin- und Unternehmensadministratorname auf der Seite „Kundenkonto“.
1. Der Kundenadministrator erstellt eine weitere Bestellung in Admin.
1. Überprüfen Sie die automatisch genehmigte E-Mail.

<u>Erwartete Ergebnisse:</u>

Kundenname und Währungssymbol werden in E-Mails geändert und haben die neuen Werte erwartungsgemäß.

<u>Tatsächliche Ergebnisse</u>:

Kundenname und Währungssymbol werden in E-Mails nicht geändert und haben ihre vorherigen Werte.

## Abhilfe

Führen Sie den Cron-Auftrag oder Verbraucher manuell aus, um die neuen Informationen weiterzugeben.

## Verwandtes Lesen

* [Verwalten von ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/message-queues/manage-message-queues) in unserer Entwicklerdokumentation.
