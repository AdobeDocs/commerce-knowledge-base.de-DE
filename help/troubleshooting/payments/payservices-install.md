---
title: Fehlerbehebung bei der Installation von Zahlungsdiensten
description: In diesem Artikel werden Fehler erläutert, die bei der Installation von Zahlungsdiensten auftreten können, und es werden Lösungen zur Behebung dieser Fehler bereitgestellt, damit Sie die Installation abschließen können.
exl-id: 0aef7482-8834-400e-85b9-d3d3eb0ab76e
feature: Install, Orders, Payments, Saas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# Fehlerbehebung bei der Installation von Zahlungsdiensten

In diesem Artikel werden Fehler erläutert, die bei der Installation von Zahlungsdiensten auftreten können, und es werden Lösungen zur Behebung dieser Fehler bereitgestellt, damit Sie die Installation abschließen können.

## Betroffene Produkte und Versionen

* [Zahlungsdienste](https://marketplace.magento.com/magento-payment-services.html) ist jetzt mit den Adobe Commerce-Versionen 2.4.0 bis 2.4.4 kompatibel.

## Problem - Falsche Composer-Schlüssel

Bei der Installation der Zahlungsdienst-Erweiterung wird möglicherweise eine Fehlermeldung angezeigt, die besagt, dass Sie während der Installation falsche Composer-Schlüssel verwendet haben.

<u>Zu reproduzierende Schritte</u>:

1. Versuchen Sie, [Zahlungsdienste zu installieren](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html).
1. Siehe den folgenden Fehler:

   *Es konnte keine passende Version von Package Magento/Payment-Services gefunden werden. Überprüfen Sie die Rechtschreibung des Pakets, Ihre Versionsbeschränkung und ob das Paket in einer Stabilität verfügbar ist, die Ihrer Mindeststabilität (stabil) entspricht.*

<u>Erwartetes Ergebnis</u>:

Sie können diese [Installationsanweisungen](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html) in unserer Entwicklerdokumentation befolgen, um Zahlungsdienste erfolgreich zu installieren.

<u>Tatsächliches Ergebnis</u>:

Während der Installation wird eine Fehlermeldung angezeigt, die besagt, dass Sie während der Installation nicht die richtigen Composer-Schlüssel verwendet haben.

### Ursache

Sie haben während der Installation falsche Composer-Schlüssel verwendet.

### Lösung

Stellen Sie sicher, dass [Ihre Composer-Schlüssel mit der Magento ID](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html#incorrect-composer-keys) verknüpft sind, die bei der Registrierung von Zahlungsdiensten verwendet wird.

## Problem - Verwendung des gleichen Datenraums über mehrere Instanzen hinweg

Ausführen einer Multi-Umgebung-Einrichtung mit Zahlungsdiensten für jede.

### Lösung

Derselbe API-Schlüssel kann für alle Instanzen verwendet werden, aber jede Instanz muss einen eigenen SaaS-Datenraum verwenden.

Wenn Sie ein SaaS-Projekt erstellen, generiert Commerce je nach Ihrer Commerce-Lizenz einen oder mehrere SaaS-Datenräume:

* Adobe Commerce - Ein Produktionsdatenraum; zwei Testdatenbereiche
* Magento Open Source - Ein Produktionsdatenraum; keine Testdatenbereiche

Befolgen Sie die Anweisungen in [Commerce-API-Schlüssel und privater Schlüssel](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#obtain-api-credentials) , um Ihre Zahlungsdiensterweiterung erfolgreich zu konfigurieren.

## Problem - Nicht genügend Speicher für PHP

Bei der Installation der Zahlungsdienst-Erweiterung wird möglicherweise eine Fehlermeldung angezeigt, dass Sie nicht genügend Speicher für PHP haben.

<u>Zu reproduzierende Schritte</u>:

1. Versuchen Sie, [Zahlungsdienste zu installieren](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html).
1. Siehe folgenden Fehler oder Ähnliches:

   *Schwerwiegender Fehler: Zulässige Speichergröße von 2146435072 Byte erschöpft (versucht, 4096 Byte zuzuweisen) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php in Zeile 52*

<u>Erwartetes Ergebnis</u>:

Sie können diese [Installationsanweisungen](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html) in unserer Entwicklerdokumentation befolgen, um Zahlungsdienste erfolgreich zu installieren.

<u>Tatsächliches Ergebnis</u>:

Während der Installation wird eine Fehlermeldung angezeigt, dass Sie nicht genügend Speicher für PHP haben.

### Ursache

Der Grenzwert für PHP in Ihrer Umgebung ist nicht hoch genug.

### Lösung

[Erhöhen Sie die Speicherbegrenzung für PHP](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html#not-enough-memory-for-php) in Ihrer Umgebung in `php.ini`.
