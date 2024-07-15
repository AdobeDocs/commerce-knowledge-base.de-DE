---
title: Anforderung zur Verbesserung der Integrationsumgebung - Pro und Starter
description: Wenn Sie Adobe Commerce on Cloud Infrastructure Pro Plan-Architekturkunde sind und derzeit die standardmäßigen Integrationsumgebungen verwenden oder Sie Adobe Commerce on Cloud Infrastructure Starter Plan Architecture-Kunde sind und derzeit die standardmäßige Staging-Umgebung verwenden und mehr Leistung wünschen, können Sie ein Upgrade auf Enhanced Integration Environments anfordern, die etwa das Vierfache der Leistung bieten. Dieser Artikel trennt Anweisungen für Pro-Kunden von Starter-Kunden.
exl-id: c49b049b-efb8-412f-b27d-a89f8a758d85
feature: Integration
role: Admin
source-git-commit: fb26b71316e04de31fa6a895b87230bed5c1ca6a
workflow-type: tm+mt
source-wordcount: '645'
ht-degree: 0%

---

# Anforderung zur Verbesserung der Integrationsumgebung - Pro und Starter

Wenn Sie Adobe Commerce on Cloud Infrastructure Pro Plan-Architekturkunde sind und derzeit die standardmäßigen Integrationsumgebungen verwenden oder Sie Adobe Commerce on Cloud Infrastructure Starter Plan Architecture-Kunde sind und derzeit die standardmäßige Staging-Umgebung verwenden und mehr Leistung wünschen, können Sie ein Upgrade auf Enhanced Integration Environments anfordern, die etwa das Vierfache der Leistung bieten. Dieser Artikel trennt Anweisungen für Pro-Kunden von Starter-Kunden.

>[!NOTE]
>
> Bei der Aktualisierung auf die erweiterte Integration werden möglicherweise nicht alle Leistungsprobleme behoben, da dies von den gesamten Ressourcenanforderungen Ihrer Installation, einschließlich Integrationen von Drittanbietern oder Anpassungen, abhängt.
>
> Außerdem müssen Sie sicherstellen, dass Sie die Best Practices für die beste Leistung in der Integrationsumgebung befolgen, und auch dies kann keine Komplettlösung sein. Eine Anleitung dazu finden Sie in der folgenden Dokumentation: [Pro-Architektur](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment) und [Starterarchitektur](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#staging-environment) im Handbuch zur Commerce on Cloud-Infrastruktur.

## Pro

1. Wenn Sie Pro verwenden, müssen Sie die Anzahl der Integrationsverzweigungen auf zwei reduzieren (**Der Hauptintegrationszweig ist in der Gesamtsumme** enthalten). **Hinweis: Die primäre Verzweigung in diesem Gesamtwert wird nicht gezählt. Die primäre Verzweigung wird nicht als Integrationsverzweigung betrachtet.** Befolgen Sie die Schritte unter [Verwalten von Zweigen mit der Cloud-Konsole](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/console-branches.html) in unserer Entwicklerdokumentation.
1. Der Händler muss [ein Support-Ticket senden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), das eine Aktualisierung auf erweiterte Integrationsumgebungen anfordert, und dabei den Kontaktgrund &quot;*Eine Änderung der Cloud-Konfiguration anfordern*&quot; verwenden.
1. Das Adobe Customer Engineering-Team bestätigt die Anzahl der Integrationsumgebungen und beginnt mit der Änderung.
1. Der Händler wird im Ticket benachrichtigt, wenn das Upgrade abgeschlossen ist.
1. Der Händler stellt die Integrationsumgebungen erneut bereit. Befolgen Sie die Schritte unter [Zusammenführen einer Verzweigung](https://devdocs.magento.com/cloud/env/environments-start.html#merge) in unserer Entwicklerdokumentation. *Hinweis*: Die Bereitstellung erfolgt automatisch bei Ausführung: <pre>Git-Push-Herkunft <branch-name></pre>

Die verbesserte Leistung weist auf eine erfolgreiche Aktualisierung auf die erweiterten Integrationsumgebungen hin.

**Notizen**:

* Die Standardgröße und die erweiterte Größe sind die einzigen beiden verfügbaren Größen.
* Alle Integrationsumgebungen für einen bestimmten Store haben dieselbe Größe - sie können nicht unabhängig voneinander skaliert werden.
* Wenn Sie mehr als zwei der erweiterten Integrationsumgebungen benötigen, wenden Sie sich an Ihr Adobe-Account-Team.

## Starter

1. Starterpläne können keine Integrationszweige aufweisen: Händler müssen die Integrationsumgebungen löschen und nur die Staging-Umgebung verlassen. Befolgen Sie die Schritte unter [Verwalten von Verzweigungen mit der Cloud-Konsole](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/console-branches.html) in unserer Entwicklerdokumentation. Die Anzahl der verfügbaren Umgebungen wird reduziert, um maximal eine Integrationsumgebung zu ermöglichen.
1. Der Händler muss [ein Support-Ticket senden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) und eine Aktualisierung auf erweiterte Integrationsumgebungen anfordern. Verwenden Sie dazu den Kontaktgrund *&quot;Cloud-Konfigurationsänderung anfordern&quot;* - **Ihre Staging-Umgebung ist eine benannte Integrationsumgebung**.
1. Das Adobe Customer Engineering-Team bestätigt die Anzahl der Integrationsumgebungen und beginnt mit der Änderung.
1. Der Händler wird im Ticket benachrichtigt, wenn das Upgrade abgeschlossen ist.
1. Der Händler stellt die Integrationsumgebungen erneut bereit. Befolgen Sie die Schritte unter [Zusammenführen einer Verzweigung](https://devdocs.magento.com/cloud/env/environments-start.html#merge) in unserer Entwicklerdokumentation. *Hinweis*: Die Bereitstellung erfolgt automatisch bei Ausführung: <pre>Git-Push-Herkunft <branch-name></pre>

Die verbesserte Leistung weist auf eine erfolgreiche Aktualisierung auf die erweiterten Integrationsumgebungen hin.

**Notizen**:

* Die Standardgröße und die erweiterte Größe sind die einzigen beiden verfügbaren Größen.
* Alle Integrationsumgebungen für einen bestimmten Store haben dieselbe Größe - sie können nicht unabhängig voneinander skaliert werden.
* Wenn Sie Integrationsumgebungen über das Staging hinaus benötigen, wenden Sie sich an Ihr Adobe-Account-Team.
* Wenn der Kauf nach dem 17. September 2020 erfolgt, gilt diese Verbesserung aufgrund erweiterter Integrationsumgebungen nicht mehr.
