---
title: SSL (TLS)-Zertifikate für Adobe Commerce in der Cloud-Infrastruktur
description: Dieser Artikel enthält schnelle Antworten auf Fragen zum Abrufen von SSL (TLS)-Zertifikaten für Ihre Adobe Commerce-Site in unserer Cloud-Infrastruktur.
exl-id: 5a682d07-e4d7-4e81-a2ad-3232f2d8d9c1
feature: Cloud, Console
source-git-commit: 7694e6cb739d73a28c902e95d324b1317f4daaf6
workflow-type: tm+mt
source-wordcount: '1087'
ht-degree: 0%

---

# SSL (TLS)-Zertifikate für Adobe Commerce in der Cloud-Infrastruktur

Dieser Artikel enthält schnelle Antworten auf Fragen zum Abrufen von SSL (TLS)-Zertifikaten für Ihre Adobe Commerce-Site in unserer Cloud-Infrastruktur.

## Welches SSL-/TLS-Zertifikat stellt Adobe bereit?

Adobe stellt ein Domain-validiertes [Let&#39;s Encrypt SSL/TLS-Zertifikat](https://letsencrypt.org/) bereit, um sicheren HTTPS-Traffic von [!DNL Fastly] bereitzustellen. Adobe stellt ein Zertifikat für jede Adobe Commerce in der Starterplanarchitekturumgebung der Cloud-Infrastruktur Pro-Planarchitektur, Staging und Adobe Commerce in der Cloud-Infrastruktur bereit, um alle Domains in dieser Umgebung zu sichern.

## Was umfasst ein Zertifikat?

Für die Pro-Planarchitektur wird sowohl für Staging- als auch für Produktionsumgebungen ein SSL-Zertifikat erstellt. Jede dedizierte Umgebung außerhalb der Platform-as-a-Service (PaaS)-Integrationsumgebungen verfügt über dieses Zertifikat für die URLs, die dieser Umgebung zugewiesen sind.

Für die Starter-Planarchitektur und die PaaS-Integrationsumgebungen gibt es eine standardmäßige technische Domain, die mit der Umgebung bereitgestellt und durch ein separates Zertifikat gesichert wird.

## Wie wird eine neue Domain für das vorhandene Zertifikat hinzugefügt?

So fügen Sie die Domain zum Service in [!DNL Fastly] hinzu:

1. Verweisen Sie Ihre Domain in DNS auf prod.magentocloud.map.fastly.net und warten Sie bis zu 6 Stunden.
1. [Senden eines Support-Tickets](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) mit der Bitte, diese Domain in der Nginx-Konfiguration hinzuzufügen (falls noch nicht geschehen).

## Wie kann ich ein Zertifikat anfordern?

Fall 1

Wenn Sie noch keine Website gestartet haben, haben Sie möglicherweise die CNAME-Anfrage von Ihrem technischen Kundenberater (CTA) erhalten. Sie benötigen nur dann eine ACME Challenge, wenn Sie Ihren DNS nicht sofort auf Ihre Produktions-URL verweisen können und die SSL-Zertifikate vorab erstellt haben müssen.

Fall 2

Wenn Ihre Site bereits live ist und/oder Sie auf die URLs verweisen können, die sofort für Ihre Live-Site verwendet werden, müssen Sie keinen CNAME für ACME anfordern. Sobald Sie die URLs zu Ihrer Adobe Commerce auf der Website der Cloud-Infrastruktur hinzugefügt haben und auf [!DNL Fastly] verweisen, funktioniert die HTTP-Validierung und erstellt entweder zum ersten Mal Ihr SSL-Zertifikat oder aktualisiert Ihr Zertifikat mit zusätzlichen URLs.

## Kann ich mein eigenes SSL-/TLS-Zertifikat verwenden?

Sie können Ihr eigenes SSL-/TLS-Zertifikat bereitstellen, anstatt das von Adobe bereitgestellte [Let&#39;s Encrypt](https://letsencrypt.org/) zu verwenden.

Dieser Prozess erfordert jedoch zusätzliche Arbeit bei der Einrichtung und Wartung. Sie müssen zunächst ein Certificate Signing Request (CSR) für den Domain-Namen (oder Gebrauchsnamen) der Website generieren und ihn Ihrem SSL-Anbieter bereitstellen, um ein SSL-Zertifikat bereitzustellen.

Sobald Sie über das SSL-Zertifikat verfügen, senden Sie ein [Adobe Commerce-Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) oder verwenden Sie Ihre CTA, um Ihren Cloud-Umgebungen benutzerdefinierte gehostete Zertifikate hinzuzufügen.

* Wenn die Domains nicht mehr verwendet werden, werden sie automatisch aus unserem System gelöscht, sodass keine weiteren Maßnahmen erforderlich sind.
* Wenn Sie bereits über ein Zertifikat verfügen, laden Sie es mithilfe eines SFTP-Clients (SSH File Transfer Protocol) an einen im Web nicht zugänglichen Dateispeicherort auf Ihrem Server hoch und [senden Sie ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), sodass der Dateipfad bekannt wird.

>[!WARNING]
>
>Es ist wichtig, dass Sie die Zertifikatsdateien nicht direkt in das Ticket hochladen. Andernfalls werden die Zertifikate als kompromittiert betrachtet und Adobe muss ein neues Zertifikat anfordern.
>Die Dateien sollten über SFTP in einen Ordner Ihrer Wahl hochgeladen werden, z. B. `var/ssl`, `/tmp/ssl` usw. - Verwenden Sie keine anderen Methoden, wie z. B. das Übertragen der Dateien in das Repository (was nur für unveränderliche Dateien erfolgen sollte, die keine vertraulichen Daten enthalten).

## Der Name Ihres Zertifikats

Der Name des SSL-Zertifikats ist nur für die primäre URL von Bedeutung, und es ist der primäre Host-Name, der durch die erste URL benannt wird und mit dem übereinstimmen muss, damit er validiert und erstellt wird. Wenn Sie einige URLs haben, werden diese als alternative Namenseinträge zum Zertifikat hinzugefügt. Wenn Sie mehrere URLs haben, die auf eine Adobe Commerce auf einer Cloud-Infrastruktur-Site verweisen, verfügen Sie nur über eine URL-Zertifizierung mit einem gemeinsamen Namen, an die dann alternative Betreffnamen angehängt werden, um Ihre Site mit SSL zu schützen.

## Welche Domain wird im Feld „Allgemeiner Name“ des Zertifikats angezeigt?

Die im Zertifikat angezeigte Domain ist nur die erste Domain, die zum TLS-Zertifikat hinzugefügt wird. Sie füllt das Feld **Allgemeiner Name** (**CN**) aus, und Browser zeigen diesen Namen zuerst an. Das Feld **Subject Alternative Name** (**SAN**) enthält alle DNS-Namen für das TLS-Zertifikat. Es gibt keine Möglichkeit, den angezeigten Gebrauchsnamen zu ändern oder anzufordern.

## Kann ich Platzhalter-TLS-Zertifikate verwenden?

Platzhalter-TLS-Zertifikate können nur mit Ihrem benutzerdefinierten Zertifikat verwendet werden, nicht aber mit Adobe Commerce Let&#39;s Encrypt-Zertifikaten. Im Rahmen unserer TLS-Optimierung stellt Adobe die Unterstützung für Platzhalter-TLS-Zertifikate ein. Wir identifizieren und kontaktieren Händler, die ein Platzhalterzertifikat mit Adobes Let&#39;s Encrypt-Zertifikaten verwenden und in der [!DNL Fastly] für Adobe Commerce konfiguriert sind. Wir bitten darum, diese Platzhalterzertifikate durch exakte Domains zu ersetzen, um die TLS-Abdeckung sicherzustellen. Um ein Platzhalter-TLS-Zertifikat zu ersetzen, besuchen Sie [ Abschnitt „Domain](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration#manage-domains) des [!DNL Fastly]-Plug-ins. Von hier aus können exakte Domains hinzugefügt und der Platzhalter entfernt werden. Beachten Sie, dass das DNS auf [!DNL Fastly] verweisen muss, damit diese neuen Domains über das CDN weitergeleitet werden. Sobald die Domains hinzugefügt und das DNS aktualisiert wurde, wird ein passendes [Let&#39;s ](https://letsencrypt.org/)) bereitgestellt. Wenn Sie eine Domain, die auf [!DNL Fastly] mit einem Platzhalter verweist, nicht entfernen, löscht Adobe das freigegebene Zertifikat. Dies kann zu einem Website-Ausfall führen, wenn Sie den URL-FQDN nicht konfiguriert und denselben URL-FQDN in Ihrem DNS eingerichtet haben. Sie sollten daher bestätigen, dass die konfigurierten URLs auch eine Eins-zu-eins-Übereinstimmung in ihrem DNS aufweisen, die auf [!DNL Fastly] verweist.

## Was sollte ich tun, wenn meine Domain nicht mehr auf Adobe Commerce verweist?

Wenn Ihre Domain nicht mehr auf Adobe Commerce verweist, entfernen Sie sie aus dem [!DNL Fastly]/Adobe Commerce-System. Weitere Informationen finden Sie [!DNL Fastly] [Löschen ](https://docs.fastly.com/en/guides/working-with-domains#deleting-a-domain) Domain). Es ist zwar nicht erforderlich, Ihre Domain auf Adobe Commerce zu verweisen, dennoch müssen Sie sicherstellen, dass ein TLS-Zertifikat für die Domain auf oberster Ebene erforderlich ist. Wenn eine Domain auf oberster Ebene erforderlich ist, aktualisieren Sie Ihr DNS, um auf Adobe Commerce zu verweisen. Wenn er bereits auf Adobe Commerce verweist, aktualisieren Sie Ihren CAA-Eintrag, um Folgendes einzuschließen [lets-encrypt](https://letsencrypt.org/). Wenn Sie diese Schritte ausführen, wird das LE-Zertifikat mit den erforderlichen sekundären URLs aktualisiert, die vom Zertifikat abgedeckt werden&#x200B;

## Verwandtes Lesen

[Bereitstellen von SSL-/TLS-](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#provision-ssltls-certificates) in unserer Entwicklerdokumentation
