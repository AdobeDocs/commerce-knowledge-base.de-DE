---
title: 'MBI: Integrationen erneut authentifizieren'
description: Dieser Artikel bietet Lösungen für die erneute Autorisierung einer Integration, um Magento Business Intelligence (MBI) die erforderlichen Berechtigungen zum Abrufen von Daten von einem Drittanbieterdienst zu gewähren. Eine erneute Autorisierung ist erforderlich, wenn diese Berechtigungen widerrufen werden.
exl-id: c608d6f9-64a5-44f8-9d7b-9a85a2668775
feature: Commerce Intelligence, Integration
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# MBI: Integrationen erneut authentifizieren

Dieser Artikel bietet Lösungen für die erneute Autorisierung einer Integration, um Magento Business Intelligence (MBI) die erforderlichen Berechtigungen zum Abrufen von Daten von einem Drittanbieterdienst zu gewähren. Eine erneute Autorisierung ist erforderlich, wenn diese Berechtigungen widerrufen werden.

## Integrationen von Datenbanken und SaaS

Eine Liste der Datenbank- und SaaS-Integrationen finden Sie unter [Verbinden externer Daten mithilfe einer Integration](https://experienceleague.adobe.com/de/docs/commerce-business-intelligence/mbi/analyze/saas/integrations) in unserer Entwicklerdokumentation. (Verwenden Sie beim Öffnen der Seite das Inhaltsverzeichnis links für die Navigation.)

## Haben Sie Verbindungsprobleme?

Durch die Autorisierung einer Integration erhält MBI die erforderlichen Berechtigungen, um Daten von einem Drittanbieterdienst abzurufen. Eine erneute Autorisierung ist erforderlich, wenn diese Berechtigungen widerrufen werden.

Dies kann aus verschiedenen Gründen passieren:

* Ein Problem mit dem Drittanbieterdienst
* Ablauf des Authentifizierungs-Tokens
* Eine Änderung an Ihrem administrativen Konto
* oder ein internes Problem innerhalb von MBI

Der Status aller Integrationen finden Sie auf der Seite Integrationen ( **Daten verwalten > Integrationen** ):

![integrations_page.png](assets/Integrations_page.png)

Um sich erneut zu authentifizieren, müssen Sie möglicherweise Ihre Kontoanmeldeinformationen erneut eingeben. In einigen Fällen müssen Sie möglicherweise neue API-Schlüssel für die Problemintegration generieren. Klicken Sie auf den Namen des Integrationsproblems, um den erneuten Autorisierungsprozess zu starten.

Wenn das Problem weiterhin besteht, [ Sie ein Support-Ticket ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
