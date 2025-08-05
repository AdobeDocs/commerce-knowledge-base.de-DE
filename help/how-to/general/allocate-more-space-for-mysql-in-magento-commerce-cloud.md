---
title: Mehr Speicherplatz für MySQL in Adobe Commerce in der Cloud zuweisen
description: Dieser Artikel enthält Anweisungen dazu, wie Sie in Adobe Commerce in der Cloud-Infrastruktur mehr Speicherplatz für MySQL zuweisen.
exl-id: 98501aa0-5ec7-4ea1-8856-13d171ad0be9
feature: Cloud
source-git-commit: 139c2836ba36686357c7a5458a36550c7b1273c1
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# Mehr Speicherplatz für MySQL in Adobe Commerce in der Cloud zuweisen


## Platz auf Starter-Plan und Pro-Plan-Integration zuweisen

Für alle Starter-Planumgebungen und Pro-Plan [Integrationsumgebung](https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-27242) können Sie mehr Speicherplatz für MySQL in der `.magento/services.yaml`-Datei zuweisen, indem Sie den `mysql: disk:` erhöhen. Beispiel:

```yaml
mysql:
    type: mysql:10.0
    disk: 2048
```

Siehe den Artikel [Einrichten des MySQL-](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/configure/service/mysql)) als Referenz.

Nachdem Sie die `.magento/services.yaml` geändert haben, müssen Sie Ihre Änderungen übernehmen und pushen, damit sie angewendet werden. Mit der Push-Benachrichtigung wird der Bereitstellungsprozess Trigger.

>[!WARNING]
>
>Eine Starterplanpartition sollte niemals kleiner gemacht werden (z. B. von 30 GB auf 20 GB), da dies wahrscheinlich zu einer katastrophalen Datenbeschädigung führen wird.

## Platz auf Pro Plan Staging oder Produktion zuweisen

Um diese Änderungen an der Staging- oder Produktionsumgebung des Pro-Plans vorzunehmen, müssen Sie ein [Support-Ticket“ ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed). Wenn Sie ein Support-Ticket einreichen, um den Speicher zu erhöhen, muss der Support wissen, auf wie viel und auf welche Partition der Speicher angewendet werden soll (`/mysql` oder `/exports`). Eine Anfrage zur Speichererhöhung erfordert die Genehmigung Ihres Adobe-Accountteams, das die für Sie geeignete Speichermenge (gemäß Bestellformular) vor der Genehmigung überprüft.

## Verringernder zugewiesener Platz nicht verfügbar (Pro- und Starter-Plan)

Der Adobe Commerce-Support kann eine Partition erweitern (`/mysql` oder `/exports`), aber eine Partition nicht verkleinern. Dadurch besteht das Risiko einer Datenbeschädigung, weshalb kein abnehmender Speicher für eine Partition verfügbar ist.
Dies gilt auch für den Starter-Plan, bei dem Sie den zugewiesenen Speicherplatz selbst erhöhen können: Senken wird dringend nicht empfohlen und kann zu einer katastrophalen Datenbeschädigung führen.
