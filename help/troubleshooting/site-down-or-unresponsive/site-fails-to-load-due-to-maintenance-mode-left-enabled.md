---
title: Site kann nicht geladen werden, da der Wartungsmodus aktiviert bleibt
description: 'Dieser Artikel bietet eine Fehlerbehebung für den Fall, dass Ihre Site nicht geladen wird, weil der Wartungsmodus aktiviert bleibt oder nicht automatisch deaktiviert wurde. Möglicherweise erhalten Sie eine Fehlermeldung: *Der Service ist vorübergehend nicht verfügbar Der Server kann Ihre Anfrage aufgrund von Wartungsarbeiten oder Kapazitätsproblemen vorübergehend nicht bearbeiten.*'
exl-id: 77e01588-e135-4d24-a0c4-1a6ee123f4a8
feature: Support
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Site kann nicht geladen werden, da der Wartungsmodus aktiviert bleibt

Dieser Artikel bietet eine Fehlerbehebung für den Fall, dass Ihre Site nicht geladen wird, weil der Wartungsmodus aktiviert bleibt oder nicht automatisch deaktiviert wurde. Möglicherweise erhalten Sie eine Fehlermeldung: *Dienst vorübergehend nicht verfügbar Der Server kann Ihre Anforderung aufgrund von Wartungsarbeiten oder Kapazitätsproblemen vorübergehend nicht bearbeiten.*

## Betroffene Versionen und Produkte

* Adobe Commerce auf Cloud-Infrastruktur 2.2.x, 2.3.x
* Adobe Commerce On-Premises 2.2.x, 2.3.x

## Problem

Der Wartungsmodus ist Teil des Bereitstellungsprozesses. Wenn er jedoch automatisch aktiviert wurde und nicht deaktiviert wurde oder der Merchant den Wartungsmodus manuell aktiviert und die Deaktivierung vergessen hat, kann dies zu einer fehlgeschlagenen Bereitstellung führen.

## Ursache

Wenn der Wartungsmodus aktiviert ist, wird die Site nicht geladen.

## Lösung

Um den aktuellen Status des Wartungsmodus zu überprüfen, führen Sie folgenden Befehl über die CLI aus:

```
bin/magento maintenance:status
```

Um den Wartungsmodus zu deaktivieren, führen Sie den folgenden Befehl in der CLI aus:

```
bin/magento maintenance:disable
```

## Verwandtes Lesen

Informationen zur Verwendung des Wartungsmodus finden Sie unter [Aktivieren oder Deaktivieren ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) Wartungsmodus“ in der Entwicklerdokumentation.
