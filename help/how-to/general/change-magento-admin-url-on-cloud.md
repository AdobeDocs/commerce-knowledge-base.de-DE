---
title: Ändern der Admin-URL in Adobe Commerce in der Cloud-Infrastruktur
description: Standardmäßig ist die [Commerce Admin](https://experienceleague.adobe.com/en/docs/commerce-admin/start/admin/admin)-URL auf *&lt;domain\_name&gt;/admin* festgelegt. Dieser Artikel zeigt, wie Sie die URL ändern.
exl-id: 6236370c-e0a2-45a6-a38f-12e219c540af
feature: Admin Workspace, Cloud
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# Ändern der Admin-URL in Adobe Commerce in der Cloud-Infrastruktur

Standardmäßig ist die URL [Commerce Admin](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/admin.html) auf *&lt;domain\_name>/admin* festgelegt. Dieser Artikel zeigt, wie Sie die URL ändern.

## Methode 1: Ändern mithilfe der Admin

Lesen Sie die Schritte: [Verwenden einer benutzerdefinierten Admin-URL > Wechsel vom Administrator](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/store-urls.html#use-a-custom-admin-url) in unserem Benutzerhandbuch.

## Methode 2: Hinzufügen der Umgebungsvariablen ADMIN\_URL

### Integrationsumgebung

Fügen Sie in [Cloud-](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html)&quot; eine neue Variable hinzu mit:

**name:** ADMIN\_URL **value:** neue Admin-URL

* Detaillierte Anweisungen finden Sie unter [Hinzufügen von Umgebungsvariablen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html#configure-environment) in unserer Entwicklerdokumentation.
* Weitere Informationen finden Sie [Umgebungsvariablen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html) in unserer Entwicklerdokumentation.

### Wenn Staging und Produktion in der Cloud-Konsole nicht verfügbar sind

[Senden eines Support-Tickets](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) mit der Aufforderung, die Variable ADMIN\_URL für Ihre Staging- oder Produktionsumgebung hinzuzufügen.

Wenn über die Cloud-Konsole auf die Staging- und Produktionsumgebung zugegriffen werden kann, fügen Sie die Umgebungsvariable hinzu, wie im Abschnitt *Integrationsumgebung* oben beschrieben.

### Hinzufügen von Variablen mithilfe der Cloud-CLI

Sie können die Variable ADMIN\_URL mit dem folgenden Cloud-CLI-Befehl hinzufügen (für die Haupt-URL):

`magento-cloud variable:update ADMIN_URL --value newAdmin_A8v10 -e master --inheritable false`

Detailliertere Anweisungen finden Sie unter [Ändern der Admin-](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html?lang=en#change-the-admin-url)) im Thema „Admin-Variablen“ im Handbuch Commerce on Cloud Infrastructure.

Beachten Sie, dass die Verwendung der Cloud-CLI zum Ändern der Variablen ADMIN\_URL eine erneute Bereitstellung der Umgebung Trigger. Variablen sind standardmäßig vererbt. Um eine Vererbung zu verhindern, verwenden Sie die Befehlsoptionen der Cloud-CLI, um anzugeben, dass der Variablenwert nicht von untergeordneten Umgebungen vererbt werden soll. Weitere Informationen finden [ unter „Sichtbarkeit](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html#visibility) in den Variablenebenen im Handbuch zu Commerce in Cloud-Infrastrukturen.
