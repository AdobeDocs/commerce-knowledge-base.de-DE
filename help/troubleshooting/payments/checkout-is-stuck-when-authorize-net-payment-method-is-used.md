---
title: Der Checkout ist blockiert, wenn die Zahlungsmethode Authorize.net verwendet wird
description: Dieser Artikel enthält eine Erklärung und Fehlerbehebung für das Adobe Commerce 2.3.x-Problem, bei dem der Checkout hängen bleibt, wenn Authorize.net verwendet wird, mit der Fehlermeldung *'Cannot read property 'length' of null'* im Browser-Konsolenprotokoll.
exl-id: 01dc1147-4010-4dc5-81f3-3b3015a8c47c
feature: Cache, Checkout, Console, Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: c4af0798-d497-5e6b-8380-19812c26d00a
    internal-label: Console
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%
---
# Der Checkout ist blockiert, wenn die Zahlungsmethode Authorize.net verwendet wird

Dieser Artikel enthält eine Erklärung und Fehlerbehebung für das Adobe Commerce 2.3.x-Problem, bei dem der Checkout hängen bleibt, wenn Authorize.net verwendet wird, mit der Fehlermeldung *Cannot read property &#39;length&#39; of null* im Protokoll der Browser-Konsole.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.3.x

>[!NOTE]
>
>Die zentrale Adobe Commerce Authorize.Net-Zahlungsintegration ist seit 2.3.4 veraltet und wurde in 2.4.0 vollständig entfernt. Verwenden Sie stattdessen eine Erweiterung, die Ihren Anforderungen entspricht, über die [Adobe Commerce [!DNL Marketplace]](https://commercemarketplace.adobe.com/).

## Problem

<u>Schritte zur Reproduktion</u>

1. Konfigurieren Sie die Zahlungsmethode Authorize.net in der Commerce Admin Console.
1. Geh zum Laden.
1. Fügen Sie ein Produkt zum Warenkorb hinzu und fahren Sie mit der Kasse fort.
1. Wählen Sie Authorize.net als Zahlungsmethode.
1. Klicken Sie **Bestellung aufgeben**.

<u>Erwartetes Ergebnis</u>

Der iframe Authorize.net wird geladen.

<u>Tatsächliches Ergebnis</u>

Ajax-Spinner wird angezeigt, und die Seite wird nie geladen. Der folgende JS-Fehler wird im Protokoll der Browser-Konsole angezeigt: *&#39;Uncatch TypeError: Die Eigenschaft &#39;length&#39; von null kann bei b nicht gelesen werden (jstest.authorize.net/v1/AcceptCore.js:1)&#39;*

## Ursache

Einer der häufigsten Gründe für dieses Problem ist, dass der öffentliche Clientschlüssel in der Authorize.Net-Konfiguration in Commerce Admin nicht angegeben ist.

## Lösung

Überprüfen Sie unter **Stores** > **Settings** > **Configuration** > **Sales** > **Payment Methods** im Abschnitt **authorize.net**, ob der Wert im **Public Client Key**-Feld angegeben ist. Wenn es leer ist, geben Sie den Schlüsselwert aus Ihrem Authorize.Net-Händlerkonto ein.

Damit die Änderungen angewendet werden können, bereinigen Sie den Cache, indem Sie Folgendes ausführen

```bash
bin/magento cache:clean
```
