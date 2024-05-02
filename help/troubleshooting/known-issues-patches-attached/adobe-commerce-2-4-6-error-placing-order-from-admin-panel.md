---
title: Adobe Commerce 2.4.6-Fehlerplatzierung von Bestellungen aus dem Admin-Bedienfeld
description: Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce-Problem in der Cloud-Infrastruktur 2.4.6, wenn Sie bei der Store-Auswahl hängen bleiben, nachdem Sie eine Bestellung über das Commerce-Admin-Bedienfeld aufgegeben haben.
feature: Admin Workspace
role: Developer
exl-id: b30be5a5-3681-41db-9040-3624faed7c46
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# Adobe Commerce 2.4.6-Fehlerplatzierung von Bestellungen aus dem Admin-Bedienfeld

Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce-Problem in der Cloud-Infrastruktur 2.4.6, wenn Sie bei der Store-Auswahl hängen bleiben, nachdem Sie eine Bestellung über das Commerce-Admin-Bedienfeld aufgegeben haben.

## Problem

Wenn Sie eine Bestellung über das Admin-Bedienfeld aufgeben, bleiben Sie bei der Store-Auswahl hängen.

<u>Zu reproduzierende Schritte</u>

1. Navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Orders]** und wählen Sie einen Kunden aus, um eine Bestellung zu erstellen.
2. Wählen Sie den Store aus, um die Bestellung im Bildschirm &quot;Store-Auswahl&quot;zu platzieren.

<u>Erwartetes Ergebnis</u>

Nach Auswahl des Stores können Sie die Bestellung abschließen.

<u>Ergebnis:</u>

Nachdem Sie den Store ausgewählt haben, werden Sie zurück zur Store-Auswahlseite weitergeleitet und Sie können keine Bestellung erstellen.

## Patch

Klicken Sie auf den folgenden Link, um den Patch herunterzuladen.

[ACSD-52277_2.4.6.patch herunterladen](assets/ACSD-52277_2.4.6.patch.zip)

### Kompatible Adobe Commerce-Versionen

Der Patch wurde für und kompatibel mit Adobe Commerce in Cloud-Infrastruktur und Adobe Commerce in lokalen Betrieben 2.4.6 und 2.4.6-p1 erstellt.

## Anwenden des Pflasters

* Anweisungen zum Anwenden von Patches für Adobe Commerce auf Cloud-Infrastruktur finden Sie unter [Anwenden von Patches](/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in unserem Commerce on Cloud Infrastructure Guide.
* Eine Anleitung zur Anwendung von Patches für Adobe Commerce vor Ort finden Sie unter [Anwenden von Patches](/docs/commerce-operations/upgrade-guide/patches/apply.html?lang=en#composer) in unserem Commerce Upgrade-Handbuch.
