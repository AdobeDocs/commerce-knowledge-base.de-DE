---
title: Leistungsprobleme aufgrund übermäßiger Ajax-Anforderungen
description: Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce-Leistungsproblem, das durch übermäßige Ajax-Anforderungen verursacht wird. Das Problem wurde in Adobe Commerce 2.3.4 behoben.
exl-id: d9a69406-3970-4556-aa6a-1309b24366d8
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 0%

---

# Leistungsprobleme aufgrund übermäßiger Ajax-Anforderungen

Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce-Leistungsproblem, das durch übermäßige Ajax-Anforderungen verursacht wird. Das Problem wurde in Adobe Commerce 2.3.4 behoben.

## Problem

Adobe Commerce sendet möglicherweise redundante [Ajax-Anfragen](/help/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.md) vom Store an den Server, um die Bannerinformationen und Kundeninformationen zu erhalten. Diese Ajax-Anforderungen wirken sich auf die Leistung aus, insbesondere bei Bedingungen mit hoher Auslastung (hohes Volumen und hohes Traffic). Wenn die Bannerfunktion also nicht verwendet wird, wird empfohlen, die Ausgabe des Adobe Commerce-Bannermoduls ](/help/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.md) vollständig zu deaktivieren und den Patch anzuwenden, um das Abrufen von Kundeninformationen zu verbessern.[

## Patch

Der Patch ist an diesen Artikel angehängt. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link:

[Laden Sie MDVA-24597\_EE\_2.2.9\_COMPOSER\_v1.patch herunter.](assets/MDVA-24597_EE_2.2.9_COMPOSER_v1.patch.zip)

### Kompatible Adobe Commerce-Versionen

Der Patch gilt für die folgenden Produkte und Versionen:

* Adobe Commerce auf Cloud-Infrastruktur 2.2.9
* Adobe Commerce vor Ort 2.2.9

Wenn Sie eine andere Version von Adobe Commerce haben, sollten Sie erwägen, auf die neueste Version 2.3.x zu aktualisieren. Wenn dies derzeit keine Option ist, wenden Sie sich bitte an den Adobe Commerce-Support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) und fordern Sie einen Patch für Ihre Version an.[

## Anwenden des Pflasters

Anweisungen finden Sie unter [Anwenden eines von Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) bereitgestellten Composer-Patches.

## Attached Files
