---
title: Ändern der Admin-URL in Adobe Commerce in der Cloud-Infrastruktur
description: Standardmäßig ist die URL [Commerce Admin](https://docs.magento.com/m2/ee/user_guide/stores/admin.html) auf *&lt;domain\_name&gt;/admin* gesetzt. Dieser Artikel zeigt, wie die URL geändert werden kann.
exl-id: 6236370c-e0a2-45a6-a38f-12e219c540af
feature: Admin Workspace, Cloud
source-git-commit: 04dba4e2adeaaa7649b817444024bf96e7830ad3
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# Ändern der Admin-URL in Adobe Commerce in der Cloud-Infrastruktur

Standardmäßig ist die URL [Commerce Admin](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/admin.html) auf *&lt;domain\_name>/admin* gesetzt. Dieser Artikel zeigt, wie die URL geändert werden kann.

## Methode 1: Änderung mithilfe des Administrators

Lesen Sie die Schritte: [Verwenden einer benutzerdefinierten Admin-URL > Ändern von Admin](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/store-urls.html#use-a-custom-admin-url) in unserem Benutzerhandbuch.

## Methode 2: Hinzufügen der Umgebungsvariablen ADMIN\_URL

### Integrationsumgebung

Fügen Sie in der [Cloud-Konsole](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html) eine neue Variable mit folgenden Eigenschaften hinzu:

**Name:** ADMIN\_URL **Wert:** neue Admin-URL

* Ausführliche Anweisungen finden Sie unter [Hinzufügen von Umgebungsvariablen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html#configure-environment) in unserer Entwicklerdokumentation.
* Weitere Informationen finden Sie unter [Umgebungsvariablen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html) in unserer Entwicklerdokumentation.

### Wenn Staging und Produktion nicht in der Cloud Console verfügbar sind

[Senden Sie ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), um die Variable ADMIN\_URL für Ihre Staging- oder Produktionsumgebung hinzuzufügen.

Wenn Staging und Produktion über die Cloud Console verfügbar sind, fügen Sie die Umgebungsvariable hinzu, wie im Abschnitt *Integrationsumgebung* oben beschrieben.

### Variablen mithilfe der Cloud CLI hinzufügen

Sie können die Variable ADMIN\_URL mit dem folgenden Cloud-CLI-Befehl hinzufügen (für main):

`magento-cloud variable:update ADMIN_URL --value newAdmin_A8v10 -e master --inheritable false`

Detaillierte Anweisungen finden Sie unter [Ändern der Admin-URL](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html?lang=en#change-the-admin-url) im Thema &quot;Admin-Variablen&quot;im Commerce on Cloud Infrastructure Guide.

Beachten Sie, dass die Verwendung der Cloud-CLI zum Ändern der ADMIN\_URL-Variablen eine Neuimplementierung der Umgebung Trigger. Variablen können standardmäßig vererbt werden. Um die Vererbung zu verhindern, verwenden Sie die Befehlsoptionen der Cloud-CLI, um anzugeben, dass der Variablenwert nicht von untergeordneten Umgebungen übernommen werden soll. Weitere Informationen finden Sie im Thema [Sichtbarkeit](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html#visibility) in den Variablenebenen im Commerce on Cloud Infrastructure Guide.
