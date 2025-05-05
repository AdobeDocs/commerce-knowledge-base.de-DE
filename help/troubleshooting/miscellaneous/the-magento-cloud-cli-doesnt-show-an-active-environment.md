---
title: Die "Magento-Cloud [!DNL CLI]  zeigt keine aktive Umgebung
description: In diesem Artikel wird ein bekanntes Adobe Commerce-Problem beschrieben, bei dem "Magento-Cloud“ [!DNL CLI] (Befehlszeilen-Tool) keine aktive Umgebung anzeigt.
feature: Cloud, Integration, Configuration
role: Developer
exl-id: 3c1b5de2-8888-4531-9dc1-cd478e3c96fc
source-git-commit: 5eac8bb54e205eff6a96e279295cd12db1009f0a
workflow-type: tm+mt
source-wordcount: '124'
ht-degree: 0%

---

# Die `Magento-cloud` [!DNL CLI] zeigt keine aktive Umgebung an

## Problem

Es gibt mehrere aktive Umgebungen, und Sie versuchen, mit einer Umgebung zu interagieren, indem Sie einen `Magento-cloud` [!DNL CLI]-Befehl (Befehlszeilen-Tool) ausführen. (Beispiel: `ssh`, `db:size`, `db:sql` usw.)
Die Aufforderung zur Auswahl der gewünschten Umgebung führt diese Umgebung jedoch nicht auf. (Beispiel: die Integrationsumgebung)

```
Enter a number to choose an environment:
Default: master
  [0] integration2 (type: development)
  [1] master (type: development)
  [2] production
  [3] staging
 >
```

## Ursache

Die Umgebung ist möglicherweise nicht verfügbar, da eine Bereitstellung in Bearbeitung ist, hängen geblieben ist oder fehlgeschlagen ist.

## Lösung

Sie müssen die Umgebung manuell mit dem `e|-environment`-Flag angeben.

1. Suchen Sie die Liste der aktiven Umgebungen und notieren Sie sich die Umgebungsnamen:

```
$ magento-cloud environment: list |grep "Active\|ID"
Your environments are:

| ID                     | Title            | Status       | Type           |
| Master                 | Master           | Active       | Development    |
|   Production           | Production       | Active       | Production     |
|     Staging            | Staging          | Active       | Staging        |
|       Integration      | Integration      | Active       | Development    |
|          Integration 2 | Integration 2    | Active       | Development    |
```

&#x200B;2. Geben Sie mit Ihrem Befehl die Umgebungskennung an:

`magento-cloud ssh -e integration`
