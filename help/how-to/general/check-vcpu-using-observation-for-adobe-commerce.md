---
title: Anzeigen der vCPU-Ebene der Umgebung in Ihrem Cluster auf Adobe Commerce
promoted: true
description: In diesem Artikel wird erläutert, wie Sie die Zuordnung Ihrer vCPU-Ebene mithilfe der New Relic-Registerkarte „Infra“ unter „Observation for Adobe Commerce" überprüfen. Observation for Adobe Commerce ist ein New Relic-Nerdlet, das den Status Ihrer Adobe Commerce-Site, aktuelle und vergangene Zeitansichten anzeigt.
exl-id: a0332e7e-d38d-47d3-b3da-293902f45edc
source-git-commit: ffb7b597d38eaed4b66e23ea533c275746e7181a
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# Anzeigen der vCPU-Ebene der Umgebung in Ihrem Cluster auf Adobe Commerce

In diesem Artikel wird erläutert, wie Sie die Zuordnung Ihrer vCPU-Ebene mithilfe der New Relic-Registerkarte „Infra“ unter „Observation for Adobe Commerce&quot; überprüfen. Observation for Adobe Commerce ist ein New Relic-Nerdlet, das den Status Ihrer Adobe Commerce-Site, aktuelle und vergangene Zeitansichten anzeigt.

## Betroffene Produkte und Versionen:

Adobe Commerce auf Cloud-Infrastruktur 2.4.3 - 2.4.6

## vCPU-Stufenzuordnung mit Observation für Adobe Commerce überprüfen:

So greifen Sie auf das Nerdlet New Relic Observation for Adobe Commerce zu und melden sich dort an:

1. Klicken Sie auf der New Relic-Startseite auf **Apps**.
1. Klicken Sie auf **Observation for Adobe Commerce**.
1. Das Nerdlet „Beobachtung für Adobe Commerce&quot; wird geöffnet.
1. Klicken Sie auf die **Konto auswählen** und wählen Sie ein Konto aus.
1. Sie können die Projekt-ID, die New Relic-Kontonummer oder den Kontonamen ausfüllen oder die Liste der Konten durchsuchen.
1. Klicken Sie auf das hellblaue Dropdown-Menü mit dem Uhrensymbol (oben rechts im Nerdlet-Fenster).
1. Wenn Sie versuchen, die Ursache eines Ereignisses/Problems zu ermitteln, wählen Sie eine Zeit vor dem Ticketdatum und der Ticketzeit aus, um festzustellen, ob zuvor Ereignisse/Daten vorhanden waren. Sie können die voreingestellten Zeitrahmen verwenden oder einen benutzerdefinierten Zeitrahmen festlegen, indem Sie **Benutzerdefiniert festlegen** auswählen.
1. Klicken Sie auf den Registerkarten **Infra**. Es gibt drei vCPU-Stufen-Diagramme:
   * Das erste Diagramm zeigt **vCPU-Stufenansicht über der Zeitleiste von MEHR als 2 Wochen (Sie müssen eine Zeitleiste von MEHR als 2 Wochen auswählen). HINWEIS: Die Stichprobenrate beträgt pro Tag. Wenn Cluster-Upsizes/-Downsises an einem Tag erfolgen, wird die End-Tier-Größe am folgenden Tag angezeigt**.
   * Das zweite Diagramm zeigt die **vCPU-Stufenansicht über der Zeitleiste (Sie müssen eine Zeitleiste auswählen, die länger als 24 Stunden, aber nicht länger als 2 Wochen ist)**.
   * Das dritte Diagramm zeigt die **vCPU-Stufenansicht über der Zeitleiste nach KNOTEN, sollte die Zeitleiste von weniger als 24 Stunden**.
