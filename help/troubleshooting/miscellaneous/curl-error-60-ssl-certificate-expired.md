---
title: 'cURL-Fehler 60: SSL-Zertifikat abgelaufen'
description: 'In diesem Artikel wird gezeigt, wie Sie überprüfen können, wann die letzte Bereitstellung einer Verzweigung nach Erhalt eines cURL-Fehlers 60 erfolgte: SSL-Zertifikat ist in den Master- oder Integrationsverzweigungen in Adobe Commerce in der Cloud-Infrastruktur abgelaufen.'
exl-id: 74f1db7e-ee2b-4e27-8fcc-fe462a9e72c3
feature: Configuration
role: Developer
source-git-commit: dcaae51408534b82181b268f60905b123e240900
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# cURL-Fehler 60: SSL-Zertifikat abgelaufen

In diesem Artikel wird gezeigt, wie Sie überprüfen können, wann die letzte Bereitstellung einer Verzweigung nach Erhalt einer `cURL error 60` erfolgte: [!DNL SSL certificate] abgelaufen in der [!DNL Master] oder [!DNL Integration] Verzweigungen in Adobe Commerce auf Cloud-Infrastruktur.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur, [alle unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Ursache

Die [!DNL SSL certificates] in diesen Verzweigungen sind nur 30 Tage gültig und die Verzweigung wurde möglicherweise in mehr als 30 Tagen nicht erneut bereitgestellt.

Der Fehler sieht in etwa so aus:

```cURL
cURL error 60: SSL certificate problem: certificate has expired
```

>[!NOTE]
>
>Diese Zertifikate werden nicht von bekannten externen Zertifizierungsstellen wie [!DNL Let's Encrypt] oder [!DNL DigiCert] signiert. Sie werden von der Adobe-Plattform zu Test- und Entwicklungszwecken verwaltet und sind in Browsern oder in cURLs möglicherweise nicht standardmäßig vertrauenswürdig, es sei denn, Sie vertrauen dem Stamm, der das Zertifikat ausstellt, ausdrücklich.

## Lösung

Überprüfen Sie, wann die Verzweigung zuletzt bereitgestellt wurde. Wenn der Schwellenwert von 30 Tagen überschritten hat, stellen Sie die Verzweigung erneut bereit.

Zwei Methoden, um zu überprüfen, wann die letzte Bereitstellung durchgeführt wurde:

* [Methode 1: Use [!DNL magento-cloud] CLI](#meth2).
* [Methode 2: Öffnen Sie die  [!DNL Project URL]](#meth3).

Wenn die Bereitstellung erfolgreich abgeschlossen wurde, wird die [!DNL SSL certificate] automatisch erneuert.

Wenn die Bereitstellung fehlschlägt und Sie Hilfe bei der Lösung benötigen, [ Sie ein Support-Ticket ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

### Methode 1: Verwenden [!DNL magento-cloud] CLI {#meth2}

Führen Sie diesen Befehl aus: `magento-cloud activity:list --type=environment.push`

### Methode 2: Öffnen Sie die [!DNL Project URL] {#meth3}

Navigieren Sie zu beispielsweise: `https://demo.magento.cloud/#/projects/<project>/environments/<environment>` und überprüfen Sie, wann die letzte Bereitstellung durchgeführt wurde.

## Verwandtes Lesen

In unserer Entwicklerdokumentation:

* [Cloud Manager-API: SSLCertificates](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/SSLCertificates)
* [Schnelles Einrichten: Bereitstellen von SSL-/TLS-Zertifikaten](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#provision-ssltls-certificates)

In unserer Support-Wissensdatenbank:

* [Informationen zum Ablauf von benutzerdefinierten SSL-Zertifikaten](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/custom-ssl-certificate-expiration-information.html)
* [SSL (TLS)-Zertifikate für Adobe Commerce in der Cloud-Infrastruktur](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/ssl-tls-certificates-for-magento-commerce-cloud-faq.html)
