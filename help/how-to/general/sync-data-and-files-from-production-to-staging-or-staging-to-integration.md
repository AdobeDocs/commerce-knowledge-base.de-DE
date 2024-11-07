---
title: Synchronisieren von Daten und Dateien Produktion mit Staging oder Staging mit Integration
description: In diesem Artikel wird erläutert, wie Sie Ihre Produktionsumgebung mit Staging auf Adobe Commerce in der Cloud-Infrastruktur synchronisieren können. Dies ist nicht möglich.
exl-id: e3d001d1-1b2a-41b5-9b4a-00e53dc9d001
feature: Integration, Build
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# Synchronisieren von Daten und Dateien Produktion mit Staging oder Staging mit Integration

In diesem Artikel wird erläutert, wie Sie Ihre Produktionsumgebung mit Staging auf Adobe Commerce in der Cloud-Infrastruktur synchronisieren können. Dies ist über die Benutzeroberfläche oder die Magento-Cloud-CLI nicht möglich.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.3.x, 2.4.x

## So synchronisieren Sie Daten zwischen Umgebungen

Um die Daten zu synchronisieren, müssen Sie die Datenbank manuell aus der Quellumgebung ablegen. Um Daten in eine andere Umgebung zu übertragen, müssen Sie die Quellablage in die Zielumgebung hochladen und importieren. Weitere Informationen finden Sie unter [Adobe Commerce-Code in ein Cloud-Projekt importieren > Adobe Commerce-Datenbank importieren](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/staging-production) in unserer Entwicklerdokumentation.

Für die Adobe Commerce on Cloud Infrastructure Pro-Planarchitektur können Sie auch von der Staging- und Produktionsumgebung mit Ihrer Integrations-Master-Verzweigung synchronisieren. Bei dieser Synchronisierung wird nur Code abgerufen und gepusht, nicht Daten. Um Daten zu synchronisieren, müssen Sie die Datenbankdaten in die Datenbank einer anderen Umgebung übertragen.

>[!WARNING]
>
>Die Synchronisierung der Datenbank kann nicht in den Pro Staging- und Produktions-Clustern durchgeführt werden.

## So synchronisieren Sie Dateien zwischen Umgebungen

Verwenden Sie den Befehl `rsync` , um Dateien von einer Umgebung in eine andere zu synchronisieren. Weitere Informationen finden Sie unter [Bereitstellen von Code und Migrieren von statischen Dateien und Daten > Migrieren von Dateien mit rsync](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/staging-production#migrate-files-using-rsync) in unserer Entwicklerdokumentation.

>[!NOTE]
>
>Wenn Sie den Code von Integration mit Staging synchronisieren möchten, müssen Sie dies über die Verzweigung Integration tun. Anweisungen finden Sie unter [Von der übergeordneten Umgebung synchronisieren](/docs/commerce-cloud-service/user-guide/project/console-branches.html#sync-an-environment) in unserer Entwicklerdokumentation.
