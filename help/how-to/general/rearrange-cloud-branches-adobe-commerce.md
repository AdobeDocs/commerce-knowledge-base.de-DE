---
title: Cloud-Verzweigungen in Adobe Commerce neu anordnen
description: In diesem Artikel finden Sie die Schritte, die Sie ausführen können, um Cloud-Verzweigungen auf Adobe Commerce neu anzuordnen, wenn sie nicht gemäß der richtigen Hierarchie organisiert sind. Wenn die Verzweigungen nicht in der richtigen Hierarchie organisiert sind, können Sie nicht mit der richtigen übergeordneten Verzweigung zusammenführen. Sie wird dann zur vorhandenen übergeordneten Verzweigung geleitet.
exl-id: 4fc0de96-da66-4634-a38a-6a1536855f8f
feature: Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Cloud-Verzweigungen in Adobe Commerce neu anordnen

In diesem Artikel finden Sie die Schritte, die Sie ausführen können, um Cloud-Verzweigungen auf Adobe Commerce neu anzuordnen, wenn sie nicht gemäß der richtigen Hierarchie organisiert sind. Wenn die Verzweigungen nicht in der richtigen Hierarchie organisiert sind, können Sie nicht mit der richtigen übergeordneten Verzweigung zusammenführen. Sie wird dann zur vorhandenen übergeordneten Verzweigung geleitet.

## Betroffene Produkte und Versionen:

* Adobe Commerce auf Cloud-Infrastruktur, 2.3.0-2.3.7-p2, 2.4.0-2.4.3-p1

## Cloud-Organisation

Die richtige Hierarchieorganisation für Ihre Filialen lautet:

* [!DNL Master [main] > Production > Staging > Integration]
* [!DNL Master [main] > Production > Staging > Integration2]

## Lösung für falsche Cloud-Zweigstellen - Organisation

So ordnen Sie Cloud-Verzweigungen neu an:

1. Sie müssen über die [[!DNL Super User]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=de) Rolle verfügen.
1. Installieren Sie den Magento-Cloud-[!DNL CLI] (falls nicht bereits geschehen).
1. Führen Sie den folgenden Befehl für die Verzweigungen aus, die verschoben werden müssen:
   `magento-cloud environment:info -e <branch to move> parent <target parent>`

Hinweis: Sie können die übergeordnete Verzweigung beim Erstellen einer neuen Verzweigung angeben. Anweisungen hierzu finden Sie unter [Erste Schritte mit dem Erstellen von Verzweigungen](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/cli-branches) in unserer Entwicklerdokumentation.

Sie können eine neue Umgebungsverzweigung mit dem `branch <environment-name> <parent-environment-ID>` Befehl „magento-cloud environment“ erstellen.

Es kann einige zusätzliche Zeit dauern, bis eine neue Umgebungsverzweigung erstellt und aktiviert wird.

## Verwandtes Lesen

[Verzweigungen mit dem verwalten [!DNL CLI]](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/cli-branches) finden Sie in unserer Entwicklerdokumentation.
