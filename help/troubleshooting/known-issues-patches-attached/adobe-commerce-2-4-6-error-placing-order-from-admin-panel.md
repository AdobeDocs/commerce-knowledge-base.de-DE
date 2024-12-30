---
title: Adobe Commerce 2.4.6 Fehler bei der Bestellung im Admin-Bedienfeld
description: Dieser Artikel enthält einen Patch für das bekannte Problem Adobe Commerce on Cloud Infrastructure 2.4.6, wenn Sie bei der Store-Auswahl hängen bleiben, nachdem Sie eine Bestellung über das Commerce Admin-Bedienfeld aufgegeben haben.
feature: Admin Workspace
role: Developer
exl-id: b30be5a5-3681-41db-9040-3624faed7c46
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# Adobe Commerce 2.4.6 Fehler bei der Bestellung im Admin-Bedienfeld

Dieser Artikel enthält einen Patch für das bekannte Problem Adobe Commerce on Cloud Infrastructure 2.4.6, wenn Sie bei der Store-Auswahl hängen bleiben, nachdem Sie eine Bestellung über das Commerce Admin-Bedienfeld aufgegeben haben.

## Problem

Wenn Sie eine Bestellung im Admin-Bedienfeld aufgeben, bleiben Sie bei der Store-Auswahl hängen.

<u>Schritte zur Reproduktion</u>

1. Gehen Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Orders]** und wählen Sie einen Kunden aus, um eine Bestellung zu erstellen.
2. Wählen Sie im Bildschirm „Store Selector“ den Store aus, um die Bestellung aufzugeben.

<u>Erwartetes Ergebnis</u>

Nachdem Sie den Store ausgewählt haben, können Sie die Bestellung abschließen.

<u>Tatsächliches Ergebnis:</u>

Nachdem Sie den Store ausgewählt haben, werden Sie zurück zur Store-Auswahlseite weitergeleitet, und Sie können keine Bestellung erstellen.

## Fleck

Klicken Sie auf den folgenden Link, um den Patch herunterzuladen.

[Herunterladen von ACSD-52277_2.4.6.patch](assets/ACSD-52277_2.4.6.patch.zip)

### Kompatible Adobe Commerce-Versionen

Der Patch wurde für Adobe Commerce on Cloud Infrastructure und Adobe Commerce On-Premises 2.4.6 und 2.4.6-p1 erstellt und ist mit diesen kompatibel.

## Anbringen des Pflasters

* Anweisungen zum Anwenden von Patches für Adobe Commerce auf die Cloud-Infrastruktur finden Sie [Anwenden von Patches](/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in unserem Handbuch zu Commerce auf Cloud-Infrastruktur.
* Anweisungen zum Anwenden von Patches für Adobe Commerce On-Premise finden Sie [Anwenden von Patches](/docs/commerce-operations/upgrade-guide/patches/apply.html?lang=en#composer) in unserem Commerce-Upgrade-Handbuch.
