---
title: Überprüfen auf DDoS-Angriffe über CLI
description: In diesem Artikel wird die Frage behandelt, wie versucht werden kann, über die Befehlszeilenschnittstelle (CLI) Ihres Servers nach DDoS-Angriffen (Distributed Denial of Service) zu suchen.
exl-id: dfdef289-cf51-42d7-b3fb-d4d2d3760951
feature: Observability
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 0%

---

# Überprüfen auf DDoS-Angriffe über CLI

In diesem Artikel wird die Frage behandelt, wie versucht werden kann, über die Befehlszeilenschnittstelle (CLI) Ihres Servers nach DDoS-Angriffen (Distributed Denial of Service) zu suchen.

## Betroffene Produkte und Versionen

* Adobe Commerce, alle Versionen
* Magento Open Source, alle Versionen

## Problem

Ihre Website ist langsam, und Sie haben außer Ihrer CLI keinen Zugriff auf andere Analyse-Anwendungs-Tools, um nach einem potenziellen DDoS-Angriff zu suchen. Die Symptome eines DDoS-Angriffs können je nach Netzwerkkonfiguration, verwendeter Software usw. stark variieren.

Es wird jedoch empfohlen, Analysesoftware-Produkte zu verwenden, die speziell entwickelt wurden, um DDoS-Angriffe zu identifizieren.

## Ursache

Es gibt mehrere mögliche Ursachen für eine langsame Website, einschließlich eines Servers mit langsamer Leistung, hoher CPU-Nutzung oder Fehlkonfiguration in Skripten, Code oder billiger Hardware. Manchmal kann es aufgrund eines DDoS-Angriffs sein. Zwei der grundlegenden Tools, die Sie auf einen DDoS-Angriff überprüfen müssen, sind Ihre Adobe Commerce-Protokolle und Ihre CLI.

Auch hier ist es wichtig zu beachten, dass die Verwendung von Software, die speziell entwickelt wurde, um DDoS-Angriffe zu erkennen, bei Ihrer Untersuchung sehr nützlich wäre.

## Lösungsschritte

1. Überprüfen Sie in den Adobe Commerce-Protokollen, ob neben einem DDoS-Angriff noch etwas Anderes auftritt. Weitere Informationen finden Sie in den folgenden Artikeln in unserer Entwicklerdokumentation:
   * [Speicherorte für Adobe Commerce- und Magento Open Source-Protokolle](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/enable-logging)
   * [Speicherorte für Adobe Commerce in Cloud-Infrastrukturprotokollen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations)
1. Verwenden Sie die CLI, um alle aktuellen Internetverbindungen mithilfe des `netstat` Befehls zu überprüfen: `netstat -na`. Hier werden alle aktiven bestehenden Verbindungen zum Server angezeigt. Hier können Sie möglicherweise feststellen, dass zu viele Verbindungen von derselben IP-Adresse stammen.
1. Verwenden Sie diesen Befehl, um Ihre Ergebnisse für bestehende Verbindungen weiter einzugrenzen auf diejenigen, die eine Verbindung über Port 80 (den HTTP-Port für Ihre Website) herstellen, sodass Sie zu viele Verbindungen von einer IP-Adresse oder einer Gruppe von IP-Adressen sortieren und erkennen können: `netstat -an | grep :80 | sort`. Sie können denselben Befehl für https auf Port 443: `netstat -an | grep :443 | sort` wiederholen. Eine weitere Möglichkeit besteht darin, den ursprünglichen Befehl auf beide Ports 80 und 443: `netstat -an | egrep ":80|:443" | sort` auszudehnen.
1. Mit dem folgenden Befehl können Sie überprüfen, ob viele aktive `SYNC_REC` auf dem Server auftreten:     `netstat -n -p|grep SYN_REC | wc -l`     Dies ist in der Regel weniger als 5, aber es könnte für einen DDoS-Angriff viel höher sein, obwohl für einige Server eine höhere Anzahl eine normale Bedingung sein könnte.
1. Um alle IP-Adressen aufzulisten, die `SYNC_REC` Status senden, verwenden Sie den Befehl `netstat -n -p | grep SYN_REC | sort -u`.
1. Um alle eindeutigen IP-Adressen, die `SYNC_REC` senden, weiter aufzulisten, verwenden Sie den Befehl `netstat -n -p | grep SYN_REC | awk ‘{print $5}’ | awk -F: ‘{print $1}’`.
1. Sie können auch den Befehl `netstat` verwenden, um die Anzahl der Verbindungen zu zählen und zu berechnen, die jede IP-Adresse mit Ihrem Server herstellt: `netstat -ntu | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -n`.
1. Um die Anzahl der mit Ihrem Server verbundenen UDP- oder TCP-Protokollverbindungen aufzulisten, verwenden Sie den Befehl `netstat -anp |grep ‘tcp|udp’ | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -n`.
1. Verwenden Sie zum Überprüfen bestehender Verbindungen (anstelle nur aller Verbindungen) und zum Anzeigen der Verbindungsanzahl für jede IP-Adresse den Befehl `netstat -ntu | grep ESTAB | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -nr`.
1. Verwenden Sie den folgenden Befehl, um die nach IP-Adresse und Port 80 aufgelisteten Verbindungszahlen anzuzeigen: `netstat -plan|grep :80|awk {‘print $5’}|cut -d: -f 1|sort|uniq -c|sort -nk 1`.

Stellen Sie sicher, dass Sie jemanden haben, der die gefundenen Daten richtig analysiert, um festzustellen, ob Sie tatsächlich einen DDoS-Angriff haben. Die Verwendung der `netstat`-Befehle von Ihrer Server-CLI in den oben genannten Schritten hilft Ihnen bei der Analyse, ob Sie einen DDoS-Angriff erleben. Verwenden Sie jedoch Softwareanalyseprodukte, die speziell entwickelt wurden, um DDoS-Angriffe zu identifizieren, zusammen mit einer ordnungsgemäßen Analyse, sind Ihre besten Tools, um DDoS-Bedrohungen zu identifizieren.

Wenn Sie feststellen, dass Sie unter DDoS-Angriffen stehen, hängen die Schritte, die Sie ausführen können, von Ihrer Netzwerkkonfiguration und dem Vorkommen des DDoS-Angriffs ab. Allgemein empfehlen wir Ihnen jedoch, Ihren ISP zu kontaktieren, eine neue IP-Adresse für Ihren Server zu erhalten und/oder sich an IT-Experten zu wenden, die im Umgang mit DDoS-Problemen erfahren, um Ihre spezielle Situation zu analysieren und zu beraten.

## Weitere Informationen finden Sie in unserer Entwicklerdokumentation:

* [DDoS-Schutz](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly#ddos-protection)
* [Verwendung von CLI-Befehlen](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/deployment/examples/example-using-cli)
* [Cloud-CLI für Commerce](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli/cloud-cli-overview)
