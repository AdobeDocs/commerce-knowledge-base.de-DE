---
title: laminas/laminas-escaper 2.7.1 verursacht Fehler auf Adobe Commerce Frontend- und Admin-Seiten
description: Dieser Artikel bietet eine Lösung für das Problem, dass die Veröffentlichung von laminas/laminas-escaper:2.7.1 die Funktionalität von Adobe Commerce in der Produktverwaltung, in Kategorien und auf Produktseiten beeinträchtigt. Dieses Problem wird in Adobe Commerce 2.4.3 behoben.
exl-id: 89de6827-7b90-4f08-92fb-56ed31ae2672
feature: Admin Workspace, Categories
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# laminas/laminas-escaper 2.7.1 verursacht Fehler auf Adobe Commerce Frontend- und Admin-Seiten


## Betroffene Produkte und Versionen

* Adobe Commerce auf unserer Cloud-Architektur 2.3.5+
* Adobe Commerce 2.3.5+

## Problem

Nach der Aktualisierung auf laminas/laminas-escaper:2.7.1 wird eine Fehlermeldung auf der Seite angezeigt.

<u>Schritte zur Reproduktion</u>:

Aktualisieren Sie laminas/laminas-escaper auf 2.7.1.

<u>Erwartetes Ergebnis</u>:

Kein Fehler.

<u>Tatsächliches </u>:

Nach der Aktualisierung auf laminas/laminas-escaper:2.7.1 wird eine Fehlermeldung auf einer Seite zur Produktbearbeitung (oder Produktverwaltung) angezeigt: *TypeError: rawurlencode() erwartet, dass Parameter 1 eine Zeichenfolge ist, int angegeben in /var/www/magento/vendor/laminas/laminas-escaper/src/Escaper.php:246*
Dieser Fehler tritt auf den Frontend- und Admin-Seiten auf, wodurch der Inhalt der Seite verzerrt wird.

## Ursache

laminas/laminas-escaper 2.7.1 begann mit der strikten Typvalidierung für die Escaper-Klasse.

## Lösung

Führen Sie `composer require laminas/laminas-escaper:2.7.0` im Stammverzeichnis jedes Projekts aus.

## Verwandtes Lesen

Laminas Dokumentation: [laminas-escaper](https://docs.laminas.dev/laminas-escaper/)
