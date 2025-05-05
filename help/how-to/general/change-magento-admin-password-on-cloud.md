---
title: Ändern des Administratorkennworts in Adobe Commerce in der Cloud-Infrastruktur
description: '![login_panel_s.png](assets/login_panel_s.png)'
exl-id: 1b6e867e-d314-4e7b-be95-d699e6749896
feature: Admin Workspace, Cloud
source-git-commit: 7dc84525aef4d59346bb9bc980a7ed9b7f6612cf
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 0%

---

# Ändern des Administratorkennworts in Adobe Commerce in der Cloud-Infrastruktur

## Methode 1: Kennwort vergessen (per E-Mail zurücksetzen)

![login_panel_s.png](assets/login_panel_s.png)

Lesen Sie die Schritte im Abschnitt [Zurücksetzen Ihres Kennworts bei Admin Sign-](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/admin-signin.html?lang=de#admin-sign-in)&quot; in unserem Benutzerhandbuch.

Nachfolgend finden Sie die kritischen Nutzungshinweise.

### Ausgehende E-Mails aktivieren

Bevor Sie das Formular **Kennwort vergessen** verwenden, [ Sie ausgehende E-Mails aktivieren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/outgoing-emails.html?lang=de) mithilfe der [Cloud-Konsole](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=de).

### Junk-E-Mail-Ordner überprüfen

Wenn Sie die Nachricht mit dem Link „Kennwort zurücksetzen“ nicht finden können, überprüfen Sie Ihren Ordner *Junk-E-Mail*. Der Name der E-Mail lautet *Bestätigung für das Zurücksetzen des Kennworts für den Admin-Benutzernamen*.

## Methode 2: Neuen Admin-Benutzer hinzufügen

Wenn Sie das Kennwort für den vorhandenen Benutzer nicht wiederherstellen oder zurücksetzen können, können Sie einen neuen Admin-Benutzer erstellen und ein Kennwort für diesen Benutzer festlegen. Gehen Sie dazu wie folgt vor:

1. Verwenden Sie [SSH, um sich bei der Remote-Umgebung anzumelden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=de).
1. Führen Sie den folgenden Befehl aus: `bin/magento admin:user:create   --admin-user=%user_name% --admin-password=%your_password% --admin-email=%your_email% --admin-firstname=%admin_user_first_name% --admin-lastname=%admin_user_last_name%`
