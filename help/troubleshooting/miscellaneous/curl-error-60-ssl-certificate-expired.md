---
title: 'cURL error 60: SSL-Zertifikat abgelaufen'
description: "Dieser Artikel zeigt, wie Sie überprüfen können, wann eine Verzweigung nach dem Erhalt eines cURL-Fehlers 60 zum letzten Mal bereitgestellt wurde: SSL-Zertifikat ist in den Master- oder Integrationszweigen in Adobe Commerce in der Cloud-Infrastruktur abgelaufen."
exl-id: 74f1db7e-ee2b-4e27-8fcc-fe462a9e72c3
feature: Configuration
role: Developer
source-git-commit: 6f631ca35b663c386bca9efe6e56db266502c0b1
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# cURL-Fehler 60: SSL-Zertifikat abgelaufen

Dieser Artikel zeigt, wie Sie überprüfen können, wann eine Verzweigung das letzte Mal nach dem Erhalt einer `cURL error 60`: [!DNL SSL certificate] abgelaufen im [!DNL Master] oder [!DNL Integration] Zweigstellen in Adobe Commerce in der Cloud-Infrastruktur.

## Betroffene Produkte und Versionen

* Adobe Commerce zur Cloud-Infrastruktur, [alle unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Ursache

Die [!DNL SSL certificates] in diesen Verzweigungen gelten nur 30 Tage, und die Verzweigung kann innerhalb von 30 Tagen nicht erneut bereitgestellt worden sein.

Der Fehler sieht in etwa so aus:

```cURL
cURL error 60: SSL certificate problem: certificate has expired
```

## Lösung

Überprüfen Sie, wann die Verzweigung zuletzt bereitgestellt wurde. Wenn Sie den Schwellenwert von 30 Tagen überschreiten, stellen Sie die Verzweigung erneut bereit.

Zwei Methoden, um zu überprüfen, wann die letzte Bereitstellung durchgeführt wurde:

* [Methode 1: Verwendung [!DNL magento-cloud] CLI](#meth2).
* [Methode 2: Öffnen Sie die [!DNL Project URL]](#meth3).

Wenn die Bereitstellung erfolgreich abgeschlossen wurde, wird die [!DNL SSL certificate] automatisch verlängert.

Wenn die Bereitstellung fehlschlägt und Sie Hilfe bei der Lösung benötigen, [Support-Ticket einreichen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

### Methode 1: Verwendung [!DNL magento-cloud] CLI {#meth2}

Führen Sie diesen Befehl aus: `magento-cloud activity:list`

### Methode 2: Öffnen Sie die [!DNL Project URL] {#meth3}

Gehen Sie beispielsweise zu: `https://demo.magento.cloud/#/projects/<project>/environments/<environment>`und überprüfen Sie, wann die letzte Bereitstellung durchgeführt wurde.

## Verwandtes Lesen

In unserer Entwicklerdokumentation:

* [Cloud Manager-API: SSLC-Zertifikate](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/SSLCertificates)
* [Schnelles Einrichten: Bereitstellen von SSL-/TLS-Zertifikaten](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#provision-ssltls-certificates)

In unserer Support-Wissensdatenbank:

* [Benutzerdefinierte SSL-Zertifikatablaufinformationen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/custom-ssl-certificate-expiration-information.html)
* [SSL-Zertifikate (TLS) für Adobe Commerce in der Cloud-Infrastruktur](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/ssl-tls-certificates-for-magento-commerce-cloud-faq.html)
