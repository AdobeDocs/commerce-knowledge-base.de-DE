---
title: SSL-Zertifikate (TLS) für Adobe Commerce in der Cloud-Infrastruktur
description: In diesem Artikel finden Sie schnelle Antworten auf Fragen zum Abrufen von SSL-Zertifikaten (TLS) für Ihre Adobe Commerce-Site in unserer Cloud-Infrastruktur.
exl-id: 5a682d07-e4d7-4e81-a2ad-3232f2d8d9c1
feature: Cloud, Console
source-git-commit: 43c3e5f95c4b54e235140cd5b3978d3887af5ee1
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 0%

---

# SSL-Zertifikate (TLS) für Adobe Commerce in der Cloud-Infrastruktur

In diesem Artikel finden Sie schnelle Antworten auf Fragen zum Abrufen von SSL-Zertifikaten (TLS) für Ihre Adobe Commerce-Site in unserer Cloud-Infrastruktur.

## Welches SSL-/TLS-Zertifikat bietet Adobe?

Adobe stellt eine Domäne bereit, die validiert wurde [SSL-/TLS-Zertifikat verschlüsseln](https://letsencrypt.org/) zur Bereitstellung des sicheren HTTPS-Traffics von [!DNL Fastly]. Adobe stellt für jede Adobe Commerce ein Zertifikat in der Planarchitektur von Cloud Infrastructure Pro, Staging und Adobe Commerce in der Planarchitekturumgebung für Cloud-Infrastruktur-Starter bereit, um alle Domänen in dieser Umgebung zu sichern.

## Was umfasst ein Zertifikat?

Für die Pro-Planarchitektur wird sowohl für Staging- als auch für Produktions-dedizierte Umgebungen ein SSL-Zertifikat erstellt. Jede dedizierte Umgebung außerhalb der Platform-as-a-Service (PaaS)-Integrationsumgebungen verfügt über dieses Zertifikat für die URLs, die dieser Umgebung zugewiesen sind.

Für die Starter-Planarchitektur und die PaaS-Integrationsumgebungen gibt es eine standardmäßige technische Domäne, die mit der Umgebung bereitgestellt und durch ein separates Zertifikat gesichert wird.

## Wie wird eine neue Domäne für das vorhandene Zertifikat hinzugefügt?

Hinzufügen der Domäne zum Dienst in [!DNL Fastly]:

1. Setzen Sie Ihre Domain im DNS auf prod.magentocloud.map.fastly.net und warten Sie bis zu 6 Stunden.
1. [Support-Ticket senden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) -Anfrage, um diese Domäne in der Nginx-Konfiguration hinzuzufügen (wenn Sie dies noch nicht getan haben).

## Wie kann ich ein Zertifikat anfordern?

1. Fall

Wenn Sie noch keine Website gestartet haben, haben Sie möglicherweise ACME Challenge CNAME von Ihrem technischen Kundenberater (CTA) erhalten. Sie benötigen nur dann eine ACME-Anfrage, wenn Sie Ihr DNS nicht sofort auf Ihre Produktions-URL verweisen können und die SSL-Zertifikate im Voraus erstellen müssen.

2. Fall

Wenn Ihre Site bereits live ist und/oder Sie auf die URLs verweisen können, die für Ihre Live-Site verwendet werden, müssen Sie keinen ACME-CNAME anfordern. Nachdem Sie die URLs nach Bedarf zu Ihrer Adobe Commerce auf der Cloud-Infrastruktur-Site hinzugefügt haben und Ihr DNS unter [!DNL Fastly], funktioniert die HTTP-Validierung und erstellen entweder das SSL-Zertifikat zum ersten Mal oder aktualisieren Sie Ihr Zertifikat mit zusätzlichen URLs.

## Kann ich mein eigenes SSL-/TLS-Zertifikat verwenden?

Sie können Ihr eigenes SSL-/TLS-Zertifikat bereitstellen, anstatt die [Zertifikat verschlüsseln](https://letsencrypt.org/) bereitgestellt von Adobe.

Dieser Prozess erfordert jedoch zusätzliche Arbeit für die Einrichtung und Wartung. Sie müssen zunächst eine Certificate Signing Request (CSR) für den Domänennamen (oder allgemeinen Namen) der Website generieren und diesem SSL-Anbieter ein SSL-Zertifikat bereitstellen.

Sobald Sie über das SSL-Zertifikat verfügen, senden Sie eine [Support-Ticket für Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) oder mit Ihrem CTA zusammenarbeiten, um benutzerdefinierte gehostete Zertifikate zu Ihren Cloud-Umgebungen hinzuzufügen.

* Wenn die Domains nicht mehr verwendet werden, werden sie automatisch aus unserem System gelöscht, und es sind keine weiteren Maßnahmen erforderlich.
* Wenn Sie bereits Inhaber eines Zertifikats sind, laden Sie es mithilfe eines SFTP-Clients (SSH File Transfer Protocol) an einen Web-nicht zugänglichen Dateispeicherort auf Ihrem Server hoch und [Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) ihnen den Dateipfad mitteilen.

>[!WARNING]
>
>Es ist wichtig, dass Sie die Zertifikatdateien nicht direkt in das Ticket hochladen. Andernfalls werden die Zertifikate als kompromittiert betrachtet und Adobe muss ein neues Zertifikat anfordern.
>Die Dateien sollten über SFTP auf den Server hochgeladen werden. Verwenden Sie keine anderen Methoden wie das Übertragen der Dateien an Ihr Repository (dies sollte nur für unveränderliche Dateien erfolgen, die keine vertraulichen Daten enthalten).

## Der Name Ihres Zertifikats

Der Name des SSL-Zertifikats spielt nur für die primäre URL eine Rolle. Er ist der primäre Hostname mit dem Namen der ersten URL und muss mit dem übereinstimmen, damit er validiert und erstellt werden kann. Wenn Sie einige URLs haben, werden diese als Einträge für alternative Namen des Betreffs zum Zertifikat hinzugefügt. Wenn Sie mehrere URLs haben, die auf eine Adobe Commerce-Website in der Cloud-Infrastruktur verweisen, haben Sie nur eine URL-Zertifizierung für allgemeine Namen, an die dann Alternativnamen für Betreffs angehängt werden, um Ihre Site mit SSL zu schützen.

## Welche Domäne wird im Feld Allgemeiner Name des Zertifikats angezeigt?

Die im Zertifikat angezeigte Domäne ist nur die erste Domäne, die dem TLS-Zertifikat hinzugefügt wurde. Sie füllt die **Gebrauchsname** (**CN**) und in Browsern wird dieser Name zuerst angezeigt. Die **Alternativname des Betreffs** (**SAN**) enthält alle DNS-Namen für das TLS-Zertifikat. Es gibt keine Möglichkeit, den angezeigten allgemeinen Namen zu ändern oder anzufordern.

## Kann ich Platzhalter-TLS-Zertifikate verwenden?

Wildcard-TLS-Zertifikate können nur mit Ihrem benutzerdefinierten Zertifikat und nicht mit Adobe Commerce Let&#39;s Encrypt certificates verwendet werden. Im Rahmen unserer TLS-Optimierung beendet Adobe die Unterstützung für Platzhalter-TLS-Zertifikate. Wir identifizieren und kontaktieren Händler, die ein Platzhalterzertifikat mit Adobe Let&#39;s Encrypt-Zertifikaten verwenden und im [!DNL Fastly] -Konsole für Adobe Commerce. Wir fordern, dass diese Wildcard-Zertifikate durch genaue Domänen ersetzt werden, um die TLS-Abdeckung sicherzustellen. Um ein Platzhalter-TLS-Zertifikat zu ersetzen, besuchen Sie bitte das [Domänenabschnitt](https://devdocs.magento.com/cloud/cdn/configure-fastly-customize-cache.html#manage-domains) des [!DNL Fastly] Plug-in. Von hier aus können exakte Domänen hinzugefügt und der Platzhalter entfernt werden. Bitte beachten Sie, dass DNS auf [!DNL Fastly] für diese neuen Domänen durch das CDN weitergeleitet werden. Sobald die Domänen hinzugefügt und das DNS aktualisiert wurde, wird eine [Verschlüsseln](https://letsencrypt.org/) -Zertifikat bereitgestellt wird. Wenn Sie keine Domäne entfernen, die auf [!DNL Fastly] mit einem Platzhalter löscht Adobe das freigegebene Zertifikat. Dies kann zu einem Site-Ausfall führen, wenn Sie den URL-FQDN nicht konfiguriert und denselben URL-FQDN in Ihrem DNS eingerichtet haben. Sie sollten daher sicherstellen, dass die konfigurierten URLs auch eine Eins-zu-Eins-Übereinstimmung im DNS aufweisen, die auf Folgendes verweist: [!DNL Fastly].

## Was sollte ich tun, wenn meine Domain nicht mehr auf Adobe Commerce verweist?

Wenn Ihre Domäne nicht mehr auf Adobe Commerce verweist, entfernen Sie sie aus dem [!DNL Fastly]/Adobe Commerce. Siehe [!DNL Fastly] [Löschen einer Domäne](https://docs.fastly.com/en/guides/working-with-domains#deleting-a-domain) , um mehr zu erfahren. Es ist zwar nicht erforderlich, Ihre Domäne auf Adobe Commerce zu verweisen, doch überprüfen Sie, ob ein TLS-Zertifikat der obersten Ebene erforderlich ist. Wenn eine Domäne der obersten Ebene erforderlich ist, aktualisieren Sie Ihr DNS so, dass sie auf Adobe Commerce verweist. Wenn er bereits auf Adobe Commerce verweist, aktualisieren Sie Ihren CAA-Datensatz, um [lets-encrypt](https://letsencrypt.org/). Wenn Sie diese Schritte ausführen, wird das LE-Zertifikat mit den erforderlichen sekundären URLs aktualisiert, die vom Zertifikat abgedeckt werden. &#x200B;

## Verwandtes Lesen

[Bereitstellen von SSL-/TLS-Zertifikaten](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#provision-ssltls-certificates) in unserer Entwicklerdokumentation
