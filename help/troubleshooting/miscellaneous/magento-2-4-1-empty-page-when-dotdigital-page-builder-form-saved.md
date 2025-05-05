---
title: 'Adobe Commerce 2.4.1: Leere Seite beim Speichern des dotdigital Page Builder-Formulars'
description: Dieser Artikel bietet eine Problemumgehung für ein bekanntes Problem in Adobe Commerce 2.4.1, um nach dem Speichern eines dotdigital Page Builder-Formulars im Admin Panel eine leere Webseite anzuzeigen, wenn der Safari-Browser verwendet wird.
exl-id: 682eac73-1ad2-4093-acfb-6a8da4c05cf5
feature: Page Builder
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# Adobe Commerce 2.4.1: Leere Seite beim Speichern des dotdigital Page Builder-Formulars

Dieser Artikel bietet eine Problemumgehung für ein bekanntes Problem in Adobe Commerce 2.4.1, um nach dem Speichern eines dotdigital Page Builder-Formulars im Admin Panel eine leere Webseite anzuzeigen, wenn der Safari-Browser verwendet wird.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premises 2.4.1
* Adobe Commerce auf Cloud-Infrastruktur 2.4.1

## Problem

<u>Schritte zur Reproduktion</u>

1. Wechseln Sie zu **Admin** > **Inhalt** > **Seiten** und wählen Sie **Bearbeiten** einer beliebigen Seite.
1. Wechseln Sie zu **Inhalt** und klicken Sie auf die Schaltfläche **Bearbeiten mit Page Builder**.
1. Ziehen Sie den **dotdigital** Block und wählen Sie **Bearbeiten**.
1. Wählen Sie eines der Testformulare aus, wählen Sie dann **Eingebetteter** Modus aus und speichern Sie das Formular.
1. Speichern Sie die Seitenänderung.

<u>Erwartetes Ergebnis:</u>

Die Web-Seite sollte erfolgreich gespeichert werden.

<u>Tatsächliches Ergebnis:</u>

Die Webseite ist leer. Nach dem Neuladen der Web-Seite werden die Änderungen angewendet.

## Abhilfe

Die Lösung besteht darin, einen alternativen Browser zu Safari zu verwenden. Das Problem wird voraussichtlich in der nächsten Version, Adobe Commerce 2.4.2, im 1. Quartal 2021 behoben.

## Verwandtes Lesen

* [Was ist Page Builder?](https://developer.adobe.com/commerce/frontend-core/page-builder/) in unserer Entwicklerdokumentation.
* [Page Builder-Setup](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/setup.html?lang=de) in unserer Entwicklerdokumentation.
* [Page Builder](https://experienceleague.adobe.com/de/docs/commerce-admin/page-builder/introduction) in unserem Benutzerhandbuch.
* [Page Builder - Elemente](https://experienceleague.adobe.com/de/docs/commerce-admin/page-builder/workspace#elements) in unserem Benutzerhandbuch.
