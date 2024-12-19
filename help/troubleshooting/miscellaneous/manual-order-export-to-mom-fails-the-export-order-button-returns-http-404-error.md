---
title: Der manuelle Bestellungsexport nach MOM schlägt fehl. Die Schaltfläche „Exportreihenfolge“ gibt den HTTP 404-Fehler zurück
description: In diesem Artikel wird beschrieben, wie Sie ein Problem beheben können, bei dem der Versuch, eine Bestellung in Magento Order Management (MOM) zu exportieren, indem Sie in der Auftragsansicht in der Commerce-Admin auf die Schaltfläche **Exportreihenfolge** klicken, den Fehler "*404 Page Not Found* " zurückgibt.
exl-id: 75741473-7c9a-4418-a56f-de75ac246d27
feature: Data Import/Export
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# Der manuelle Bestellungsexport nach MOM schlägt fehl. Die Schaltfläche „Exportreihenfolge“ gibt den HTTP 404-Fehler zurück

In diesem Artikel wird beschrieben, wie Sie ein Problem beheben können, bei dem der Versuch, eine Bestellung in Magento Order Management (MOM) zu exportieren, indem Sie auf die Schaltfläche **Exportreihenfolge** in der Auftragsansicht in Commerce Admin klicken und den Fehler &quot;*404 Page Not Found* &quot; zurückgeben.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.2.x, 2.3.x
* MOM-Connector 2.3.0, 2.4.0, 3.2.0, 3.3.0

## Problem

<u>Schritte zur Reproduktion:</u>:

1. Klicken Sie in Commerce Admin auf **Verkauf > Bestellungen**.
1. Klicken Sie auf **Schaltfläche „Neuen Auftrag erstellen**.
1. Wählen Sie einen Benutzer aus, fügen Sie Artikel hinzu, wählen Sie Zahlungs- und Versandmethoden aus und klicken Sie auf die Schaltfläche **Bestellung**.
1. Klicken Sie auf **Exportreihenfolge** und dann auf **OK**.

<u>Erwartetes Ergebnis</u>:

Die Bestellung wird an MOM gesendet.

<u>Tatsächliches </u>:

Es wird die Seite &quot;*404 error: page not found* &quot; angezeigt.

## Lösung

* Aktualisieren Sie den MOM-Connector auf 3.4.0 für Adobe Commerce 2.3.x oder den MOM-Connector 2.5 für Adobe Commerce 2.2.x.
* Wenn ein Upgrade des MOM-Connectors nicht möglich ist, können Sie die Bestellung mithilfe des CLI-Befehls in das Magento Order Management exportieren:

```bash
$bin/magento oms:orders:sync
```

## Verwandtes Lesen

Technische Dokumentation zu [Magento Order Management](https://commerce-docs.github.io/oms-documentation-archive/)
