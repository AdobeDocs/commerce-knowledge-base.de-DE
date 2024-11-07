---
title: "Adobe Commerce 2.4.1: leere Seite beim Speichern des digitalen Seitenaufbaus"
description: Dieser Artikel bietet eine Behelfslösung für ein bekanntes Problem in Adobe Commerce 2.4.1, bei dem bei Verwendung des Safari-Browsers eine leere Webseite angezeigt wird, nachdem ein dotdigital Page Builder -Formular im Admin Panel gespeichert wurde.
exl-id: 682eac73-1ad2-4093-acfb-6a8da4c05cf5
feature: Page Builder
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# Adobe Commerce 2.4.1: leere Seite beim Speichern des Digital Page Builder-Formulars

Dieser Artikel bietet eine Behelfslösung für ein bekanntes Problem in Adobe Commerce 2.4.1, bei dem bei Verwendung des Safari-Browsers eine leere Webseite angezeigt wird, nachdem ein dotdigital Page Builder -Formular im Admin Panel gespeichert wurde.

## Betroffene Produkte und Versionen

* Adobe Commerce vor Ort 2.4.1
* Adobe Commerce in Cloud-Infrastruktur 2.4.1

## Problem

<u>Zu reproduzierende Schritte</u>

1. Wechseln Sie zu **Admin-Bedienfeld** > **Inhalt** > **Seiten** und wählen Sie **Bearbeiten** einer beliebigen Seite aus.
1. Wechseln Sie zu **Inhalt** und klicken Sie auf die Schaltfläche **Mit Seitenaufbau bearbeiten** .
1. Ziehen Sie den Block **dotdigital form** und wählen Sie **Edit** aus.
1. Wählen Sie eines der Testformulare aus, wählen Sie dann den Modus **Eingebettet** und speichern Sie das Formular.
1. Speichern Sie die Seitenänderung.

<u>Erwartetes Ergebnis:</u>

Die Webseite sollte erfolgreich gespeichert werden.

<u>Tatsächliches Ergebnis:</u>

Die Webseite ist leer. Nach dem erneuten Laden der Webseite werden die Änderungen übernommen.

## Workaround

Die Lösung besteht darin, einen alternativen Browser zu Safari zu verwenden. Das Problem wird in der nächsten Version, Adobe Commerce 2.4.2, im 1. Quartal 2021 behoben.

## Verwandtes Lesen

* [Was ist Page Builder?](https://developer.adobe.com/commerce/frontend-core/page-builder/) in unserer Entwicklerdokumentation.
* [Einrichten des Seitenaufbaus](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/setup.html) in unserer Entwicklerdokumentation.
* [Seitenaufbau](https://experienceleague.adobe.com/en/docs/commerce-admin/page-builder/introduction) in unserem Benutzerhandbuch.
* [Seitenaufbau - Elemente](https://experienceleague.adobe.com/en/docs/commerce-admin/page-builder/workspace#elements) in unserem Benutzerhandbuch.
