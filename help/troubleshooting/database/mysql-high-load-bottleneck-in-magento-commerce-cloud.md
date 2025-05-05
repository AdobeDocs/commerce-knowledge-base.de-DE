---
title: MySQL-Engpass bei hoher Auslastung in Adobe Commerce auf Cloud-Infrastruktur
description: In diesem Abschnitt wird eine Lösung erläutert, wenn eine hohe Last von MySQL in Adobe Commerce zu einem Leistungsengpass in der Cloud-Infrastruktur führt.
exl-id: c1f9d282-41d8-4850-8a24-336d55aa3140
feature: Cloud, Observability, Paas, Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '864'
ht-degree: 0%

---

# MySQL-Engpass bei hoher Auslastung in Adobe Commerce auf Cloud-Infrastruktur

In diesem Abschnitt wird eine Lösung erläutert, wenn eine hohe Last von MySQL in Adobe Commerce zu einem Leistungsengpass in der Cloud-Infrastruktur führt.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.x.x, Pro-Konten.

### Voraussetzungen

* ECE Tools-Version 2002.0.16 und höher
* New Relic APM-Service (**Ihr Adobe Commerce auf Cloud-Infrastrukturkonto enthält die Software für den New Relic APM** Service zusammen mit einem Lizenzschlüssel.)

Weitere Informationen zum New Relic-APM-Service und dessen Einrichtung mit Ihrem Adobe Commerce-Konto in Cloud-Infrastruktur finden Sie unter [New Relic-Services](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/monitor/new-relic/new-relic-service) und [Einführung in New Relic APM](https://docs.newrelic.com/docs/apm/new-relic-apm/getting-started/introduction-apm/).

## Problem

<u>Schritte, um festzustellen, ob das Problem Sie betrifft</u>

1. Überprüfen Sie in Ihrem New Relic APM-Übersichtsdiagramm, ob der erste Hinweis darauf vorliegt, dass MySQL zu einem Engpass geworden ist. Im folgenden Beispielbild ist dargestellt, wo MySQL zu einem Engpass geworden ist und die meiste Zeit der Webtransaktionen in Anspruch nimmt:

   ![KB-372_image002.png](assets/KB-372_image002.png)

   Beachten Sie, dass die rote gestrichelte Linie im Bild einen erkennbaren Aufwärtstrend in der Zeit der MySQL-Webtransaktionen zeigt und dann auf noch höheren Ebenen ihren Höhepunkt erreicht.
1. Von hier aus können Sie dann zu Ihrem **Datenbank**-Bildschirm gehen, wo Sie den zweiten Hinweis auf hohe Durchsätze oder langsame `SELECT` Abfragen in MySQL sehen können, und in dem folgenden Beispielbild können Sie sehen, wenn Sie nach **am meisten Zeit verbrauchen** sortieren, ist Ihr Speicher in diesem Beispiel langsam in `SELECT` MySQL-Abfragen.

   ![KB-372_image003_blurredExtension.png](assets/KB-372_image003_BlurredExtension.png)

Analysieren Sie die langsamen Transaktionen in New Relic APM. Wenn eine MySQL-Datenbank ein hohes Abfragevolumen oder einen hohen Druck aufweist, können Sie die Last auf verschiedene Knoten verteilen, indem Sie `SLAVE` Verbindungen aktivieren.

## Ursache

Ihr Adobe Commerce im Cloud-Infrastrukturspeicher hat einen hohen Durchsatz oder ist langsam bei der `SELECT` von MySQL-Abfragen.

## Lösung

>[!WARNING]
>
>Für skalierte Architektur (Split-Architektur) sollten Redis-Slave **Verbindungen** werden. Sie können überprüfen, ob Sie sich in einer skalierten Architektur befinden, indem Sie zu Ihrer Projekt-URL gehen, z. B. `https://console.adobecommerce.com/<owner-user-name>/<project-ID>/<environment-name>`. Klicken Sie auf **[!UICONTROL SSH]**. Wenn es mehr als drei Knoten gibt, befinden Sie sich auf skalierter Architektur. Wenn Sie Redis Slave Reads auf skalierter Architektur aktivieren, erhält der Kunde Fehler, wenn Redis-Verbindungen keine Verbindung herstellen können. Das hat damit zu tun, wie die Cluster konfiguriert sind, um Redis-Verbindungen zu verarbeiten. Redis-Slaves sind noch aktiv, werden aber nicht für Redis-Reads verwendet. Wir empfehlen für die skalierte Architektur die Verwendung von Adobe Commerce 2.3.5 oder höher und die Implementierung der neuen Redis-Backend-Konfiguration und die Implementierung des L2-Caching für Redis.

Wenn diese beiden Anzeichen auftreten, kann die Aktivierung `SLAVE` Verbindungen für die MySQL-Datenbank und Redis dazu beitragen, die Last auf verschiedene Knoten zu verteilen.

Adobe Commerce kann mehrere Datenbanken oder Redis asynchron lesen. Aktualisieren der `.magento.env.yaml`-Datei durch Festlegen von auf `true` der Werte `MYSQL_USE_SLAVE_CONNECTION` und `REDIS_USE_SLAVE_CONNECTION`, um eine **schreibgeschützte)** zur Datenbank zu verwenden, um schreibgeschützten Traffic auf einem Nicht-Master-Knoten zu empfangen. Dies verbessert die Leistung durch Lastenausgleich, da nur ein Knoten Lese-/Schreibdatenverkehr verarbeiten muss. Mit der Einstellung auf `false` entfernen Sie ein vorhandenes schreibgeschütztes Verbindungs-Array aus der `env.php`.

