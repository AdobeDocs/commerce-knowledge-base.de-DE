---
title: Anzeigen der vCPU-Umgebungsebene in Ihrem Cluster auf Adobe Commerce
promoted: true
description: In diesem Artikel wird erläutert, wie Sie Ihre vCPU-Stufenzuordnung mithilfe der Registerkarte New Relic Infra unter Beobachtung für Adobe Commerce überprüfen. Beobachtung für Adobe Commerce ist ein New Relic-Nerdlet, das den Zustand Ihrer Adobe Commerce-Site, aktuelle und vergangene Ansichten anzeigt.
exl-id: a0332e7e-d38d-47d3-b3da-293902f45edc
source-git-commit: 309fda5284de3b8be54e95bf2bfd8ff1777b6c90
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# Anzeigen der vCPU-Umgebungsebene in Ihrem Cluster auf Adobe Commerce

In diesem Artikel wird erläutert, wie Sie Ihre vCPU-Stufenzuordnung mithilfe der Registerkarte New Relic Infra unter Beobachtung für Adobe Commerce überprüfen. Beobachtung für Adobe Commerce ist ein New Relic-Nerdlet, das den Zustand Ihrer Adobe Commerce-Site, aktuelle und vergangene Ansichten anzeigt.

## Betroffene Produkte und Versionen:

Adobe Commerce auf Cloud-Infrastruktur 2.4.3 - 2.4.6

## Überprüfen Sie die vCPU-Stufenzuordnung mit der Beobachtung für Adobe Commerce:

So greifen Sie auf das Nerdlet New Relic Observation for Adobe Commerce zu und melden sich dort an:

1. Klicken Sie auf der New Relic-Startseite auf **Apps**.
1. Klicks **Beobachtung für Adobe Commerce**.
1. Die Beobachtung für das Adobe Commerce-Nerdlet wird geöffnet.
1. Klicken Sie auf **Konto auswählen** und wählen Sie ein Konto aus.
1. Sie können die Projekt-ID, die New Relic-Kontonummer oder den Kontonamen eingeben oder die Kontoliste durchsuchen.
1. Klicken Sie auf das hellblaue Dropdown-Menü mit dem Uhrensymbol (rechts oben im Nerdlet-Fenster).
1. Wenn Sie die Ursache eines Ereignisses/Problems ermitteln möchten, wählen Sie eine Zeit vor dem Ticketdatum und der Ticketzeit aus, um zu sehen, ob zuvor Ereignisse/Daten aufgetreten sind. Sie können die vorgegebenen Zeitrahmen verwenden oder einen benutzerdefinierten Zeitrahmen festlegen, indem Sie **Festlegen benutzerdefinierter**.
1. Klicken Sie auf den Registerkarten auf **Infra**. Es gibt drei Diagramme der vCPU-Ebene:
   * Das erste Diagramm zeigt **vCPU-Stufenansicht im Zeitleistensegment GRÖSSER 2 Wochen (Sie müssen eine Timeline auswählen, die GRÖSSER als 2 Wochen ist). HINWEIS: Die Stichprobenrate wird pro Tag berechnet. Wenn Cluster-Uploads/Downloads an einem Tag stattfinden, wird die Größe der Endstufe am folgenden Tag angezeigt**.
   * Das zweite Diagramm zeigt **vCPU-Stufenansicht über Zeitleiste (Zeitleistensegment muss GRÖSSER als 24 Stunden, aber nicht länger als 2 Wochen sein)**.
   * Das dritte Diagramm zeigt die **vCPU-Stufenansicht über Timeline BY NODE, sollte sich Timeline LESS than 24 Stunden ansehen**.

## Verwandtes Lesen

* [Beobachtung für Adobe Commerce - Übersicht](/help/support-tools/observation-for-adobe-commerce/observation-adobe-commerce-overview.md) in unserer Wissensdatenbank.
