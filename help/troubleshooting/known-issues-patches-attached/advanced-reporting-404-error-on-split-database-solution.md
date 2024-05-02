---
title: Fehler "Erweiterte Berichterstellung 404"in der geteilten Datenbanklösung
description: Dieser Artikel enthält einen Patch für Benutzer von Adobe Commerce 2.3.x mit der [split database solution](https://devdocs.magento.com/guides/v2.3/config-guide/multi-master/multi-master.html), bei dem beim Versuch, die erweiterte Berichterstellung zu verwenden, ein 404-Fehler auftritt.
exl-id: b81d4ada-5f38-4882-bc5b-ab4ccd63fc5f
feature: Commerce Intelligence
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---

# Fehler &quot;Erweiterte Berichterstellung 404&quot;in der geteilten Datenbanklösung

Dieser Artikel enthält einen Patch für Benutzer von Adobe Commerce 2.3.x mit der [Split-Datenbanklösung](https://devdocs.magento.com/guides/v2.3/config-guide/multi-master/multi-master.html) bei dem beim Versuch, die erweiterte Berichterstellung zu verwenden, ein 404-Fehler auftritt.

## Betroffene Produkte und Versionen

Adobe Commerce 2.3.0 - 2.3.5-p1

## Problem

Der Patch behebt das Problem, dass der falsche Verbindungsname zum Erfassen von Anführungsdaten verwendet wird. Da der falsche Verbindungsname verwendet wird, werden die Anführungsdaten nicht an Magento Business Intelligence (MBI) gesendet und die Berichte können nicht generiert werden.

## Lösung

Wenden Sie die [Patch](assets/MDVA-26831_EE_2.3.4_v1.composer.patch.zip) in diesem Artikel angegeben.

## Patch

Der Patch ist an diesen Artikel angehängt. Um es herunterzuladen, klicken Sie auf den folgenden Link:

[MDVA-26831\_EE\_2.3.4\_v1.composer.patch](assets/MDVA-26831_EE_2.3.4_v1.composer.patch.zip)

## Anwenden des Pflasters

Entpacken Sie die Datei und befolgen Sie die Anweisungen unter [Anwenden eines von Adobe bereitgestellten Composer-Patches](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).
