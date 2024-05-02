---
title: Beim Auschecken ist hängengeblieben, wenn Authorize.net Zahlungsmethode verwendet wird
description: Dieser Artikel enthält eine Erklärung und eine Korrektur für das Adobe Commerce 2.3.X-Problem, bei dem der Checkout hängenbleibt, wenn Authorize.net verwendet wird, mit der Fehlermeldung *'Cannot read property 'length' of null'* im Browser-Konsolenprotokoll.
exl-id: 01dc1147-4010-4dc5-81f3-3b3015a8c47c
feature: Cache, Checkout, Console, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Beim Auschecken ist hängengeblieben, wenn Authorize.net Zahlungsmethode verwendet wird

Dieser Artikel enthält eine Erklärung und eine Korrektur für das Adobe Commerce 2.3.X-Problem, bei dem der Checkout hängenbleibt, wenn Authorize.net verwendet wird, wobei die Variable *&quot;Cannot read property &#39;length&#39; of null&quot;* Fehlermeldung im Browser-Konsolenprotokoll.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.3.X

>[!NOTE]
>
>Die Adobe Commerce-Zahlungsintegration &quot;Authorize.Net&quot;ist seit 2.3.4 veraltet und wurde in 2.4.0 vollständig entfernt. Verwenden Sie eine Erweiterung, die Ihren Anforderungen entspricht. Wählen Sie dazu die [Adobe Commerce [!DNL Marketplace]](https://commercemarketplace.adobe.com/) anstatt.

## Problem

<u>Zu reproduzierende Schritte</u>

1. Konfigurieren Sie die Zahlungsmethode Authorize.net in Commerce Admin.
1. Gehen Sie zur Storefront.
1. Fügen Sie ein Produkt zum Warenkorb hinzu und fahren Sie mit dem Checkout fort.
1. Wählen Sie Authorize.net als Zahlungsmethode aus.
1. Klicks **Bestellung platzieren**.

<u>Erwartetes Ergebnis</u>

Der iframe Authorize.net wird geladen.

<u>Tatsächliches Ergebnis</u>

Das Ajax-Netz wird angezeigt und die Seite wird nie geladen. Der folgende JS-Fehler wird im Browser-Konsolenprotokoll angezeigt: *&#39;Uncaught TypeError: Cannot read property &#39;length&#39; of null at b (jstest.authorize.net/v1/AcceptCore.js:1)&#39;)*

## Ursache

Einer der häufigsten Gründe für dieses Problem ist, dass der öffentliche Client-Schlüssel nicht in der Authorize.Net-Konfiguration in Commerce Admin angegeben ist.

## Lösung

under **Stores** > **Einstellungen** > **Konfiguration** > **Vertrieb** > **Zahlungsmethoden** in der **Authorize.net** überprüfen, ob der Wert im Abschnitt **Public Client Key** -Feld. Wenn dieser Wert leer ist, geben Sie den Schlüsselwert aus Ihrem Authorize.Net-Handelskonto ein.

Um die Änderungen anzuwenden, leeren Sie den Cache, indem Sie

```bash
bin/magento cache:clean
```
