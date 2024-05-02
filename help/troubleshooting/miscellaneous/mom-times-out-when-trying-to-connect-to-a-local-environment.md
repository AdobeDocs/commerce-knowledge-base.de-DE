---
title: Zeitüberschreitung des Magento Order Management-Systems (OMS) für Adobe Commerce
description: Dieser Artikel bietet eine Lösung für das Problem, dass das Magento Order Management-System (OMS) für Adobe Commerce den lokal installierten Microservice nicht mit MOM mit ngrok registrieren kann, da MOM beim Versuch, einen Rückruf vorzunehmen, eine Zeitüberschreitung aufweist.
exl-id: 19149d8c-ea24-46fb-8815-9f637afe46ca
feature: System
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# Zeitüberschreitung des Magento Order Management-Systems (OMS) für Adobe Commerce

Dieser Artikel bietet eine Lösung für das Problem, dass das Magento Order Management-System (OMS) für Adobe Commerce den lokal installierten Microservice nicht mit MOM mit ngrok registrieren kann, da MOM beim Versuch, einen Rückruf vorzunehmen, eine Zeitüberschreitung aufweist.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.3.1
* OMS
* ngrok

>[!WARNING]
>
>Haftungsausschluss: Adobe Commerce empfiehlt oder unterstützt kein bestimmtes Instrument zur Tunnelerstellung. Die vorhergehenden sind nur Vorschläge. Weitere Informationen finden Sie im [ngrok-Dokumentation](https://ngrok.com/docs).

## Problem

<u>Zu reproduzierende Schritte</u>

1. Installieren Sie Adobe Commerce in Ihrer lokalen Umgebung.
1. Richten Sie ngrok ein, um einen Tunnel zu erstellen und Ihren lokalen Server verfügbar zu machen.
1. Probieren [Verbindung zu OMS](https://omsdocs.magento.com/en/integration/connector/setup-tutorial/).

<u>Erwartetes Ergebnis</u>

Verbindung erfolgreich hergestellt.

<u>Tatsächliches Ergebnis</u>

MCOM scheint eine Zeitüberschreitung zu haben, wenn versucht wird, auf die ngrok-URL zurückzurufen.

## Ursache

Einer der möglichen Gründe für die Zeitüberschreitung ist, dass Server geografisch zu weit entfernt sind und die Verbindung zu viel Zeit in Anspruch nimmt.

## Lösung

Fügen Sie beim Starten von ngrok einen Parameter hinzu, der Ihre Region angibt. Wie:

```bash
./ngrok http 80 -region eu
```

Die Standardregion ist US. Siehe [alle möglichen Werte](https://ngrok.com/docs#config_region).
