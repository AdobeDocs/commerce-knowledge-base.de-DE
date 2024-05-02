---
title: '[!DNL SendGrid] Dateibegrenzung für Adobe Commerce Cloud'
description: Dieser Artikel bietet eine Problemumgehung zum  [!DNL SendGrid] Einschränkung für Adobe Commerce in der Cloud-Infrastruktur.
feature: Deploy, Marketing Tools
role: Developer, Admin
exl-id: 48629f48-8100-4128-9211-53d947aecd49
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---

# [!DNL SendGrid] Beschränkung für Adobe Commerce Cloud

Dieser Artikel enthält einige Problemumgehungen zum [!DNL SendGrid] Beschränkung für Adobe Commerce in Cloud-Infrastruktur.

## Betroffene Produkte und Versionen

* Adobe Commerce zur Cloud-Infrastruktur, [alle unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)


## Problem

Sie versuchen, große Anhänge in E-Mails zu senden und sehen diese Protokollfehler:

In `/var/log/mail.log`

```shell
Month Date Time i-xxxxxxxxxxxxxxxxx postfix/sendmail[21408]: fatal: no-reply@xxxxxxxx.com(8080): message file too big
Month Date Time i-xxxxxxxxxxxxxxxxx postfix/sendmail[26434]: fatal: no-reply@xxxxxxxxx.com(8080): message file too big
```

In `/var/log/exception.log`

Produktion:

`/app/<project-id>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

Staging:

`/app/<project-id_stg>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

Staging2:

`/app/<project-id_stg2>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

## Ursache

[!DNL SendGrid] hat eine Systembegrenzung von 30 MB für E-Mails. Es wird empfohlen, keine Anlagen zu verwenden, die 10 MB überschreiten. Siehe [Senden von Anhängen](https://docs.sendgrid.com/ui/sending-email/attachments-with-digioh) Weitere Informationen finden Sie in der SendGrid-Dokumentation .

## Workaround

* Verwenden Sie keine Anlagen mit einer Auflösung von mehr als 6 MB oder 10 MB.
* Erwägen Sie die Verwendung eines Remote-SMTP-Servers auf Ihrer Adobe Commerce-Instanz. Eine Anleitung finden Sie unter [E-Mail-Kommunikation konfigurieren](https://experienceleague.adobe.com/docs/commerce-admin/systems/communications/email-communications.html) in unserem Administratorsystem-Handbuch.
* Konfigurieren Sie Ihren Server so, dass Dateien in Ihrem Modul gespeichert werden können, und fügen Sie dann den Link an die Dateien in den E-Mails an.

## Verwandtes Lesen

* [[!DNL SendGrid] Email Service](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/sendgrid.html) in unserem Commerce on Cloud Infrastructure Guide.
