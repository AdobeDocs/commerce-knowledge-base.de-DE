---
title: Mehr Speicherplatz für MySQL in Adobe Commerce in der Cloud zuweisen
description: Dieser Artikel enthält Anweisungen dazu, wie Sie in Adobe Commerce in der Cloud-Infrastruktur mehr Speicherplatz für MySQL zuweisen.
exl-id: 98501aa0-5ec7-4ea1-8856-13d171ad0be9
feature: Cloud
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%
---
# Mehr Speicherplatz für MySQL in Adobe Commerce in der Cloud zuweisen


## Platz auf Starter-Plan und Pro-Plan-Integration zuweisen

Für alle Starter-Planumgebungen und Pro-Plan [Integrationsumgebung](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27242) können Sie mehr Speicherplatz für MySQL in der `.magento/services.yaml`-Datei zuweisen, indem Sie den `mysql: disk:` erhöhen. Beispiel:

```yaml
mysql:
    type: mysql:10.0
    disk: 2048
```

Siehe den Artikel [Einrichten des MySQL-](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/mysql)) als Referenz.

Nachdem Sie die `.magento/services.yaml` geändert haben, müssen Sie Ihre Änderungen übernehmen und pushen, damit sie angewendet werden. Mit der Push-Benachrichtigung wird der Bereitstellungsprozess Trigger.

>[!WARNING]
>
>Eine Starterplanpartition sollte niemals kleiner gemacht werden (z. B. von 30 GB auf 20 GB), da dies wahrscheinlich zu einer katastrophalen Datenbeschädigung führen wird.

## Platz auf Pro Plan Staging oder Produktion zuweisen

Um diese Änderungen an der Staging- oder Produktionsumgebung des Pro-Plans vorzunehmen, müssen Sie ein [Support-Ticket“ ](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide). Wenn Sie ein Support-Ticket einreichen, um den Speicher zu erhöhen, muss der Support wissen, auf wie viel und auf welche Partition der Speicher angewendet werden soll (`/mysql` oder `/exports`). Eine Anfrage zur Speichererhöhung erfordert die Genehmigung Ihres Adobe-Accountteams, das die für Sie geeignete Speichermenge (gemäß Bestellformular) vor der Genehmigung überprüft.

## Verringernder zugewiesener Platz nicht verfügbar (Pro- und Starter-Plan)

Der Adobe Commerce-Support kann eine Partition erweitern (`/mysql` oder `/exports`), aber eine Partition nicht verkleinern. Dadurch besteht das Risiko einer Datenbeschädigung, weshalb kein abnehmender Speicher für eine Partition verfügbar ist.
Dies gilt auch für den Starter-Plan, bei dem Sie den zugewiesenen Speicherplatz selbst erhöhen können: Senken wird dringend nicht empfohlen und kann zu einer katastrophalen Datenbeschädigung führen.
