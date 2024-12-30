---
title: Admin 2FA-E-Mail-Benachrichtigungen werden nicht empfangen
description: Dieser Artikel enthält eine Fehlerbehebung, wenn Sie die E-Mail mit den Anweisungen zum Abschluss der Einrichtung nicht erhalten, nachdem Sie die Zwei-Faktor-Authentifizierung (2FA) eingerichtet haben, um die Sicherheit des Administratorzugriffs in Adobe Commerce auf die Cloud-Infrastruktur zu verbessern.
exl-id: 7ab6b2b4-6aca-4323-a45b-2b4e52955160
feature: Admin Workspace, Communications
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '300'
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

Überprüfen Sie Ihren Spam-Ordner auf die E-Mail. Wenn die E-Mail dort angezeigt [, ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#login) Sie ein Support-Ticket ein, um die Domain in SendGrid mit einer weißen Kennzeichnung zu versehen.

## Verwandtes Lesen

* [SendGrid](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/project/sendgrid) in unserer Entwicklerdokumentation.
