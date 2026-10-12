---
title: 'FEHLER: Aufwärmen in Adobe Commerce auf Cloud-Infrastruktur fehlgeschlagen'
description: 'Dieser Artikel bietet eine Lösung für den Fall, dass der Seiten-Cache sich aufwärmt und mit einem Fehler fehlschlägt:'
exl-id: 20a88030-b1c9-4fdc-83c1-f344d44cd2e1
feature: Cache, Cloud, Paas
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '213'
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

* [Adobe Commerce-Benutzerhandbuch > Vollseitiger Cache](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/tools/cache-management#full-page-caching) in unserem Benutzerhandbuch.
* [Cache-Aufwärmung und Site auf Adobe Commerce nicht verfügbar](/help/troubleshooting/miscellaneous/cache-warming-up-and-site-unavailable-on-magento.md) in unserer Support-Wissensdatenbank.
