---
title: Ändern des Administratorkennworts in Adobe Commerce in der Cloud-Infrastruktur
description: '![login_panel_s.png](assets/login_panel_s.png)'
exl-id: 1b6e867e-d314-4e7b-be95-d699e6749896
feature: Admin Workspace, Cloud
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%
---
# Ändern des Administratorkennworts in Adobe Commerce in der Cloud-Infrastruktur

## Methode 1: Kennwort vergessen (per E-Mail zurücksetzen)

![login_panel_s.png](assets/login_panel_s.png)

Lesen Sie die Schritte im Abschnitt [Zurücksetzen Ihres Kennworts bei Admin Sign-](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/admin-signin.html#admin-sign-in)&quot; in unserem Benutzerhandbuch.

Nachfolgend finden Sie die kritischen Nutzungshinweise.

### Ausgehende E-Mails aktivieren

Bevor Sie das Formular **Kennwort vergessen** verwenden, stellen Sie sicher, dass Sie [ausgehende E-Mails aktivieren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/outgoing-emails.html) mithilfe der [Cloud-Konsole](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html). Dies gilt nur für Integrationsumgebungen und Sandbox-Projekte.

Wenn ausgehende E-Mails in Pro Produktion oder Staging wirklich deaktiviert sind - was bedeutet, dass die E-Mail nicht von SendGrid aufgenommen wurde - können Sie dies überprüfen, indem Sie die Option [E-Mails in der Cloud-Konsole aktivieren](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/project/outgoing-emails#enable-emails-in-the-cli) aktivieren. Wenn das Problem weiterhin besteht, können Sie ein Adobe-Support[Ticket ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide).

### Junk-E-Mail-Ordner überprüfen

Wenn Sie die Nachricht mit dem Link „Kennwort zurücksetzen“ nicht finden können, überprüfen Sie Ihren Ordner *Junk-E-Mail*. Der Name der E-Mail lautet *Bestätigung für das Zurücksetzen des Kennworts für den Admin-Benutzernamen*.

## Methode 2: Neuen Admin-Benutzer hinzufügen

Wenn Sie das Kennwort für den vorhandenen Benutzer nicht wiederherstellen oder zurücksetzen können, können Sie einen neuen Admin-Benutzer erstellen und ein Kennwort für diesen Benutzer festlegen. Gehen Sie dazu wie folgt vor:

1. Verwenden Sie [SSH, um sich bei der Remote-Umgebung anzumelden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Führen Sie den folgenden Befehl aus: `bin/magento admin:user:create   --admin-user=%user_name% --admin-password=%your_password% --admin-email=%your_email% --admin-firstname=%admin_user_first_name% --admin-lastname=%admin_user_last_name%`
