---
title: SSL-Zertifikate (TLS) für Adobe Commerce in der Cloud-Infrastruktur
description: In diesem Artikel finden Sie schnelle Antworten auf Fragen zum Abrufen von SSL-Zertifikaten (TLS) für Ihre Adobe Commerce-Site in unserer Cloud-Infrastruktur.
exl-id: 5a682d07-e4d7-4e81-a2ad-3232f2d8d9c1
feature: Cloud, Console
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 0%

---

# SSL-Zertifikate (TLS) für Adobe Commerce in der Cloud-Infrastruktur

In diesem Artikel finden Sie schnelle Antworten auf Fragen zum Abrufen von SSL-Zertifikaten (TLS) für Ihre Adobe Commerce-Site in unserer Cloud-Infrastruktur.

## Welches SSL-/TLS-Zertifikat bietet Adobe?

Adobe stellt ein domänenvalidiertes [SSL-/TLS-Zertifikat verschlüsseln](https://letsencrypt.org/) bereit, um sicheren HTTPS-Traffic von [!DNL Fastly] bereitzustellen. Adobe stellt für jede Adobe Commerce ein Zertifikat in der Planarchitektur von Cloud Infrastructure Pro, Staging und Adobe Commerce in der Planarchitekturumgebung für Cloud-Infrastruktur-Starter bereit, um alle Domänen in dieser Umgebung zu sichern.

## Was umfasst ein Zertifikat?

Für die Pro-Planarchitektur wird sowohl für Staging- als auch für Produktions-dedizierte Umgebungen ein SSL-Zertifikat erstellt. Jede dedizierte Umgebung außerhalb der Platform-as-a-Service (PaaS)-Integrationsumgebungen verfügt über dieses Zertifikat für die URLs, die dieser Umgebung zugewiesen sind.

Für die Starter-Planarchitektur und die PaaS-Integrationsumgebungen gibt es eine standardmäßige technische Domäne, die mit der Umgebung bereitgestellt und durch ein separates Zertifikat gesichert wird.

## Wie wird eine neue Domäne für das vorhandene Zertifikat hinzugefügt?

Hinzufügen der Domäne zum Dienst in [!DNL Fastly]:

1. Setzen Sie Ihre Domain im DNS auf prod.magentocloud.map.fastly.net und warten Sie bis zu 6 Stunden.
1. [Senden Sie ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), um diese Domäne in die Nginx-Konfiguration hinzuzufügen (falls Sie dies noch nicht getan haben).

## Wie kann ich ein Zertifikat anfordern?

1. Fall

Wenn Sie noch keine Website gestartet haben, haben Sie möglicherweise von Ihrem technischen Kundenberater (CTA) ACME Challenge CNAME erhalten. Sie benötigen nur dann eine ACME-Anfrage, wenn Sie Ihr DNS nicht sofort auf Ihre Produktions-URL verweisen können und die SSL-Zertifikate im Voraus erstellen müssen.

2. Fall

Wenn Ihre Site bereits live ist und/oder Sie auf die URLs verweisen können, die für Ihre Live-Site verwendet werden, müssen Sie keinen ACME-CNAME anfordern. Nachdem Sie die URLs nach Bedarf zu Ihrer Adobe Commerce auf der Cloud-Infrastruktur-Site hinzugefügt und Ihr DNS auf [!DNL Fastly] verweisen, funktioniert die HTTP-Validierung und erstellt entweder zum ersten Mal Ihr SSL-Zertifikat oder aktualisiert Ihr Zertifikat mit zusätzlichen URLs.

## Kann ich mein eigenes SSL-/TLS-Zertifikat verwenden?

Sie können Ihr eigenes SSL-/TLS-Zertifikat bereitstellen, anstatt das von Adobe bereitgestellte [Let&#39;s Encrypt certificate](https://letsencrypt.org/) zu verwenden.

Dieser Prozess erfordert jedoch zusätzliche Arbeit für die Einrichtung und Wartung. Sie müssen zunächst eine Certificate Signing Request (CSR) für den Domänennamen (oder allgemeinen Namen) der Website generieren und diesem SSL-Anbieter ein SSL-Zertifikat bereitstellen.

Sobald Sie über das SSL-Zertifikat verfügen, senden Sie ein [Adobe Commerce-Supportticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) oder arbeiten Sie mit Ihrer CTA zusammen, um benutzerdefinierte gehostete Zertifikate zu Ihren Cloud-Umgebungen hinzuzufügen.

* Wenn die Domains nicht mehr verwendet werden, werden sie automatisch aus unserem System gelöscht, und es sind keine weiteren Maßnahmen erforderlich.
* Wenn Sie bereits Inhaber eines Zertifikats sind, laden Sie es mithilfe eines SFTP-Clients (SSH File Transfer Protocol) an einen Web-nicht zugänglichen Dateispeicherort auf Ihrem Server hoch und senden Sie [ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), um ihnen den Dateipfad mitzuteilen.

>[!WARNING]
>
>Es ist wichtig, dass Sie die Zertifikatdateien nicht direkt in das Ticket hochladen. Andernfalls werden die Zertifikate als kompromittiert betrachtet und Adobe muss ein neues Zertifikat anfordern.
>Die Dateien sollten über SFTP auf den Server hochgeladen werden. Verwenden Sie keine anderen Methoden wie das Übertragen der Dateien an Ihr Repository (dies sollte nur für unveränderliche Dateien erfolgen, die keine vertraulichen Daten enthalten).

## Der Name Ihres Zertifikats

Der Name des SSL-Zertifikats spielt nur für die primäre URL eine Rolle. Er ist der primäre Hostname mit dem Namen der ersten URL und muss mit dem übereinstimmen, damit er validiert und erstellt werden kann. Wenn Sie einige URLs haben, werden diese als Einträge für alternative Namen des Betreffs zum Zertifikat hinzugefügt. Wenn Sie mehrere URLs haben, die auf eine Adobe Commerce-Website in der Cloud-Infrastruktur verweisen, haben Sie nur eine URL-Zertifizierung für allgemeine Namen, an die dann Alternativnamen für Betreffs angehängt werden, um Ihre Site mit SSL zu schützen.

## Welche Domäne wird im Feld Allgemeiner Name des Zertifikats angezeigt?

Die im Zertifikat angezeigte Domäne ist nur die erste Domäne, die dem TLS-Zertifikat hinzugefügt wurde. Sie füllt das Feld **Gebrauchsname** (**CN**) und in Browsern wird dieser Name zuerst angezeigt. Das Feld **Alternativer Betreffname** (**SAN**) enthält alle DNS-Namen für das TLS-Zertifikat. Es gibt keine Möglichkeit, den angezeigten allgemeinen Namen zu ändern oder anzufordern.

## Kann ich Platzhalter-TLS-Zertifikate verwenden?

Wildcard-TLS-Zertifikate können nur mit Ihrem benutzerdefinierten Zertifikat und nicht mit Adobe Commerce Let&#39;s Encrypt certificates verwendet werden. Im Rahmen unserer TLS-Optimierung beendet Adobe die Unterstützung für Platzhalter-TLS-Zertifikate. Wir identifizieren und kontaktieren Händler, die ein Platzhalterzertifikat mit Adobe Let&#39;s Encrypt-Zertifikaten verwenden und in der [!DNL Fastly] -Konsole für Adobe Commerce konfiguriert sind. Wir fordern, dass diese Wildcard-Zertifikate durch genaue Domänen ersetzt werden, um die TLS-Abdeckung sicherzustellen. Um ein Platzhalter-TLS-Zertifikat zu ersetzen, besuchen Sie den Abschnitt [Domäne](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration#manage-domains) des Plug-ins [!DNL Fastly] . Von hier aus können exakte Domänen hinzugefügt und der Platzhalter entfernt werden. Beachten Sie, dass DNS auf [!DNL Fastly] verweisen muss, damit diese neuen Domänen durch das CDN weitergeleitet werden. Sobald die Domänen hinzugefügt und das DNS aktualisiert wurde, wird ein entsprechendes [Let&#39;s Encrypt](https://letsencrypt.org/) -Zertifikat bereitgestellt. Wenn Sie eine Domäne, die mit einem Platzhalter auf [!DNL Fastly] verweist, nicht entfernen, löscht Adobe das freigegebene Zertifikat. Dies kann zu einem Site-Ausfall führen, wenn Sie den URL-FQDN nicht konfiguriert und denselben URL-FQDN in Ihrem DNS eingerichtet haben. Sie sollten daher sicherstellen, dass die konfigurierten URLs auch eine Eins-zu-Eins-Übereinstimmung im DNS aufweisen, die auf [!DNL Fastly] verweist.

## Was sollte ich tun, wenn meine Domain nicht mehr auf Adobe Commerce verweist?

Wenn Ihre Domäne nicht mehr auf Adobe Commerce verweist, entfernen Sie sie aus dem System [!DNL Fastly]/Adobe Commerce . Weitere Informationen finden Sie unter [!DNL Fastly] [Löschen einer Domäne](https://docs.fastly.com/en/guides/working-with-domains#deleting-a-domain) . Es ist zwar nicht erforderlich, Ihre Domäne auf Adobe Commerce zu verweisen, doch überprüfen Sie, ob ein TLS-Zertifikat der obersten Ebene erforderlich ist. Wenn eine Domäne der obersten Ebene erforderlich ist, aktualisieren Sie Ihr DNS so, dass sie auf Adobe Commerce verweist. Wenn er bereits auf Adobe Commerce verweist, aktualisieren Sie Ihren CAA-Datensatz, sodass er [lets-encrypt](https://letsencrypt.org/) enthält. Wenn Sie diese Schritte ausführen, wird das LE-Zertifikat mit den erforderlichen sekundären URLs aktualisiert, die vom Zertifikat abgedeckt werden. &#x200B;

## Verwandtes Lesen

[Bereitstellen von SSL-/TLS-Zertifikaten](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#provision-ssltls-certificates) in unserer Entwicklerdokumentation
