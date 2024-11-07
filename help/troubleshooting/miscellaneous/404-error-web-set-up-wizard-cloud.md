---
title: Fehler 404 beim Zugriff auf den Web-Setup-Assistenten über das Admin-Bedienfeld nicht gefunden
description: Dieser Artikel bietet eine Lösung für den Fall, dass beim Versuch, über das Admin-Bedienfeld auf den Web-Setup-Assistenten zuzugreifen, ein Fehler vom Typ 404 (nicht gefunden) auftritt.
exl-id: 1b89da58-c872-481b-b2a0-aa48db8223db
feature: Admin Workspace, Cloud, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# Fehler 404 beim Zugriff auf den Web-Setup-Assistenten über das Admin-Bedienfeld nicht gefunden

Dieser Artikel bietet eine Lösung für den Fall, dass beim Versuch, über das Admin-Bedienfeld auf den Web-Setup-Assistenten zuzugreifen, ein Fehler vom Typ 404 (nicht gefunden) auftritt.

## Betroffene Produkte und Versionen

* Die Funktion des Websetup-Assistenten wurde in Adobe Commerce (alle Bereitstellungsmethoden) 2.3.6 eingestellt und in Version 2.4.0 entfernt.

## Problem

Bei der Installation einer Erweiterung mit dem Web-Einrichtungs-Assistenten wird eine Seite 404 angezeigt.

<u>Zu reproduzierende Schritte</u>:

Der Händler klickt auf den Web-Einrichtungs-Assistenten, um ein neues Modul/eine neue Integration zu installieren.

<u>Erwartetes Ergebnis</u>:

Module/Integration wird installiert.

<u>Tatsächliches Ergebnis</u>:

Es wird ein 404-Fehler angezeigt.

## Ursache

Der Web-Einrichtungs-Assistent wurde für alle Adobe Commerce-Instanzen in Cloud-Infrastrukturinstanzen deaktiviert. Es ist nicht möglich, ihn zu aktivieren. Erweiterungen müssen über Composer installiert werden.

## Lösung

Diese Funktion ist in Adobe Commerce in der Cloud-Infrastruktur deaktiviert.

Informationen zum Ausführen von Aktualisierungen oder Installieren externer Module für Adobe Commerce in unserer Cloud-Infrastruktur finden Sie unter [Installieren, Verwalten und Aktualisieren von Erweiterungen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/extensions) in unserer Entwicklerdokumentation.
Informationen zum Durchführen von Aktualisierungen oder Installieren externer Module für Adobe Commerce vor Ort finden Sie unter [Schnellstart-Installation](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/composer) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

* Siehe [Installieren einer Erweiterung](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/extensions#install-an-extension) in unserer Entwicklerdokumentation.
