---
title: '"Magento-cloud"zeigt keine aktive Umgebung an. [!DNL CLI] '
description: In diesem Artikel wird ein bekanntes Adobe Commerce-Problem beschrieben, bei dem "Magento-cloud" [!DNL CLI]  (Befehlszeilen-Tool) keine aktive Umgebung anzeigt.
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

Es gibt mehrere aktive Umgebungen. Sie versuchen, mit einer Umgebung zu interagieren, indem Sie einen Befehl `Magento-cloud` [!DNL CLI] (Befehlszeilen-Tool) ausführen. (Beispiel: `ssh`, `db:size`, `db:sql` usw.)
Die Aufforderung zur Auswahl der gewünschten Umgebung listet diese Umgebung jedoch nicht auf. (Beispiel: die Integrationsumgebung)

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

Die Umgebung ist möglicherweise nicht verfügbar, da eine Implementierung ausgeführt wird, blockiert ist oder fehlgeschlagen ist.

## Lösung

Sie müssen die Umgebung manuell mit dem Flag `e|-environment` angeben.

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

2. Geben Sie die Kennung der Umgebung mit Ihrem Befehl an:

`magento-cloud ssh -e integration`