### Schritte

1. Bearbeiten Sie die `.magento.env.yaml` und fügen Sie den folgenden Inhalt hinzu:

   ![KB-372_image004.png](assets/KB-372_image004.png)

   Weitere Informationen finden Sie unter [Bereitstellen von Variablen in DevDocs](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#mysql_use_slave_connection).

1. Übertragen Sie Ihre Änderungen und übertragen Sie sie.
1. Durch das Pushen von Änderungen wird ein neuer Bereitstellungsprozess gestartet. Sobald die Bereitstellung erfolgreich abgeschlossen ist, sollte Ihre Instanz von Adobe Commerce in der Cloud-Infrastruktur jetzt für die Verwendung von Slave-Verbindungen konfiguriert sein.

## Häufige Fragen

Im Folgenden finden Sie die häufigsten Fragen, die Sie stellen können, wenn Sie die Verwendung der Slave-Verbindungsfunktion für Ihren Adobe Commerce im Cloud-Infrastrukturspeicher in Betracht ziehen.

* Gibt es bekannte Probleme oder Einschränkungen bei der Verwendung von Slave-Verbindungen? **Bei der Verwendung von Slave-Verbindungen sind keine Probleme bekannt. Stellen Sie einfach sicher, dass Sie das zuletzt aktualisierte Paket ece-tools verwenden. Anleitungen dazu finden Sie [Aktualisieren Ihres ece-tools-Pakets](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package).**
* Gibt es eine zusätzliche Latenz bei der Verwendung von Slave-Verbindungen? *Ja, die Latenz zwischen AZ (Cross-Availability Zones) ist höher und reduziert die Leistung einer Adobe Commerce auf einer Cloud-Infrastrukturinstanz, falls die Instanz nicht überladen ist und die Gesamtlast tragen kann. Wenn die Instanz jedoch überlastet ist, hilft Master-Slave bei der Leistung, indem die Last auf die MySQL-Datenbank oder Redis auf verschiedene Knoten verteilt wird.*

  **Auf nicht überladenen Clustern** - **Slave-Verbindungen verlangsamen die Leistung um 10-15%**, was einer der Gründe dafür ist, dass es nicht standardmäßig ist.

  *Auf überlasteten Clustern kommt es jedoch zu einer Leistungssteigerung, da diese 10-15 % durch die Reduzierung der Last durch Traffic gemindert werden.*
* Sollte ich diese Einstellungen für meinen Store aktivieren? *Wenn Sie hohe Last haben oder hohe Last auf der MySQL-Datenbank oder Redis erwarten, müssen Sie auf jeden Fall Slave-Verbindungen aktivieren. Für einen regulären Kunden mit durchschnittlichem Traffic ist dies **nicht**&#x200B;eine optimale Einstellung, die aktiviert werden sollte.*

## Verwandtes Lesen

In unserer Entwicklerdokumentation:

* [Variablen bereitstellen](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy).
* [Richten Sie eine optionale Datenbankreplikation ](https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/storage/split-db/multi-master-replication).
* [ECE-Tools-Paket](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/package-overview).

>[!NOTE]
>
>Wir sind uns bewusst, dass dieser Artikel immer noch branchenübliche Softwarebegriffe enthalten kann, die manche als rassistisch, sexistisch oder repressiv empfinden und die den Leser verletzen, traumatisieren oder unwillkommen heißen können. Adobe arbeitet daran, diese Begriffe aus unserem Code, unserer Dokumentation und unseren Benutzererlebnissen zu entfernen.
