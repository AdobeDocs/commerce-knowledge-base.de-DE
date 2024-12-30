---
title: 'FEHLER: Aufwärmen in Adobe Commerce auf Cloud-Infrastruktur fehlgeschlagen'
description: 'Dieser Artikel bietet eine Lösung für den Fall, dass der Seiten-Cache sich aufwärmt und mit einem Fehler fehlschlägt:'
exl-id: 20a88030-b1c9-4fdc-83c1-f344d44cd2e1
feature: Cache, Cloud, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# FEHLER: Aufwärmen in Adobe Commerce auf Cloud-Infrastruktur fehlgeschlagen

Dieser Artikel bietet eine Lösung für den Fall, dass der Seiten-Cache sich aufwärmt und mit einem Fehler fehlschlägt:

*FEHLER: Aufwärmen fehlgeschlagen:`<website link>`*

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur, alle [unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problem

Fehler beim Aufwärmen des Cache.

<u>Schritte zur Reproduktion</u>:

Starten Sie die Cache-Aufwärmvorgänge.

<u>Erwartetes Ergebnis</u>:

Seiten oder Ladevorgänge der gesamten Site.

<u>Tatsächliches </u>:

Die Site ist nicht verfügbar oder die Antwortzeit ist zu hoch. *FEHLER: Aufwärmen fehlgeschlagen:`<website link>`*

## Ursache

Das Aufwärmen des Cache funktioniert nicht mit aktivierter HTTP-Zugriffssteuerung.

## Lösung

Stellen Sie sicher, dass die Zugriffssteuerung nicht aktiviert ist: Wechseln Sie zu der jeweiligen Verzweigung/Umgebung, klicken Sie auf das Symbol **Einstellungen** und überprüfen Sie die Einstellung **HTTP-Zugriffssteuerung** - Cache-Aufwärmung kann in diesem Szenario nicht auftreten, und die Zugriffssteuerung muss deaktiviert sein.

## Verwandtes Lesen

* [Adobe Commerce-Benutzerhandbuch > Vollseitiger Cache](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management#full-page-caching) in unserem Benutzerhandbuch.
* [Cache-Aufwärmung und Site auf Adobe Commerce nicht verfügbar](/help/troubleshooting/miscellaneous/cache-warming-up-and-site-unavailable-on-magento.md) in unserer Support-Wissensdatenbank.
