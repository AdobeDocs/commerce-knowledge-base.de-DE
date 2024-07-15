---
title: Fehlerbehebung in Adobe Commerce rückgängig machen
description: Dieser Artikel ist ein Tool zur Fehlerbehebung für Adobe Commerce On-Premise- und Adobe Commerce für Cloud-Infrastruktur-Händler, die Probleme mit Redis haben. Klicken Sie auf jede Frage, um die Antwort in jedem Schritt der Problembehebung anzuzeigen. Abhängig von Ihren Symptomen und Ihrer Konfiguration wird in der Fehlerbehebung erläutert, wie Sie Probleme mit Version und Speicher beheben und die Leistung optimieren können.
exl-id: 241abcfd-33b8-449b-b385-32950bd26320
feature: Services, Support
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '566'
ht-degree: 0%

---

# Fehlerbehebung in Adobe Commerce rückgängig machen

Dieser Artikel ist ein Tool zur Fehlerbehebung für Adobe Commerce On-Premise- und Adobe Commerce für Cloud-Infrastruktur-Händler, die Probleme mit Redis haben. Klicken Sie auf jede Frage, um die Antwort in jedem Schritt der Problembehebung anzuzeigen. Abhängig von Ihren Symptomen wird in der Fehlerbehebung erläutert, wie Sie Probleme mit Version und Speicher beheben und die Leistung optimieren können.

## Schritt 1: Problem mit Redis {#step-1}

+++Redis-Problem?

a. YES - Fahren Sie mit [Schritt 2](#step2)</a> fort.

b. NO - Kehren Sie zu [support.magento.com](https://support.magento.com/hc/en-us) zurück und suchen Sie nach relevanten Artikeln zur Fehlerbehebung.

+++

## Schritt 2: Überprüfen der installierten Redis-Patches {#step-2}

+++Aktuelle Redis-Patches installiert?

a. JA - Fahren Sie mit [Schritt 3](#step3)</a> fort.

b. NO - Stellen Sie sicher, dass Sie die neueste Version des Pakets `magento-cloud-patches` installiert haben. Dieses Paket enthält die erforderlichen Patches für Redis. Navigieren Sie zu [GitHub Magneto-Cloud-Patches](https://github.com/magento/magento-cloud-patches/), um darauf zuzugreifen.

+++

## Schritt 3: Bestätigen, dass Redis unterstützt wird {#step-3}

+++On Redis Version 3.2 oder 5.0?

Überprüfen Sie, indem Sie die folgenden Befehle in der CLI ausführen. Pro oder Staging: `$ redis-cli -p %port-number% info | grep redis_version`, wobei `%port-number%` die Nummer des Ports ist, der in der Datei `app/etc/env.php` zu finden ist oder durch Ausführen eines der folgenden Befehle ausgeführt wird: `$ vendor/bin/ece-tools env:config:show | grep -i redis -A 3` oder `$ cat app/etc/env.php | grep redis -A 3` Starter oder Integration: `$ redis-cli -h 'redis.internal' info | grep redis_version`

a. YES - Fahren Sie mit [Schritt 4](#step4) fort.

b. NO - Adobe Commerce unterstützt die Redis-Versionen 3.2 und 5.0. Wenn Sie Adobe Commerce auf Cloud-Infrastruktur 2.3.3 oder höher ausführen, empfehlen wir ein Upgrade auf Redis 5. Informationen zum Einrichten von Adobe Commerce für Cloud Infrastructure Pro-Planarchitektur, Integration- und Starterumgebungen einschließlich der Masterverzweigung finden Sie unter [Adobe Commerce on cloud Infrastructure > Einrichten des Redis-Dienstes](https://devdocs.magento.com/cloud/project/services-redis.html)</a> in unserer Entwicklerdokumentation. **Sie müssen [ein Support-Ticket senden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), um die Dienstkonfiguration in Produktions- und Staging-Umgebungen der Pro-Architektur zu ändern. Außerdem wird für Adobe Commerce on Cloud Infrastructure und Adobe Commerce On-Premise 2.3.5+ eine erweiterte Redis-Cache-Implementierung empfohlen. Diese Art der Redis-Cache-Implementierung bietet Verbesserungen, die die Anzahl der Abfragen an Redis minimieren, die bei jeder Adobe Commerce-Anfrage ausgeführt werden. Anweisungen finden Sie unter [Erweiterte Redis-Cache-Implementierung Adobe Commerce 2.3.5+](https://support.magento.com/hc/en-us/articles/360049292532) in unserer Support-Wissensdatenbank. Anweisungen für alle anderen Adobe Commerce-Benutzer finden Sie in unserer Entwicklerdokumentation unter [Adobe Commerce Configuration Guide > Configure Redis](https://devdocs.magento.com/guides/v2.4/config-guide/redis/config-redis.html) .

+++

## Schritt 4: Überprüfen der neuesten Version der ECE-Tools {#step-4}

+++ Haben Sie die neueste Version von [ECE Tools > v2002.1.1](https://github.com/magento/ece-tools/releases)?

Überprüfen Sie, welche Version Sie haben, indem Sie den Befehl im CLI/Terminal ausführen: `$php vendor/bin/composer info magento/ece-tools`.

a. YES - Fahren Sie mit [Schritt 5](#step5) fort.

b. NO - [Aktualisieren Sie ECE-Tools](https://devdocs.magento.com/cloud/project/ece-tools-update.html) auf die neueste Version.

+++

## Schritt 5: Prüfen des Netzwerk-Traffics {#step-5}

+++ Gibt es viel Netzwerk-Traffic zwischen der App und Redis?

a. YES - Versuchen Sie Folgendes: Stellen Sie für eine nicht geteilte Architektur sicher, dass eine [sekundäre Verbindung](/help/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.md) verwendet wird. Für die Aufspaltungsarchitektur muss der Cache [L2 aktiviert sein](https://devdocs.magento.com/guides/v2.4/config-guide/cache/two-level-cache.html).

b. NO - Konfigurieren Sie die L2-Cache-Konfiguration durch [Aktualisieren des Redis-Backend](https://devdocs.magento.com/cloud/env/variables-deploy.html#redis_backend). Fahren Sie mit [Schritt 6](#step6) fort.

+++

## Schritt 6: Überprüfen der Geschwindigkeit der Website {#step-6}

+++ Funktioniert die Site nach Aktivierung des L2-Cache immer noch langsam?

a. YES - Überprüfen Sie das temporäre Verzeichnis `/dev/shm` , um zu sehen, ob Sie den Speicherplatz erhöhen müssen. Wenn Sie mehr Speicherplatz benötigen, senden Sie [ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
b. NO - Die Aktivierung des L2-Cache scheint Ihre Redis-Probleme gelöst zu haben.

+++

[Zurück zu Schritt 1](#step-1)
