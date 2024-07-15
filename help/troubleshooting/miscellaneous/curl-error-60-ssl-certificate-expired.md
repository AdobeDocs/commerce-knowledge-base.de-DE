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

In diesem Artikel wird gezeigt, wie geprüft wird, wann ein Zweig das letzte Mal bereitgestellt wurde, nachdem ein `cURL error 60` erhalten wurde: [!DNL SSL certificate] ist in den Verzweigungen [!DNL Master] oder [!DNL Integration] in Adobe Commerce in der Cloud-Infrastruktur abgelaufen.

## Betroffene Produkte und Versionen

* Adobe Commerce in der Cloud-Infrastruktur, [alle unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Ursache

Die [!DNL SSL certificates] in diesen Verzweigungen sind nur für 30 Tage gültig und der Zweig wurde möglicherweise innerhalb von 30 Tagen nicht erneut bereitgestellt.

Der Fehler sieht in etwa so aus:

```cURL
cURL error 60: SSL certificate problem: certificate has expired
```

## Lösung

Überprüfen Sie, wann die Verzweigung zuletzt bereitgestellt wurde. Wenn Sie den Schwellenwert von 30 Tagen überschreiten, stellen Sie die Verzweigung erneut bereit.

Zwei Methoden, um zu überprüfen, wann die letzte Bereitstellung durchgeführt wurde:

* [Methode 1: Verwenden Sie  [!DNL magento-cloud] CLI](#meth2).
* [Methode 2: Öffnen Sie den  [!DNL Project URL]](#meth3).

Wenn die Bereitstellung erfolgreich abgeschlossen wurde, wird der [!DNL SSL certificate] automatisch erneuert.

Wenn die Bereitstellung fehlschlägt und Sie Hilfe beim Auflösen benötigen, senden [ein Support-Ticket](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

### Methode 1: Verwenden von [!DNL magento-cloud] CLI {#meth2}

Führen Sie diesen Befehl aus: `magento-cloud activity:list`

### Methode 2: Öffnen Sie den [!DNL Project URL] {#meth3}

Wechseln Sie zu , z. B. &quot;`https://demo.magento.cloud/#/projects/<project>/environments/<environment>`&quot;, und überprüfen Sie, wann die letzte Bereitstellung durchgeführt wurde.

## Verwandtes Lesen

In unserer Entwicklerdokumentation:

* [Cloud Manager API: SSLCertificates](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/SSLCertificates)
* [Schnelles Einrichten: Bereitstellen von SSL-/TLS-Zertifikaten](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#provision-ssltls-certificates)

In unserer Support-Wissensdatenbank:

* [Ablaufinformationen des benutzerdefinierten SSL-Zertifikats](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/custom-ssl-certificate-expiration-information.html)
* [SSL-Zertifikate (TLS) für Adobe Commerce in der Cloud-Infrastruktur](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/ssl-tls-certificates-for-magento-commerce-cloud-faq.html)
