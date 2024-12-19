---
title: Fehlerbehebung bei der Installation von Zahlungs-Services
description: In diesem Artikel werden Fehler erläutert, die bei der Installation von Zahlungsdiensten auftreten können, und es werden Lösungen zur Behebung dieser Fehler bereitgestellt, damit Sie die Installation abschließen können.
exl-id: 0aef7482-8834-400e-85b9-d3d3eb0ab76e
feature: Install, Orders, Payments, Saas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# Fehlerbehebung bei der Installation von Zahlungs-Services

In diesem Artikel werden Fehler erläutert, die bei der Installation von Zahlungsdiensten auftreten können, und es werden Lösungen zur Behebung dieser Fehler bereitgestellt, damit Sie die Installation abschließen können.

## Betroffene Produkte und Versionen

* [Payment Services](https://marketplace.magento.com/magento-payment-services.html) ist jetzt mit den Adobe Commerce-Versionen 2.4.0 bis 2.4.4 kompatibel.

## Problem - Falsche Composer-Schlüssel

Bei der Installation der Payment Services-Erweiterung wird möglicherweise eine Fehlermeldung angezeigt, die besagt, dass Sie während der Installation falsche Composer-Schlüssel verwendet haben.

<u>Schritte zur Reproduktion</u>:

1. Versuchen Sie, [Payment Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html) zu installieren.
1. Siehe folgenden Fehler:

   *Es konnte keine passende Version des Pakets magento/payment-services gefunden werden. Überprüfen Sie die Schreibweise des Pakets, Ihre Versionsbeschränkung und ob das Paket in einer Stabilität verfügbar ist, die Ihrer minimalen Stabilität (stabil) entspricht.*

<u>Erwartetes Ergebnis</u>:

Folgen Sie diesen [Installationsanweisungen](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html) in unserer Entwicklerdokumentation, um Payment Services erfolgreich zu installieren.

<u>Tatsächliches </u>:

Während der Installation wird eine Fehlermeldung angezeigt, die besagt, dass Sie während der Installation nicht die richtigen Composer-Schlüssel verwendet haben.

### Ursache

Sie haben während der Installation falsche Composer-Schlüssel verwendet.

### Lösung

Stellen Sie sicher[ dass Ihre Composer-Schlüssel mit der Magento-ID verknüpft sind](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html#incorrect-composer-keys) die bei der Registrierung von Payment Services verwendet wird.

## Problem - Verwendung desselben Datenspeichers über mehrere Instanzen hinweg

Ausführen einer Multi-Umgebung-Einrichtung mit jeweils Zahlungsdiensten.

### Lösung

Derselbe API-Schlüssel kann instanzenübergreifend verwendet werden, aber jede Instanz muss ihren eigenen SaaS-Datenspeicher verwenden.

Wenn Sie ein SaaS-Projekt erstellen, generiert Commerce je nach Ihrer Commerce-Lizenz einen oder mehrere SaaS-Datenbereiche:

* Adobe Commerce: ein Produktionsdatenbereich; zwei Testdatenbereiche
* Magento Open Source - Ein Produktionsdatenbereich; keine Testdatenbereiche

Befolgen Sie die Anweisungen unter [Commerce-API-Schlüssel und privater Schlüssel](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#obtain-api-credentials) um Ihre Payment Services-Erweiterung erfolgreich zu konfigurieren.

## Problem - Nicht genügend Speicher für PHP

Bei der Installation der Payment Services-Erweiterung wird möglicherweise eine Fehlermeldung angezeigt, die besagt, dass Sie nicht über ausreichend Speicher für PHP verfügen.

<u>Schritte zur Reproduktion</u>:

1. Versuchen Sie, [Payment Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html) zu installieren.
1. Siehe den folgenden Fehler oder Ähnliches:

   *Schwerwiegender Fehler: Zulässige Speichergröße von 2146435072 Byte erschöpft (versucht, 4096 Byte zuzuweisen) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php in Zeile 52*

<u>Erwartetes Ergebnis</u>:

Folgen Sie diesen [Installationsanweisungen](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html) in unserer Entwicklerdokumentation, um Payment Services erfolgreich zu installieren.

<u>Tatsächliches </u>:

Während der Installation wird eine Fehlermeldung angezeigt, die besagt, dass Sie nicht über genügend Speicher für PHP verfügen.

### Ursache

Der Grenzwert für PHP in Ihrer Umgebung ist nicht auf einen Schwellenwert festgelegt, der hoch genug ist.

### Lösung

[Erhöhen Sie die Speicherbegrenzung für PHP](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html#not-enough-memory-for-php) in Ihrer Umgebung in `php.ini`.
