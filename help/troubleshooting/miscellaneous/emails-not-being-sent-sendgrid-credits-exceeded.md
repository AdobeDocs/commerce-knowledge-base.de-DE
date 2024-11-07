---
title: E-Mails werden nicht gesendet, wenn die SendGrid-Gutschriften in Adobe Commerce überschritten wurden
description: Dieser Artikel bietet eine Lösung, wenn Ihre E-Mails nicht gesendet werden, da Sie die Beschränkung für SendGrid-Guthaben auf Adobe Commerce überschritten haben.
exl-id: 43438890-665b-4408-8034-e61de8fbbd8b
feature: Communications, Orders
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# E-Mails werden nicht gesendet, wenn die SendGrid-Gutschriften in Adobe Commerce überschritten wurden

## Betroffene Produkte und Versionen

* Adobe Commerce für Cloud-Infrastruktur 2.3.0 - 2.3.7-p1, 2.4.0 - 2.4.3

## Problem

SendGrid-Gutschriften beziehen sich auf die Anzahl der zulässigen E-Mails, die gesendet werden können. Pro Monat können nur 12.000 E-Mails aus den Integrations- und Staging-Zweigen gesendet werden. Die Kreditkarten werden zu Beginn des Monats erneuert, also müssen Sie, wenn Ihnen der Kredit ausgeht, auf die Verlängerung warten.

Es gibt keine festen Beschränkungen für die Anzahl der E-Mails, die in der Produktion gesendet werden können, solange die Reputation des Absenders über 95 % liegt. Die Reputation wird durch die Anzahl an nicht zugestellten/abgelehnten E-Mails und die Tatsache beeinflusst, ob DNS-basierte Spam-Registrierungen Ihre Domain als potenzielle Spam-Quelle gekennzeichnet haben. Im Produktionsbereich werden pro Tag insgesamt 12.000 E-Mails zugeordnet. Diese Anzahl kann jedoch auf der Grundlage der durchschnittlichen Anzahl von E-Mails erweitert werden, die in den letzten fünf Tagen gesendet wurden.

## Wie kann ich überprüfen, ob Ihre Guthaben überschritten wurden?

Adobe Commerce on Cloud Infrastructure Pro-Planarchitektur: Überprüfen Sie die `/var/log/mail.log` - möglicherweise wird eine Meldung wie die folgende angezeigt:

`May 28 21:13:00 <i-node> postfix/error[21335]: BC7941A2BBF: to=<to@email.com>, relay=none, delay=4642, delays=4642/0.56/0/0.03, dsn=4.0.0, status=deferred (delivery temporarily suspended: SASL authentication failed; server smtp.sendgrid.net[ip address] said: 451 Authentication failed: Maximum credits exceeded).`

## Ursache

Die Anzahl der zulässigen E-Mails, die gesendet werden können, ist begrenzt.

## Lösung

* Wenn diese Nachricht in der Produktionsumgebung angezeigt wird, senden Sie ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), geben Sie die oben genannte Meldung an und fordern Sie die Erhöhung der Gutschriften an.[
* Wenn diese Meldung nicht angezeigt wird oder Sie sich in der Adobe Commerce-Planarchitektur für Cloud-Infrastruktur-Starter befinden, senden Sie auch ein Support-Ticket ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) und weisen Sie darauf hin, dass die Datei `mail.log` nicht angibt, dass die Credits überschritten wurden.[

## Verwandtes Lesen

* [SendGrid](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/project/sendgrid) in unserer Entwicklerdokumentation.
