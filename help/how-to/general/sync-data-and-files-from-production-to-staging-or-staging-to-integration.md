---
title: Synchronisieren von Daten und Produktionsdateien mit der Staging- oder Staging-Integration
description: In diesem Artikel wird erläutert, wie Sie Ihre Produktionsumgebung mit der Staging-Umgebung in Adobe Commerce auf Cloud-Infrastrukturen synchronisieren. Dies ist nicht möglich.
exl-id: e3d001d1-1b2a-41b5-9b4a-00e53dc9d001
feature: Integration, Build
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# Synchronisieren von Daten und Produktionsdateien mit der Staging- oder Staging-Integration

In diesem Artikel wird erläutert, wie Sie Ihre Produktionsumgebung mit der Staging-Umgebung in Adobe Commerce auf Cloud-Infrastrukturen synchronisieren können. Dies ist nicht über die Benutzeroberfläche oder die Magento-Cloud-CLI möglich.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.3.x, 2.4.x

## So synchronisieren Sie Daten von einer Umgebung mit einer anderen

Um die Daten zu synchronisieren, müssen Sie die Datenbank manuell aus der Quellumgebung entladen. Um Daten in eine andere Umgebung zu übertragen, müssen Sie dann den Quell-Dump in die Zielumgebung hochladen und importieren. Weitere Informationen finden Sie unter [Importieren von Adobe Commerce-Code in ein Cloud-Projekt > Importieren ](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/deploy/staging-production) Adobe Commerce-Datenbank“ in unserer Entwicklerdokumentation.

Für die Planarchitektur Adobe Commerce on Cloud Infrastructure Pro können Sie auch von der Staging- und Produktionsumgebung aus mit Ihrer Hauptverzweigung für die Integration synchronisieren. Diese Synchronisierung ruft nur Code ab und pusht ihn, keine Daten. Um Daten zu synchronisieren, müssen Sie die Datenbankdaten ablegen und in die Datenbank einer anderen Umgebung pushen.

>[!WARNING]
>
>Die Synchronisierung der Datenbank kann nicht in den Pro-Staging- und Produktions-Clustern durchgeführt werden.

## So synchronisieren Sie Dateien von einer Umgebung mit einer anderen

Um Dateien von einer Umgebung mit einer anderen zu synchronisieren, verwenden Sie den Befehl `rsync` . Weitere Informationen finden Sie unter [Bereitstellen von Code und Migrieren statischer Dateien und Daten > Migrieren von Dateien mithilfe von rsync](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/deploy/staging-production#migrate-files-using-rsync) in unserer Entwicklerdokumentation.

>[!NOTE]
>
>Wenn Sie den Code von der Integration zur Staging-Umgebung synchronisieren möchten, müssen Sie dies über die Integrationsverzweigung tun. Anweisungen hierzu finden Sie [Synchronisieren mit dem übergeordneten Element der Umgebung](/docs/commerce-cloud-service/user-guide/project/console-branches.html#sync-an-environment) in unserer Entwicklerdokumentation.
