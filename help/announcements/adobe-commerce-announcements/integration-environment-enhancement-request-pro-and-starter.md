---
title: Verbesserungsanfrage zur Integrationsumgebung - Pro und Starter
description: Wenn Sie Adobe Commerce on Cloud Infrastructure Pro Plan Architecture-Kunde sind und derzeit die Integrationsumgebungen in Standardgröße verwenden oder wenn Sie Adobe Commerce on Cloud Infrastructure Starter Plan Architecture-Kunde sind und derzeit die Staging-Umgebung in Standardgröße verwenden und mehr Leistung benötigen, können Sie ein Upgrade auf Enhanced Integration Environments anfordern, die etwa die vierfache Leistung bieten. In diesem Artikel werden Anweisungen für Pro-Kunden und Starter-Kunden getrennt.
exl-id: c49b049b-efb8-412f-b27d-a89f8a758d85
feature: Integration
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '645'
ht-degree: 0%

---

# Verbesserungsanfrage zur Integrationsumgebung - Pro und Starter

Wenn Sie Adobe Commerce on Cloud Infrastructure Pro Plan Architecture-Kunde sind und derzeit die Integrationsumgebungen in Standardgröße verwenden oder wenn Sie Adobe Commerce on Cloud Infrastructure Starter Plan Architecture-Kunde sind und derzeit die Staging-Umgebung in Standardgröße verwenden und mehr Leistung benötigen, können Sie ein Upgrade auf Enhanced Integration Environments anfordern, die etwa die vierfache Leistung bieten. In diesem Artikel werden Anweisungen für Pro-Kunden und Starter-Kunden getrennt.

>[!NOTE]
>
> Das Upgrade auf eine erweiterte Integration kann nicht alle Leistungsprobleme beheben, da es von den gesamten Ressourcenanforderungen Ihrer Installation abhängt, einschließlich Integrationen oder Anpassungen von Drittanbietern.
>
> Außerdem müssen Sie sicherstellen, dass Sie die Best Practices für die beste Leistung in der Integrationsumgebung befolgen. Auch dies ist möglicherweise keine Komplettlösung. Weitere Informationen finden Sie in der Dokumentation zu [Pro-Architektur](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment) und [Starter-](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#staging-environment) im Handbuch zu Commerce in Cloud-Infrastrukturen .

## Profi

1. Wenn Sie Pro verwenden, müssen Sie zum Upgrade die Anzahl der Integrationsverzweigungen auf zwei reduzieren (**die Hauptverzweigung der Integration ist in der Gesamtanzahl enthalten**). **Hinweis: Die primäre Verzweigung wird in dieser Summe nicht gezählt. Die primäre Verzweigung wird nicht als Integrationsverzweigung betrachtet.** Folgen Sie den Schritten in [Verzweigungen mit der Cloud-Konsole verwalten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/console-branches.html) in unserer Entwicklerdokumentation.
1. Der Händler muss [ein Support-Ticket ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), um ein Upgrade auf eine erweiterte Integrationsumgebung anzufordern, und zwar unter Verwendung des Kontaktgrundes &quot;*einer Cloud-Konfigurationsänderung*.
1. Adobe Customer Engineering-Team bestätigt die Anzahl der Integrationsumgebungen und beginnt mit der Änderung.
1. Der Händler wird im Ticket benachrichtigt, wenn das Upgrade abgeschlossen ist.
1. Der Händler stellt die Integrationsumgebungen erneut bereit. Befolgen Sie die Schritte unter [Verzweigung zusammenführen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches#merge-a-branch) in unserer Entwicklerdokumentation. *Hinweis*: Die Bereitstellung erfolgt automatisch, wenn Sie Folgendes ausführen: <pre>Git-Push-Herkunft &lt;branch-name></pre>

Eine höhere Leistung bedeutet ein erfolgreiches Upgrade auf erweiterte Integrationsumgebungen.

**Hinweise**:

* Die Standardgröße und die erweiterte Größe sind die einzigen beiden verfügbaren Größen.
* Alle Integrationsumgebungen für einen bestimmten Store haben dieselbe Größe und können nicht unabhängig voneinander skaliert werden.
* Wenn Sie mehr als zwei der erweiterten Integrationsumgebungen benötigen, wenden Sie sich an Ihr Adobe-Account-Team.

## Starter

1. Starterpläne können keine Integrationszweige haben: Händler müssen die Integrationsumgebungen löschen und dürfen nur die Staging-Umgebung verlassen. Befolgen Sie die Schritte in [Verzweigungen mit der Cloud-Konsole verwalten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/console-branches.html) in unserer Entwicklerdokumentation. Die Anzahl der verfügbaren Umgebungen wird reduziert, um maximal eine Integrationsumgebung zu ermöglichen.
1. Der Händler muss [ein Support-Ticket ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), um ein Upgrade auf die erweiterte Integrationsumgebung anzufordern, und zwar unter Verwendung des Kontaktgrundes *„Änderung der Cloud-Konfiguration anfordern“* - **Ihre Staging-Umgebung ist eine benannte Integrationsumgebung**.
1. Adobe Customer Engineering-Team bestätigt die Anzahl der Integrationsumgebungen und beginnt mit der Änderung.
1. Der Händler wird im Ticket benachrichtigt, wenn das Upgrade abgeschlossen ist.
1. Der Händler stellt die Integrationsumgebungen erneut bereit. Befolgen Sie die Schritte unter [Verzweigung zusammenführen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches#merge-a-branch) in unserer Entwicklerdokumentation. *Hinweis*: Die Bereitstellung erfolgt automatisch, wenn Sie Folgendes ausführen: <pre>Git-Push-Herkunft &lt;branch-name></pre>

Eine höhere Leistung bedeutet ein erfolgreiches Upgrade auf erweiterte Integrationsumgebungen.

**Hinweise**:

* Die Standardgröße und die erweiterte Größe sind die einzigen beiden verfügbaren Größen.
* Alle Integrationsumgebungen für einen bestimmten Store haben dieselbe Größe und können nicht unabhängig voneinander skaliert werden.
* Wenn Sie Integrationsumgebungen benötigen, die über das Staging hinausgehen, wenden Sie sich an Ihr Adobe-Account-Team.
* Wenn der Kauf nach dem 17. September 2020 erfolgt, gilt diese Verbesserung aufgrund der erweiterten Integrationsumgebungen nicht.
