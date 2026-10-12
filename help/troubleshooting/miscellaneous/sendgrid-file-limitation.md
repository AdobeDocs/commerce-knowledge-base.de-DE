---
title: '[!DNL SendGrid] Dateibegrenzung für Adobe Commerce Cloud'
description: Dieser Artikel bietet eine Problemumgehung für die [!DNL SendGrid] von Adobe Commerce in Cloud-Infrastrukturen.
feature: Deploy, Marketing Tools
role: Developer, Admin
exl-id: 48629f48-8100-4128-9211-53d947aecd49
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%
---
# [!DNL SendGrid] für Adobe Commerce Cloud

In diesem Artikel finden Sie einige Problemumgehungen zur [!DNL SendGrid] für Adobe Commerce in Cloud-Infrastrukturen.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur, [alle unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)


## Problem

Sie versuchen, große Anhänge in E-Mails zu senden, und sehen die folgenden Protokollfehler:

in `/var/log/mail.log`

```shell
Month Date Time i-xxxxxxxxxxxxxxxxx postfix/sendmail[21408]: fatal: no-reply@xxxxxxxx.com(8080): message file too big
Month Date Time i-xxxxxxxxxxxxxxxxx postfix/sendmail[26434]: fatal: no-reply@xxxxxxxxx.com(8080): message file too big
```

in `/var/log/exception.log`

Produktion:

`/app/<project-id>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

Staging:

`/app/<project-id_stg>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

Staging2:

`/app/<project-id_stg2>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

## Ursache

[!DNL SendGrid] hat eine Systembegrenzung von 30 MB für E-Mails. Es wird empfohlen, keine Anhänge zu verwenden, die mehr als 10 MB umfassen. Weitere Informationen finden [&#x200B; in der &#x200B;](https://docs.sendgrid.com/ui/sending-email/attachments-with-digioh)-Dokumentation unter „Senden von Anhängen“.

## Abhilfe

* Verwenden Sie keine Anhänge mit mehr als 6 MB oder 10 MB.
* Erwägen Sie die Verwendung eines Remote-SMTP-Servers auf Ihrer Adobe Commerce-Instanz. Anweisungen hierzu finden Sie unter [Konfigurieren von E-Mail](https://experienceleague.adobe.com/docs/commerce-admin/systems/communications/email-communications.html) in unserem Admin-Systemhandbuch.
* Konfigurieren Sie Ihren Server neu, sodass Dateien in Ihrem Modul gespeichert werden können, und fügen Sie dann den Link zu den Dateien in den E-Mails hinzu.

## Verwandtes Lesen

* [[!DNL SendGrid] E-Mail](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/sendgrid.html)Service) in unserem Handbuch zu Commerce in Cloud-Infrastrukturen.
