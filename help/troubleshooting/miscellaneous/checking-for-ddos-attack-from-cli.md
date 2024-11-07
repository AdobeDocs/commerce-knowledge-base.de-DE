---
title: Überprüfung auf DoS-Angriff von CLI
description: In diesem Artikel wird die Frage besprochen, wie Sie versuchen, über die Befehlszeilenschnittstelle (CLI) Ihres Servers nach Dezentralen-Service-Angriffen (Dezentrales Service, Distributed Denial of Service) zu suchen.
exl-id: dfdef289-cf51-42d7-b3fb-d4d2d3760951
feature: Observability
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 0%

---

# Überprüfung auf DoS-Angriff von CLI

In diesem Artikel wird die Frage besprochen, wie Sie versuchen, über die Befehlszeilenschnittstelle (CLI) Ihres Servers nach Dezentralen-Service-Angriffen (Dezentrales Service, Distributed Denial of Service) zu suchen.

## Betroffene Produkte und Versionen

* Adobe Commerce, alle Versionen
* Magento Open Source, alle Versionen

## Problem

Ihre Website ist langsam, und Sie haben keinen Zugriff auf andere Analytics-Anwendungs-Tools, mit Ausnahme Ihrer CLI, um nach einem potenziellen DDoS-Angriff zu suchen. Die Symptome eines DoS-Angriffs können je nach Netzwerkkonfiguration, verwendeter Software usw. stark variieren.

Es wird jedoch empfohlen, Analysesoftware-Produkte zu verwenden, die speziell zur Identifizierung von DDoS-Angriffen entwickelt wurden.

## Ursache

Es gibt mehrere mögliche Ursachen für eine langsame Website, darunter einen Server mit geringer Leistung, eine hohe CPU-Auslastung oder eine falsche Konfiguration in Skripten, Code oder billiger Hardware. Manchmal kann dies auf einen DDoS-Angriff zurückzuführen sein. Zwei der grundlegenden Tools, die Sie auf einen DDoS-Angriff überprüfen müssen, sind Ihre Adobe Commerce-Protokolle und Ihre CLI.

Auch hier ist zu beachten, dass die Verwendung von Software, die speziell zur Identifizierung von DDoS-Angriffen entwickelt wurde, sehr nützlich für Ihre Untersuchung wäre.

## Lösungsschritte

1. Überprüfen Sie Ihre Adobe Commerce-Protokolle, um zu sehen, ob neben einem DDoS-Angriff etwas Anderes auftritt. Weitere Informationen finden Sie in den folgenden Artikeln in unserer Entwicklerdokumentation:
   * [Adobe Commerce- und Magento Open Source-Protokollspeicherorte](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/enable-logging)
   * [Adobe Commerce in Cloud-Infrastruktur protokolliert Standorte](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations)
1. Beginnen Sie mit der Verwendung Ihrer CLI, um Ihre aktuellen Internetverbindungen mit dem Befehl `netstat` zu überprüfen: `netstat -na`. Dadurch werden alle aktiven eingerichteten Verbindungen zum Server angezeigt. Hier können Sie feststellen, dass zu viele Verbindungen von derselben IP-Adresse kommen.
1. Verwenden Sie folgenden Befehl, um Ihre etablierten Verbindungen weiter auf die Verbindungen zu reduzieren, die über Port 80 (den HTTP-Anschluss für Ihre Website) verbunden sind, sodass Sie zu viele Verbindungen von einer IP-Adresse oder IP-Adressgruppe sortieren und erkennen können: `netstat -an | grep :80 | sort`. Sie können denselben Befehl für HTTPS an Port 443 wiederholen: `netstat -an | grep :443 | sort`. Eine andere Möglichkeit besteht darin, den ursprünglichen Befehl auf die Ports 80 und 443 zu erweitern: `netstat -an | egrep ":80|:443" | sort`.
1. Um zu sehen, ob viele aktive `SYNC_REC` auf dem Server vorhanden sind, verwenden Sie den Befehl:     `netstat -n -p|grep SYN_REC | wc -l`     Normalerweise sind es weniger als 5, aber es könnte bei einem DDoS-Angriff viel höher sein, auch wenn bei einigen Servern eine höhere Zahl ein normaler Zustand sein könnte.
1. Um alle IP-Adressen aufzulisten, die den Status `SYNC_REC` senden, verwenden Sie den Befehl: `netstat -n -p | grep SYN_REC | sort -u`.
1. Um alle eindeutigen IP-Adressen, die den Status `SYNC_REC` senden, weiter aufzulisten, verwenden Sie den Befehl: `netstat -n -p | grep SYN_REC | awk ‘{print $5}’ | awk -F: ‘{print $1}’`.
1. Sie können auch den Befehl `netstat` verwenden, um die Anzahl der Verbindungen zu Ihrem Server zu zählen und zu berechnen: `netstat -ntu | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -n`.
1. Verwenden Sie den Befehl `netstat -anp |grep ‘tcp|udp’ | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -n`, um die Anzahl der mit Ihrem Server verbundenen UDP- oder TCP-Protokollverbindungen aufzulisten.
1. Verwenden Sie den Befehl `netstat -ntu | grep ESTAB | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -nr`, um anstelle aller Verbindungen die eingerichteten Verbindungen zu überprüfen und die Anzahl der Verbindungen für jede IP-Adresse anzuzeigen.
1. Verwenden Sie den Befehl `netstat -plan|grep :80|awk {‘print $5’}|cut -d: -f 1|sort|uniq -c|sort -nk 1`, um die Anzahl der Verbindungen anzuzeigen, die nach IP-Adresse bis Port 80 aufgeführt sind.

Stellen Sie sicher, dass Sie jemanden haben, der die Daten, die Sie finden, richtig analysiert, um festzustellen, ob Sie tatsächlich einen DDoS-Angriff haben. Die Verwendung der Befehle &quot;`netstat`&quot; von Ihrer Server-CLI in den oben genannten Schritten hilft Ihnen dabei zu analysieren, ob Sie einen DDoS-Angriff erleben. Die Verwendung von Softwareanalyseprodukten, die speziell zur Identifizierung von DDoS-Angriffen entwickelt wurden, sowie einer ordnungsgemäßen Analyse sind jedoch die besten Werkzeuge zur Ermittlung von DDoS-Bedrohungen.

Wenn Sie feststellen, dass Sie unter einem DDoS-Angriff leiden, hängen die möglichen Schritte von Ihrer Netzwerkkonfiguration ab und davon, wie der DDoS-Angriff auftritt. Allgemeine Ratschläge sind jedoch, Ihren ISP zu kontaktieren, eine neue IP-Adresse für Ihren Server zu erhalten und/oder IT-Experten zu konsultieren, die mit DDoS-Problemen vertraut sind, um Ihre jeweilige Situation zu analysieren und zu beraten.

## Weitere Informationen finden Sie in unserer Entwicklerdokumentation:

* [S-Schutz](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly#ddos-protection)
* [Verwenden von CLI-Befehlen](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/deployment/examples/example-using-cli)
* [Cloud-CLI für Commerce](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli/cloud-cli-overview)
