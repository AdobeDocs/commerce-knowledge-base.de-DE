---
title: Überprüfung auf DoS-Angriff von CLI
description: In diesem Artikel wird die Frage besprochen, wie Sie versuchen, über die Befehlszeilenschnittstelle (CLI) Ihres Servers nach Dezentralen-Service-Angriffen (Dezentrales Service, Distributed Denial of Service) zu suchen.
exl-id: dfdef289-cf51-42d7-b3fb-d4d2d3760951
feature: Observability
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
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
   * [Speicherorte für Adobe Commerce- und Magento Open Source-Protokolle](https://devdocs.magento.com/guides/v2.3/config-guide/cli/logging.html)
   * [Adobe Commerce auf Cloud-Infrastrukturprotokollen](https://devdocs.magento.com/guides/v2.3/cloud/trouble/environments-logs.html)
1. Beginnen Sie mit der Verwendung Ihrer CLI, um Ihre aktuellen Internetverbindungen mithilfe der `netstat` command: `netstat -na`. Dadurch werden alle aktiven eingerichteten Verbindungen zum Server angezeigt. Hier können Sie feststellen, dass zu viele Verbindungen von derselben IP-Adresse kommen.
1. Verwenden Sie diesen Befehl, um Ihre etablierten Verbindungen weiter auf die Verbindungen zu Port 80 (dem HTTP-Port für Ihre Website) zu beschränken, sodass Sie zu viele Verbindungen von einer IP-Adresse oder IP-Adressgruppe sortieren und erkennen können: `netstat -an | grep :80 | sort`. Sie können denselben Befehl für HTTPS an Port 443 wiederholen: `netstat -an | grep :443 | sort`. Eine weitere Möglichkeit besteht darin, den ursprünglichen Befehl auf die Ports 80 und 443 zu erweitern: `netstat -an | egrep ":80|:443" | sort`.
1. So sehen Sie, ob viele `SYNC_REC` auf dem Server vorhanden sind, verwenden Sie den folgenden Befehl:     `netstat -n -p|grep SYN_REC | wc -l`     Normalerweise sind es weniger als 5, aber es könnte bei einem DDoS-Angriff viel höher sein, auch wenn bei einigen Servern eine höhere Zahl ein normaler Zustand sein könnte.
1. So listen Sie alle IP-Adressen auf, die gesendet werden `SYNC_REC` -Status verwenden Sie den Befehl: `netstat -n -p | grep SYN_REC | sort -u`.
1. So listen Sie alle eindeutigen IP-Adressen, die gesendet werden `SYNC_REC` -Status verwenden Sie den Befehl: `netstat -n -p | grep SYN_REC | awk ‘{print $5}’ | awk -F: ‘{print $1}’`.
1. Sie können auch die `netstat` -Befehl zum Zählen und Berechnen der Anzahl der Verbindungen, die jede IP-Adresse mit Ihrem Server verbindet: `netstat -ntu | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -n`.
1. Verwenden Sie den folgenden Befehl, um die Anzahl der mit Ihrem Server verbundenen UDP- oder TCP-Protokollverbindungen aufzulisten: `netstat -anp |grep ‘tcp|udp’ | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -n`.
1. Verwenden Sie den folgenden Befehl, um anstelle aller Verbindungen die eingerichteten Verbindungen zu überprüfen und die Anzahl der Verbindungen für jede IP-Adresse anzuzeigen: `netstat -ntu | grep ESTAB | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -nr`.
1. Verwenden Sie den folgenden Befehl, um die Anzahl der Verbindungen anzuzeigen, die nach IP-Adresse bis Port 80 aufgeführt sind: `netstat -plan|grep :80|awk {‘print $5’}|cut -d: -f 1|sort|uniq -c|sort -nk 1`.

Stellen Sie sicher, dass Sie jemanden haben, der die Daten, die Sie finden, richtig analysiert, um festzustellen, ob Sie tatsächlich einen DDoS-Angriff haben. Verwenden der `netstat` -Befehle Ihrer Server-CLI in den oben genannten Schritten helfen Ihnen dabei zu analysieren, ob Sie einen DDoS-Angriff erleben. Verwenden Sie jedoch Softwareanalyseprodukte, die speziell zur Identifizierung von DDoS-Angriffen entwickelt wurden, sowie eine ordnungsgemäße Analyse, sind Ihre besten Tools zur Identifizierung von DDoS-Bedrohungen.

Wenn Sie feststellen, dass Sie unter einem DDoS-Angriff leiden, hängen die möglichen Schritte von Ihrer Netzwerkkonfiguration ab und davon, wie der DDoS-Angriff auftritt. Allgemeine Ratschläge sind jedoch, Ihren ISP zu kontaktieren, eine neue IP-Adresse für Ihren Server zu erhalten und/oder IT-Experten zu konsultieren, die mit DDoS-Problemen vertraut sind, um Ihre jeweilige Situation zu analysieren und zu beraten.

## Weitere Informationen finden Sie in unserer Entwicklerdokumentation:

* [DDoS-Schutz](https://devdocs.magento.com/guides/v2.3/cloud/cdn/cloud-fastly.html#ddos-protection)
* [Verwenden von CLI-Befehlen](https://devdocs.magento.com/guides/v2.3/config-guide/deployment/pipeline/example/cli.html)
* [Cloud-CLI für Commerce](https://devdocs.magento.com/guides/v2.3/cloud/reference/cli-ref-topic.html)
