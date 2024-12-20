---
title: Site kann aufgrund des Wartungsmodus, der aktiviert bleibt, nicht geladen werden
description: 'Dieser Artikel enthält eine Korrektur für den Fall, dass Ihre Site nicht geladen wird, da der Wartungsmodus aktiviert bzw. nicht automatisch deaktiviert wurde. Möglicherweise erhalten Sie eine Fehlermeldung: *Dienst vorübergehend nicht verfügbar Der Server kann Ihre Anfrage aufgrund von Wartungs-Ausfallzeiten oder Kapazitätsproblemen vorübergehend nicht bearbeiten.*'
exl-id: 77e01588-e135-4d24-a0c4-1a6ee123f4a8
feature: Support
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Site kann aufgrund des Wartungsmodus, der aktiviert bleibt, nicht geladen werden

Dieser Artikel enthält eine Korrektur für den Fall, dass Ihre Site nicht geladen wird, da der Wartungsmodus aktiviert bzw. nicht automatisch deaktiviert wurde. Möglicherweise erhalten Sie eine Fehlermeldung: *Dienst vorübergehend nicht verfügbar Der Server kann Ihre Anfrage aufgrund von Wartungs-Ausfallzeiten oder Kapazitätsproblemen vorübergehend nicht bearbeiten.*

## Betroffene Versionen und Produkte

* Adobe Commerce auf Cloud-Infrastruktur 2.2.x, 2.3.x
* Adobe Commerce lokal 2.2.x, 2.3.x

## Problem

Der Wartungsmodus ist Teil des Implementierungsprozesses. Wenn sie jedoch automatisch aktiviert wurde und nicht deaktiviert wurde oder der Händler den Wartungsmodus manuell aktiviert hat und vergessen hat, ihn zu deaktivieren, kann dies zu einer fehlgeschlagenen Bereitstellung führen.

## Ursache

Wenn der Wartungsmodus aktiviert ist, wird das Laden der Site verhindert.

## Lösung

Um den aktuellen Wartungsmodus-Status zu überprüfen, führen Sie den folgenden Befehl über die CLI aus:

```
bin/magento maintenance:status
```

Um den Wartungsmodus zu deaktivieren, führen Sie den folgenden Befehl in der CLI aus:

```
bin/magento maintenance:disable
```

## Verwandte Informationen

Informationen dazu, wann der Wartungsmodus verwendet werden soll, finden Sie in unserer Entwicklerdokumentation unter [Wartungsmodus aktivieren oder deaktivieren](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) .
