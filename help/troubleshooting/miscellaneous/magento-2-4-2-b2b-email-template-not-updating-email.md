---
title: "Adobe Commerce 2.4.2 B2B: E-Mail-Vorlage nicht aktualisiert E-Mail"
description: In diesem Artikel wird ein bekanntes B2B-Problem in Adobe Commerce 2.4.2 beschrieben, bei dem das Aktualisieren einiger Informationen in einer E-Mail-Vorlage in E-Mails nicht aktualisiert wird. Dieses Problem betrifft E-Mail-Inhalte wie Kundeninformationen, Währungsraten, Währungssymbol, E-Mail-Vorlagenänderungen usw. Es gibt derzeit keine Lösung, aber am Ende dieses Artikels gibt es eine Lösung.
exl-id: 31b7086f-a941-4682-aa07-301ac31d543b
feature: B2B, Communications
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# Adobe Commerce 2.4.2 B2B: E-Mail-Vorlage, die die E-Mail nicht aktualisiert

In diesem Artikel wird ein bekanntes B2B-Problem in Adobe Commerce 2.4.2 beschrieben, bei dem das Aktualisieren einiger Informationen in einer E-Mail-Vorlage in E-Mails nicht aktualisiert wird. Dieses Problem betrifft E-Mail-Inhalte wie Kundeninformationen, Währungsraten, Währungssymbol, E-Mail-Vorlagenänderungen usw. Es gibt derzeit keine Lösung, aber am Ende dieses Artikels gibt es eine Lösung.

## Betroffene Produkte und Versionen

* Adobe Commerce vor Ort 2.4.2
* Adobe Commerce Cloud-Infrastruktur 2.4.2
* B2B 1.3.1

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Der Unternehmensadministrator erstellt eine Bestellung (Purchase Order) im Frontend.
1. Überprüfen Sie die E-Mail &quot;Automatisch genehmigt&quot;. Der **Kundenname** / **Währungskurs** sollte erwartete Werte sein.
1. Ändern Sie das Währungssymbol (**Geschäfte > Konfiguration > Währungseinstellungen > Währungsoptionen**) in den Namen des Administrators für Admin und Unternehmen auf der Seite Kundenkonto .
1. Der Kundenadministrator erstellt eine weitere Bestellung in Admin.
1. Überprüfen Sie die E-Mail &quot;Automatisch genehmigt&quot;.

<u>Erwartete Ergebnisse:</u>

Der Kundenname und das Währungssymbol werden in E-Mails geändert und weisen die neuen Werte erwartungsgemäß auf.

<u>Tatsächliche Ergebnisse</u>:

Der Kundenname und das Währungssymbol werden in E-Mails nicht geändert und haben ihre vorherigen Werte.

## Workaround

Führen Sie den Cron-Auftrag oder Verbraucher manuell aus, um die neuen Informationen zu propagieren.

## Verwandtes Lesen

* [Verwalten von Nachrichtenwarteschlangen](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/message-queues/manage-message-queues) in unserer Entwicklerdokumentation.
