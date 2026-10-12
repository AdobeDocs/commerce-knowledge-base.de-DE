---
title: Installation xdebug Fehler für maximale Verschachtelungsebene der Funktion
description: Dieser Artikel enthält eine Fehlerbehebung für den Fehler der maximalen Verschachtelungsebene der xdebug-Funktion während der Installation.
exl-id: 1f64a9bb-59a7-41df-92a4-890d9d32bcbe
feature: Install
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 0%
---
# Installation xdebug Fehler für maximale Verschachtelungsebene der Funktion

Dieser Artikel enthält eine Fehlerbehebung für den Fehler der maximalen Verschachtelungsebene der xdebug-Funktion während der Installation.

## Details

Während der Installation von Adobe Commerce wird eine Meldung ähnlich der folgenden angezeigt:

`PHP Fatal error: Maximum function nesting level of '100' reached, aborting! in <path>/ClassLoader.php`

Es wird dringend empfohlen, `xdebug` NICHT in einer Produktionsumgebung zu verwenden!

## Lösung

Es gibt ein bekanntes Problem mit `xdebug`, das sich nach der Installation auf Adobe Commerce-Installationen oder den Zugriff auf die Storefront oder Commerce Admin auswirken kann.

Weitere Informationen finden Sie unter [Bekanntes Problem mit xdebug](/help/troubleshooting/miscellaneous/known-issues-that-affect-installation.md) in unserer Support-Wissensdatenbank.
