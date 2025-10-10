---
title: Admin 2FA-E-Mail-Benachrichtigungen werden nicht empfangen
description: Dieser Artikel enthält eine Fehlerbehebung, wenn Sie die E-Mail mit den Anweisungen zum Abschluss der Einrichtung nicht erhalten, nachdem Sie die Zwei-Faktor-Authentifizierung (2FA) eingerichtet haben, um die Sicherheit des Administratorzugriffs in Adobe Commerce auf die Cloud-Infrastruktur zu verbessern.
exl-id: 7ab6b2b4-6aca-4323-a45b-2b4e52955160
feature: Admin Workspace, Communications
role: Developer
source-git-commit: 9eaea028886e74fc06c9516801919cd7f650f98c
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# Admin 2FA-E-Mail-Benachrichtigungen werden nicht empfangen


## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur, alle Versionen

## Problem

Sie haben die Zwei-Faktor-Authentifizierung eingerichtet, um die Sicherheit des Admin-Zugriffs zu verbessern, erhalten jedoch keine E-Mail mit den Anweisungen zum Abschließen der Einrichtung.

## Ursache

Wenn Sie die Absender-E-Mail nicht richtig konfiguriert haben oder Ihre Domain in SendGrid nicht mit einem weißen Label versehen wurde, ist die E-Mail wahrscheinlich im Spam-Ordner gelandet.

## Fehlerbehebung

### Schritt 1: Spam-Ordner überprüfen

1. Wenn die E-Mail nicht im Spam-Ordner angezeigt wurde, führen Sie diese MySQL-Abfrage aus, um zu überprüfen, ob die E-Mail-Adressen konfiguriert wurden:

   ```sql
   select * from core_config_data where path like '%trans_email%';
   ```

   * Wenn keine Ergebnisse zurückgegeben werden, bedeutet dies, dass die Absenderadresse nicht konfiguriert wurde.
Da Sie keinen Zugriff auf den Administrator haben, müssen Sie die Konfiguration in die Datenbank einfügen. Fügen Sie die entsprechende E-Mail-Adresse ein und führen Sie die MySQL-Anweisung aus:

   ```
   insert into core_config_data (scope,scope_id,path,value) values ('default',0,'trans_email/ident_general/email', your-email@here.com)
   ```

   * Wenn ein Ergebnis zurückgegeben wird, fahren Sie mit (**2)**.

1. Wenn die E-Mail in Ihrem Spam-Ordner angezeigt wurde, klicken Sie auf den Link in der E-Mail. Wenn der Link seitdem abgelaufen ist, versuchen Sie erneut, sich anzumelden, um den Vorgang zu wiederholen.
1. Nachdem Sie Zugriff erhalten haben, gehen Sie zu **Stores** > **Konfiguration** > **Allgemein** > **E-Mail-Adressen speichern** und konfigurieren Sie die E-Mail-Adressen.

### Schritt 2: Wenn/nachdem die E-Mail-Adressen ordnungsgemäß konfiguriert wurden, SSH in die Umgebung einbinden und diesen Befehl ausführen:

```php
php -r "mail(<your email address>,<subject>,<content>,'To: <sender email>');"
```

Überprüfen Sie Ihren Spam-Ordner auf die E-Mail.

Wenn die E-Mail in Ihrem Spam-Ordner angezeigt wird, ist die E-Mail-Authentifizierung Ihrer Domain möglicherweise nicht vollständig für den ausgehenden Versand über SendGrid konfiguriert.

Wenn Sie den von Adobe verwalteten SendGrid-Service verwenden:

[Senden Sie ein Support-Ticket](https://experienceleague.adobe.com/home?support-tab=home#support) in dem Sie anfordern, dass Ihre Versand-Domain mit SendGrid authentifiziert *auch als „weiß gekennzeichnet* bezeichnet) wird.
Dieser Prozess umfasst das Hinzufügen von DNS-Einträgen (DKIM und SPF), um SendGrid zu autorisieren, E-Mails im Namen Ihrer Domain zu senden, was die Wahrscheinlichkeit erhöht, dass Ihre E-Mails an den Posteingang statt an den Spam-Ordner gesendet werden.

Wenn Sie Ihr eigenes SendGrid-Konto verwenden:

Sie sind dafür verantwortlich, Ihre Domain-Authentifizierungseinstellungen direkt in Ihrem SendGrid-Konto-Dashboard zu verwalten. Weitere Informationen finden Sie [ der SendGrid-](https://www.twilio.com/docs/sendgrid/ui/account-and-settings/how-to-set-up-domain-authentication) unter „Einrichten der Domain-Authentifizierung“.

>[!NOTE]
>
>Einige Kunden entscheiden sich möglicherweise für einen separat bereitgestellten SendGrid-Service, um die volle Kontrolle über E-Mail-Zustellbarkeit und Compliance (z. B. HIPAA-Anforderungen) zu haben. Stellen Sie sicher, dass Sie die richtigen Schritte zur Fehlerbehebung je nach dem verwendeten SendGrid-Service (Adobe-verwaltet vs. selbst-verwaltet) ausführen.


## Verwandtes Lesen

* [SendGrid](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/project/sendgrid) in unserer Entwicklerdokumentation.
