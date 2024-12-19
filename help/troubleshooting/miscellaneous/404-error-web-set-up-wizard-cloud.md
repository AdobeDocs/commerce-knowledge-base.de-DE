---
title: 404 Fehler „Nicht gefunden“ beim Zugriff auf den Websetup-Assistenten über das Admin-Bedienfeld
description: Dieser Artikel bietet eine Lösung für den Fall, dass beim Versuch, über das Admin-Bedienfeld auf den Websetup-Assistenten zuzugreifen, der Fehler 404 Nicht gefunden angezeigt wird.
exl-id: 1b89da58-c872-481b-b2a0-aa48db8223db
feature: Admin Workspace, Cloud, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# 404 Fehler „Nicht gefunden“ beim Zugriff auf den Websetup-Assistenten über das Admin-Bedienfeld

Dieser Artikel bietet eine Lösung für den Fall, dass beim Versuch, über das Admin-Bedienfeld auf den Websetup-Assistenten zuzugreifen, der Fehler 404 Nicht gefunden angezeigt wird.

## Betroffene Produkte und Versionen

* Die Funktion Websetup-Assistent wird in Adobe Commerce (alle Bereitstellungsmethoden) 2.3.6 nicht mehr unterstützt und in 2.4.0 entfernt.

## Problem

Beim Installieren einer Erweiterung mithilfe des Websetup-Assistenten wird eine 404-Seite angezeigt.

<u>Schritte zur Reproduktion</u>:

Der Händler klickt auf den Websetup-Assistenten, um ein neues Modul/eine neue Integration zu installieren.

<u>Erwartetes Ergebnis</u>:

Module/Integrationen werden installiert.

<u>Tatsächliches </u>:

Ein 404-Fehler wird angezeigt.

## Ursache

Der Websetup-Assistent wurde für alle Adobe Commerce auf Cloud-Infrastrukturinstanzen deaktiviert. Er kann nicht aktiviert werden. Erweiterungen müssen über Composer installiert werden.

## Lösung

Diese Funktion ist in Adobe Commerce in der Cloud-Infrastruktur deaktiviert.

Siehe [Installieren, Verwalten und Aktualisieren von Erweiterungen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/extensions) in unserer Entwicklerdokumentation, um Informationen zum Ausführen von Aktualisierungen oder Installieren externer Module für Adobe Commerce in unserer Cloud-Infrastruktur zu erhalten.
Informationen [ Ausführen von Aktualisierungen oder Installieren externer Module ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/composer) Adobe Commerce On-Premise finden Sie in unserer Entwicklerdokumentation unter „Schnellstartanleitung“.

## Verwandtes Lesen

* Siehe [Installieren einer Erweiterung](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/extensions#install-an-extension) in unserer Entwicklerdokumentation.
