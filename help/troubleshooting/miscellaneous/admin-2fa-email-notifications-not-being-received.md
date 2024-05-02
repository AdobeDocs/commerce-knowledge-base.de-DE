---
title: Keine E-Mail-Benachrichtigungen von Admin 2FA
description: Dieser Artikel enthält eine Fehlerbehebung, wenn Sie die E-Mail nicht mit den Einrichtungsanweisungen erhalten, nachdem Sie die Zwei-Faktor-Authentifizierung (2FA) eingerichtet haben, um die Sicherheit des Administratorzugriffs in Adobe Commerce auf der Cloud-Infrastruktur zu verbessern.
exl-id: 7ab6b2b4-6aca-4323-a45b-2b4e52955160
feature: Admin Workspace, Communications
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# Keine E-Mail-Benachrichtigungen von Admin 2FA


## Betroffene Produkte und Versionen

* Adobe Commerce in der Cloud-Infrastruktur, alle Versionen

## Problem

Sie haben die Zweifaktorauthentifizierung eingerichtet, um die Sicherheit des Administratorzugriffs zu verbessern, erhalten jedoch keine E-Mail mit Anweisungen zum Abschluss des Setups.

## Ursache

Wenn Sie die Sender-E-Mail nicht richtig konfiguriert haben oder Ihre Domain in SendGrid nicht auf die Whitelist gesetzt wurde, wäre die E-Mail wahrscheinlich im Spam-Ordner gelandet.

## Fehlerbehebung

### Schritt 1: Überprüfen des Spam-Ordners

1. Wenn die E-Mail nicht in Ihrem Spam-Ordner angezeigt wurde, führen Sie diese MySQL-Abfrage aus, um zu überprüfen, ob die E-Mail-Adressen konfiguriert wurden:

   ```sql
   select * from core_config_data where path like '%trans_email%';
   ```

   * Wenn keine Ergebnisse zurückgegeben werden, bedeutet dies, dass die Absenderadresse nicht konfiguriert wurde.
   * Wenn ein Ergebnis zurückgegeben wird, fahren Sie mit **Schritt 2**.

1. Wenn die E-Mail in Ihrem Spam-Ordner erscheint, klicken Sie auf den Link in der E-Mail. Wenn der Link seither abgelaufen ist, versuchen Sie erneut, sich anzumelden, um den Vorgang zu wiederholen.
1. Sobald Sie Zugriff erhalten haben, navigieren Sie zu **Stores** > **Konfiguration** > **Allgemein** > **E-Mail-Adressen speichern** und konfigurieren Sie die E-Mail-Adressen.

### Schritt 2: Wenn/nachdem die E-Mail-Adressen ordnungsgemäß konfiguriert wurden, SSH in die Umgebung und führen Sie folgenden Befehl aus:

```php
php -r "mail(<your email address>,<subject>,<content>,'To: <sender email>');"
```

Überprüfen Sie Ihren Spam-Ordner auf die E-Mail. Wenn die E-Mail dort angezeigt wurde, [Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#login) , um anzufordern, dass die Domäne in SendGrid eine weiße Beschriftung aufweist.

## Verwandtes Lesen

* [SendGrid](https://devdocs.magento.com/cloud/project/sendgrid.html) in unserer Entwicklerdokumentation.
