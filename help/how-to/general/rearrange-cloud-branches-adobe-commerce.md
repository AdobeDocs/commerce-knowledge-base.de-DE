---
title: Neuanordnen von Cloud-Verzweigungen in Adobe Commerce
description: In diesem Artikel finden Sie die Schritte, die Sie unternehmen können, um Cloud-Verzweigungen in Adobe Commerce neu anzuordnen, wenn sie nicht gemäß der richtigen Hierarchie organisiert sind. Wenn die Verzweigungen nicht in der richtigen Hierarchie angeordnet sind, können Sie nicht mit der richtigen übergeordneten Verzweigung zusammenführen. Dies erfolgt über die vorhandene übergeordnete Verzweigung.
exl-id: 4fc0de96-da66-4634-a38a-6a1536855f8f
feature: Cloud
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Neuanordnen von Cloud-Verzweigungen in Adobe Commerce

In diesem Artikel finden Sie die Schritte, die Sie unternehmen können, um Cloud-Verzweigungen in Adobe Commerce neu anzuordnen, wenn sie nicht gemäß der richtigen Hierarchie organisiert sind. Wenn die Verzweigungen nicht in der richtigen Hierarchie angeordnet sind, können Sie nicht mit der richtigen übergeordneten Verzweigung zusammenführen. Dies erfolgt über die vorhandene übergeordnete Verzweigung.

## Betroffene Produkte und Versionen:

* Adobe Commerce für Cloud-Infrastruktur, 2.3.0-2.3.7-p2, 2.4.0-2.4.3-p1

## Cloud-Zweigorganisation

Die richtige Hierarchieorganisation für Ihre Verzweigungen ist:

* [!DNL Master [main] > Production > Staging > Integration]
* [!DNL Master [main] > Production > Staging > Integration2]

## Lösung für falsche Cloud-Verzweigungsorganisation

So ordnen Sie Cloud-Verzweigungen neu an:

1. Sie müssen über die [[!DNL Super User]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) Rolle.
1. Magento-Cloud installieren [!DNL CLI] (falls nicht geschehen).
1. Führen Sie den folgenden Befehl für die Verzweigungen aus, die verschoben werden müssen:
   `magento-cloud environment:info -e <branch to move> parent <target parent>`

Hinweis: Sie können die übergeordnete Verzweigung beim Erstellen einer neuen Verzweigung angeben. Eine Anleitung finden Sie unter [Erste Schritte - Erstellen von Verzweigungen](https://devdocs.magento.com/cloud/env/environments-start.html#getstarted) in unserer Entwicklerdokumentation.

Sie können eine neue Umgebungsverzweigung mit dem `branch <environment-name> <parent-environment-ID>` Befehl für die magento-cloud-Umgebung.

Es kann einige zusätzliche Zeit dauern, einen neuen Umgebungsverzweig zu erstellen und zu aktivieren.

## Verwandtes Lesen

[Verwalten von Verzweigungen mit [!DNL CLI]](https://devdocs.magento.com/cloud/env/environments-start.html) in unserer Entwicklerdokumentation.
