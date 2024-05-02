---
title: Der manuelle Bestellexport nach MOM schlägt fehl. Die Schaltfläche "Auftrag exportieren"gibt den HTTP-404-Fehler zurück
description: In diesem Artikel wird erläutert, wie ein Problem behoben werden kann, bei dem beim Versuch, eine Bestellung in Magento Order Management (MOM) zu exportieren, durch Klicken auf die Schaltfläche "Bestellung exportieren"in der Bestellansicht im Commerce-Admin der Fehler "*404-Seite nicht gefunden*"zurückgegeben wird.
exl-id: 75741473-7c9a-4418-a56f-de75ac246d27
feature: Data Import/Export
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# Der manuelle Bestellexport nach MOM schlägt fehl. Die Schaltfläche &quot;Auftrag exportieren&quot;gibt den HTTP-404-Fehler zurück

In diesem Artikel wird beschrieben, wie Sie ein Problem beheben können, bei dem versucht wird, eine Bestellung nach Magento Order Management (MOM) zu exportieren, indem Sie auf das **Auftrag exportieren** -Schaltfläche in der Bestellansicht in Commerce Admin gibt einen &quot;&quot; *404 Seite nicht gefunden* &quot;.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.2.x, 2.3.x
* MOM Connector 2.3.0, 2.4.0, 3.2.0, 3.3.0

## Problem

<u>Zu reproduzierende Schritte:</u>:

1. Klicken Sie in Commerce Admin auf **Vertrieb > Bestellungen**.
1. Klicken Sie auf **Neue Bestellung erstellen** Schaltfläche.
1. Wählen Sie einen Benutzer aus, fügen Sie einen oder mehrere Artikel hinzu, wählen Sie die Zahlungs- und Versandmethoden aus und klicken Sie auf die Schaltfläche **Bestellung absenden** Schaltfläche.
1. Klicken Sie auf **Auftrag exportieren** Schaltfläche und dann **OK**.

<u>Erwartetes Ergebnis</u>:

Die Bestellung wird an MOM gesendet.

<u>Tatsächliches Ergebnis</u>:

A *404-Fehler: Seite nicht gefunden* angezeigt.

## Lösung

* Aktualisieren Sie den MOM-Connector auf 3.4.0 für Adobe Commerce 2.3.x oder MOM Connector 2.5 für Adobe Commerce 2.2.x.
* Wenn die Aktualisierung des MOM Connector nicht möglich ist, können Sie die Bestellung mithilfe des CLI-Befehls nach Magento Order Management exportieren:

```bash
$bin/magento oms:orders:sync
```

## Verwandtes Lesen

[Technische Dokumentation zu Magento Order Managements](https://omsdocs.magento.com/en/)
