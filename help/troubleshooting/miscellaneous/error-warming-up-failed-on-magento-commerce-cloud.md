---
title: "FEHLER: Aufwärmen in Adobe Commerce in Cloud-Infrastruktur fehlgeschlagen"
description: "Dieser Artikel bietet eine Lösung für den Fall, dass sich der Seiten-Cache erwärmt und mit einem Fehler fehlschlägt:"
exl-id: 20a88030-b1c9-4fdc-83c1-f344d44cd2e1
feature: Cache, Cloud, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# FEHLER: Aufwärmen in Adobe Commerce in Cloud-Infrastruktur fehlgeschlagen

Dieser Artikel bietet eine Lösung für den Fall, dass der Seiten-Cache wärmer wird und mit einem Fehler fehlschlägt:

*FEHLER: Aufwärmen fehlgeschlagen:`<website link>`*

## Betroffene Produkte und Versionen

* Adobe Commerce in der Cloud-Infrastruktur, alle [unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problem

Cache-Warmup-Fehler.

<u>Zu reproduzierende Schritte</u>:

Starten Sie Aufwärmvorgänge für den Cache.

<u>Erwartetes Ergebnis</u>:

Seiten oder die gesamte Site werden geladen.

<u>Tatsächliches Ergebnis</u>:

Die Site ist nicht verfügbar oder die Antwortzeit ist zu hoch. *FEHLER: Aufwärmen fehlgeschlagen:`<website link>`*

## Ursache

Die Cache-Aktualisierung funktioniert nicht, wenn die HTTP-Zugriffssteuerung aktiviert ist.

## Lösung

Vergewissern Sie sich, dass die Zugriffskontrolle nicht aktiviert ist: Wechseln Sie zur jeweiligen Verzweigung/Umgebung und klicken Sie auf das Symbol &quot;**Einstellungen**&quot;. Aktivieren Sie die Einstellung &quot;**HTTP-Zugriffssteuerung**&quot;. In diesem Szenario kann keine Aktualisierung des Cache vorgenommen werden. Die Zugriffssteuerung muss deaktiviert werden.

## Verwandtes Lesen

* [Adobe Commerce-Benutzerhandbuch > Vollseiten-Cache](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management#full-page-caching) in unserem Benutzerhandbuch.
* [Caching-Erwärmung und Site nicht verfügbar auf Adobe Commerce](/help/troubleshooting/miscellaneous/cache-warming-up-and-site-unavailable-on-magento.md) in unserer Support-Wissensdatenbank.
