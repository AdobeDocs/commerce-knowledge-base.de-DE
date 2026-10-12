---
title: 'MBI: Integrationen erneut authentifizieren'
description: Dieser Artikel bietet Lösungen für die erneute Autorisierung einer Integration, um Magento Business Intelligence (MBI) die erforderlichen Berechtigungen zum Abrufen von Daten aus einem Drittanbieterdienst zu gewähren. Eine erneute Autorisierung ist erforderlich, wenn diese Berechtigungen widerrufen werden.
exl-id: c608d6f9-64a5-44f8-9d7b-9a85a2668775
feature: Commerce Intelligence, Integration
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 3cd14413-6539-5c64-b063-fdcabf03abff
    internal-label: Commerce Intelligence
  - id: cc04bd17-78d5-5120-8c3d-1b8a57e49280
    internal-label: Integration
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%
---
# MBI: Integrationen erneut authentifizieren

Dieser Artikel bietet Lösungen für die erneute Autorisierung einer Integration, um Magento Business Intelligence (MBI) die erforderlichen Berechtigungen zum Abrufen von Daten aus einem Drittanbieterdienst zu gewähren. Eine erneute Autorisierung ist erforderlich, wenn diese Berechtigungen widerrufen werden.

## Integrationen von Datenbanken und SaaS

Eine Liste der Datenbank- und SaaS-Integrationen finden Sie unter [Verbinden externer Daten mithilfe einer Integration](https://experienceleague.adobe.com/en/docs/commerce-business-intelligence/mbi/analyze/saas/integrations) in unserer Entwicklerdokumentation. (Verwenden Sie beim Öffnen der Seite das Inhaltsverzeichnis links für die Navigation.)

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

Wenn das Problem weiterhin besteht, [&#x200B; Sie ein Support-Ticket &#x200B;](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket).
