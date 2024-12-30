---
title: E-Mails werden nicht gesendet, wenn die SendGrid-Punktzahl für Adobe Commerce überschritten wird
description: Dieser Artikel bietet eine Lösung für den Fall, dass Ihre E-Mails nicht gesendet werden, weil Sie das Limit für SendGrid-Guthaben in Adobe Commerce überschritten haben.
exl-id: 43438890-665b-4408-8034-e61de8fbbd8b
feature: Communications, Orders
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# E-Mails werden nicht gesendet, wenn die SendGrid-Punktzahl für Adobe Commerce überschritten wird

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.3.0 - 2.3.7-p1, 2.4.0 - 2.4.3

## Problem

SendGrid-Guthaben beziehen sich auf die Anzahl der zulässigen E-Mails, die gesendet werden können. Von den Integrations- und Staging-Zweigen können monatlich nur 12.000 E-Mails versendet werden. Das Guthaben wird zu Beginn des Monats erneuert. Wenn Ihnen also das Guthaben ausgeht, müssen Sie auf die Verlängerung warten.

Die Anzahl der E-Mails, die in der Produktion gesendet werden können, ist unbegrenzt, solange die Reputation des Absenders über 95 % liegt. Die Reputation wird von der Anzahl der Bounce/Rejected-E-Mails und davon beeinflusst, ob DNS-basierte Spam-Register Ihre Domain als potenzielle Spam-Quelle markiert haben. In der Produktionsumgebung werden pro Tag insgesamt 12.000 E-Mails zugewiesen. Diese Anzahl kann jedoch auf der Grundlage der durchschnittlichen Anzahl der E-Mails erweitert werden, die in den letzten fünf Tagen gesendet wurden.

## So können Sie überprüfen, ob Ihre Credits überschritten wurden:

Adobe Commerce auf Cloud-Infrastruktur Pro Planarchitektur: Überprüfen Sie die `/var/log/mail.log` - möglicherweise wird eine Meldung wie die folgende angezeigt:

`May 28 21:13:00 <i-node> postfix/error[21335]: BC7941A2BBF: to=<to@email.com>, relay=none, delay=4642, delays=4642/0.56/0/0.03, dsn=4.0.0, status=deferred (delivery temporarily suspended: SASL authentication failed; server smtp.sendgrid.net[ip address] said: 451 Authentication failed: Maximum credits exceeded).`

## Ursache

Die Anzahl der zulässigen E-Mails, die gesendet werden können, ist begrenzt.

## Lösung

* Wenn diese Meldung in der Produktionsumgebung angezeigt wird[ reichen Sie ein Support-Ticket ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), geben Sie die obige Meldung ein und fordern Sie die Erhöhung des Guthabens an.
* Wenn diese Meldung nicht angezeigt wird oder Sie sich in der Starterplanarchitektur für die Adobe Commerce-Cloud-Infrastruktur befinden, [ Sie auch „Support-Ticket senden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) und erwähnen, dass die `mail.log`-Datei nicht angibt, dass die Credits überschritten wurden.

## Verwandtes Lesen

* [SendGrid](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/project/sendgrid) in unserer Entwicklerdokumentation.
