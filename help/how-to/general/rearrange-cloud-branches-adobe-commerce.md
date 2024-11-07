---
title: Neuanordnen von Cloud-Verzweigungen in Adobe Commerce
description: In diesem Artikel finden Sie die Schritte, die Sie unternehmen können, um Cloud-Verzweigungen in Adobe Commerce neu anzuordnen, wenn sie nicht gemäß der richtigen Hierarchie organisiert sind. Wenn die Verzweigungen nicht in der richtigen Hierarchie angeordnet sind, können Sie nicht mit der richtigen übergeordneten Verzweigung zusammenführen. Dies erfolgt über die vorhandene übergeordnete Verzweigung.
exl-id: 4fc0de96-da66-4634-a38a-6a1536855f8f
feature: Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

1. Sie müssen über die Rolle [[!DNL Super User]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) verfügen.
1. Installieren Sie die magento-cloud [!DNL CLI] (falls noch nicht geschehen).
1. Führen Sie den folgenden Befehl für die Verzweigungen aus, die verschoben werden müssen:
   `magento-cloud environment:info -e <branch to move> parent <target parent>`

Hinweis: Sie können die übergeordnete Verzweigung beim Erstellen einer neuen Verzweigung angeben. Anweisungen hierzu finden Sie in unserer Entwicklerdokumentation unter [Erste Schritte - Erstellen von Zweigen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches).

Mit dem Befehl `branch <environment-name> <parent-environment-ID>` magento-cloud-Umgebung können Sie eine neue Umgebungsverzweigung erstellen.

Es kann einige zusätzliche Zeit dauern, einen neuen Umgebungsverzweig zu erstellen und zu aktivieren.

## Verwandtes Lesen

[Verwalten Sie Zweige mit dem  [!DNL CLI]](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches) in unserer Entwicklerdokumentation.
