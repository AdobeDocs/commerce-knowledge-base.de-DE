---
title: Zeitüberschreitung des Magento Order Management-Systems (OMS) für Adobe Commerce
description: Dieser Artikel bietet eine Lösung für das Problem, dass das Magento Order Management System (OMS) für Adobe Commerce den lokal installierten Microservice nicht mit ngrok bei MOM registrieren kann, da MOM beim Versuch, einen Rückruf durchzuführen, eine Zeitüberschreitung aufweist.
exl-id: 19149d8c-ea24-46fb-8815-9f637afe46ca
feature: System
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# Zeitüberschreitung des Magento Order Management-Systems (OMS) für Adobe Commerce

Dieser Artikel bietet eine Lösung für das Problem, dass das Magento Order Management System (OMS) für Adobe Commerce den lokal installierten Microservice nicht mit ngrok bei MOM registrieren kann, da MOM beim Versuch, einen Rückruf durchzuführen, eine Zeitüberschreitung aufweist.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.3.1
* OMS
* inGrok

>[!WARNING]
>
>Haftungsausschluss: Adobe Commerce empfiehlt oder unterstützt kein bestimmtes Tool für die Tunnelerstellung. Die zuvor genannten Vorschläge sind nur Empfehlungen. Weitere Informationen finden Sie in der [ngrok-Dokumentation](https://ngrok.com/docs).

## Problem

<u>Schritte zur Reproduktion</u>

1. Installieren Sie Adobe Commerce in Ihrer lokalen Umgebung.
1. Richten Sie Network ein, um einen Tunnel zu erstellen, um Ihren lokalen Server anzuzeigen.
1. Versuchen Sie [Verbindung mit OMS herstellen](https://commerce-docs.github.io/oms-documentation-archive/integration/connector/setup-tutorial/).

<u>Erwartetes Ergebnis</u>

Verbindung erfolgreich hergestellt.

<u>Tatsächliches Ergebnis</u>

MCOM scheint beim Versuch, einen Rückruf an die Netzwerk-URL durchzuführen, eine Zeitüberschreitung aufzutreten.

## Ursache

Einer der möglichen Gründe für die Zeitüberschreitung ist, dass Server geografisch zu weit entfernt sind und die Verbindung zu viel Zeit in Anspruch nimmt.

## Lösung

Fügen Sie beim Starten einer Gruppe einen Parameter hinzu, der Ihre Region angibt. Wie folgt:

```bash
./ngrok http 80 -region eu
```

Die Standardregion ist „US“. Siehe [alle möglichen Werte](https://ngrok.com/docs#config_region).
