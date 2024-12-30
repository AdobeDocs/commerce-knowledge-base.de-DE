---
title: Der Checkout ist blockiert, wenn die Zahlungsmethode Authorize.net verwendet wird
description: Dieser Artikel enthält eine Erklärung und Fehlerbehebung für das Adobe Commerce 2.3.x-Problem, bei dem der Checkout hängen bleibt, wenn Authorize.net verwendet wird, mit der Fehlermeldung *'Cannot read property 'length' of null'* im Browser-Konsolenprotokoll.
exl-id: 01dc1147-4010-4dc5-81f3-3b3015a8c47c
feature: Cache, Checkout, Console, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '285'
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
