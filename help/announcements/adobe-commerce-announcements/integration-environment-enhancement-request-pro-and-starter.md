---
title: Anforderung zur Verbesserung der Integrationsumgebung - Pro und Starter
description: Wenn Sie Adobe Commerce on Cloud Infrastructure Pro Plan-Architekturkunde sind und derzeit die standardmäßigen Integrationsumgebungen verwenden oder Sie Adobe Commerce on Cloud Infrastructure Starter Plan Architecture-Kunde sind und derzeit die standardmäßige Staging-Umgebung verwenden und mehr Leistung wünschen, können Sie ein Upgrade auf Enhanced Integration Environments anfordern, die etwa das Vierfache der Leistung bieten. Dieser Artikel trennt Anweisungen für Pro-Kunden von Starter-Kunden.
exl-id: c49b049b-efb8-412f-b27d-a89f8a758d85
feature: Integration
role: Admin
source-git-commit: 43be85de953909253900d60488f76a20bac91793
workflow-type: tm+mt
source-wordcount: '568'
ht-degree: 0%

---

# Anforderung zur Verbesserung der Integrationsumgebung - Pro und Starter

Wenn Sie Adobe Commerce on Cloud Infrastructure Pro Plan-Architekturkunde sind und derzeit die standardmäßigen Integrationsumgebungen verwenden oder Sie Adobe Commerce on Cloud Infrastructure Starter Plan Architecture-Kunde sind und derzeit die standardmäßige Staging-Umgebung verwenden und mehr Leistung wünschen, können Sie ein Upgrade auf Enhanced Integration Environments anfordern, die etwa das Vierfache der Leistung bieten. Dieser Artikel trennt Anweisungen für Pro-Kunden von Starter-Kunden.

## Pro

1. Wenn Sie Pro verwenden, müssen Sie die Anzahl der Integrationsverzweigungen auf zwei reduzieren (**der Hauptintegrationszweig ist in der Summe enthalten.**). **Hinweis: Die primäre Verzweigung wird in dieser Summe nicht gezählt. Die primäre Verzweigung wird nicht als Integrationsverzweigung betrachtet.** Führen Sie die Schritte unter [Verwalten von Zweigen mit der Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/console-branches.html) in unserer Entwicklerdokumentation.
1. Der Händler muss [Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) Anforderung eines Upgrades auf erweiterte Integrationsumgebungen unter Verwendung des Kontaktgrunds &quot;*Änderung der Cloud-Konfiguration anfordern*&quot;.
1. Das Adobe Customer Engineering-Team bestätigt die Anzahl der Integrationsumgebungen und beginnt mit der Änderung.
1. Der Händler wird im Ticket benachrichtigt, wenn das Upgrade abgeschlossen ist.
1. Der Händler stellt die Integrationsumgebungen erneut bereit. Führen Sie die Schritte unter [Zusammenführen einer Verzweigung](https://devdocs.magento.com/cloud/env/environments-start.html#merge) in unserer Entwicklerdokumentation. *Hinweis*: Die Bereitstellung erfolgt automatisch bei der Ausführung: <pre>Git-Push-Herkunft <branch-name></pre>

Die verbesserte Leistung weist auf eine erfolgreiche Aktualisierung auf die erweiterten Integrationsumgebungen hin.

**Hinweise**:

* Die Standardgröße und die erweiterte Größe sind die einzigen beiden verfügbaren Größen.
* Alle Integrationsumgebungen für einen bestimmten Store haben dieselbe Größe - sie können nicht unabhängig voneinander skaliert werden.
* Wenn Sie mehr als zwei der erweiterten Integrationsumgebungen benötigen, wenden Sie sich an Ihr Adobe-Account-Team.

## Starter

1. Starterpläne können keine Integrationszweige aufweisen: Händler müssen die Integrationsumgebungen löschen und nur die Staging-Umgebung verlassen. Führen Sie die Schritte unter [Verwalten von Zweigen mit der Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/console-branches.html) in unserer Entwicklerdokumentation. Die Anzahl der verfügbaren Umgebungen wird reduziert, um maximal eine Integrationsumgebung zu ermöglichen.
1. Der Händler muss [Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) Anforderung eines Upgrades auf erweiterte Integrationsumgebungen unter Verwendung des Kontaktgrunds *&quot;Eine Änderung der Cloud-Konfiguration anfordern&quot;* -  **Ihre Staging-Umgebung ist eine benannte Integrationsumgebung.**.
1. Das Adobe Customer Engineering-Team bestätigt die Anzahl der Integrationsumgebungen und beginnt mit der Änderung.
1. Der Händler wird im Ticket benachrichtigt, wenn das Upgrade abgeschlossen ist.
1. Der Händler stellt die Integrationsumgebungen erneut bereit. Führen Sie die Schritte unter [Zusammenführen einer Verzweigung](https://devdocs.magento.com/cloud/env/environments-start.html#merge) in unserer Entwicklerdokumentation. *Hinweis*: Die Bereitstellung erfolgt automatisch bei der Ausführung: <pre>Git-Push-Herkunft <branch-name></pre>

Die verbesserte Leistung weist auf eine erfolgreiche Aktualisierung auf die erweiterten Integrationsumgebungen hin.

**Hinweise**:

* Die Standardgröße und die erweiterte Größe sind die einzigen beiden verfügbaren Größen.
* Alle Integrationsumgebungen für einen bestimmten Store haben dieselbe Größe - sie können nicht unabhängig voneinander skaliert werden.
* Wenn Sie Integrationsumgebungen über das Staging hinaus benötigen, wenden Sie sich an Ihr Adobe-Account-Team.
* Wenn der Kauf nach dem 17. September 2020 erfolgt, gilt diese Verbesserung aufgrund erweiterter Integrationsumgebungen nicht mehr.
