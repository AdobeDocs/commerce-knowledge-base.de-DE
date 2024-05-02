---
title: Mehr Speicherplatz für MySQL in Adobe Commerce in Cloud zuweisen
description: Dieser Artikel enthält Anweisungen dazu, wie Sie in Adobe Commerce mehr Speicherplatz für MySQL in der Cloud-Infrastruktur zuweisen.
exl-id: 98501aa0-5ec7-4ea1-8856-13d171ad0be9
feature: Cloud
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# Mehr Speicherplatz für MySQL in Adobe Commerce in Cloud zuweisen


## Weisen Sie Platz für Starter-Plan und Pro-Plan-Integration zu

Für alle Starter-Planumgebungen und Pro-Plan [Integrationsumgebung](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md), können Sie MySQL im Abschnitt `.magento/services.yaml` durch Erhöhung der `mysql: disk:` -Parameter. Beispiel:

```yaml
mysql:
    type: mysql:10.0
    disk: 2048
```

Siehe [MySQL-Dienst einrichten](https://devdocs.magento.com/guides/v2.3/cloud/project/project-conf-files_services-mysql.html) Artikel als Referenz.

Sobald Sie die `.magento/services.yaml` -Datei, müssen Sie Ihre Änderungen übernehmen und pushen, damit sie angewendet werden. Die Push-Benachrichtigung Trigger den Bereitstellungsprozess.

>[!WARNING]
>
>Eine Starter-Plan-Partition sollte niemals kleiner werden (z. B. von 30 GB auf 20 GB), da dies wahrscheinlich zu einer katastrophalen Datenbeschädigung führen wird.

## Speicherplatz für Pro-Plan-Staging oder -Produktion zuweisen

Um diese Änderungen für die Staging- oder Produktionsumgebung des Pro-Plans vorzunehmen, müssen Sie eine [Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed). Beim Senden eines Support-Tickets zur Erhöhung des Speichers muss der Support wissen, wie viel und auf welche Partition der Speicher angewendet werden soll (`/mysql` oder `/exports`). Eine Anfrage zur Erhöhung des Speicherplatzes erfordert die Genehmigung durch Ihr Adobe Account-Team, das vor der Validierung Ihre berechtigte Speichermenge (gemäß Bestellformular) überprüft.

## Verringerter zugewiesener Speicherplatz nicht verfügbar (Pro- und Starter-Plan)

Der Adobe Commerce-Support kann eine Partition (`/mysql` oder `/exports`), kann aber eine Partition nicht verkleinern. Dies birgt die Gefahr von Datenbeschädigungen, weshalb eine Verringerung des Speicherplatzes für eine Partition nicht verfügbar ist.
Dies gilt auch für den Starter-Plan, bei dem Sie den zugewiesenen Platz selbst vergrößern können: Eine Reduzierung wird dringend nicht empfohlen und könnte zu katastrophalen Datenbeschädigungen führen.
