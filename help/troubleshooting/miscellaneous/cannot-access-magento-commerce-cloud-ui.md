---
title: Zugriff auf Adobe Commerce in der Cloud-Infrastruktur-Benutzeroberfläche nicht möglich
description: Dieser Artikel bietet Lösungen für das Problem, dass Sie sich nicht in Ihrer Adobe Commerce in der Cloud-Infrastruktur-Benutzeroberfläche anmelden und den „403-Fehler“ erhalten können.
exl-id: 948e4acd-abd6-4562-b9c0-771a977188ba
feature: Cloud, Paas
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%
---
# Zugriff auf Adobe Commerce in der Cloud-Infrastruktur-Benutzeroberfläche nicht möglich

Dieser Artikel bietet Lösungen für das Problem, dass Sie sich nicht in Ihrer Adobe Commerce in der Cloud-Infrastruktur-Benutzeroberfläche anmelden und den *403-Fehler* erhalten können.

## Problem

Beim erstmaligen Anmelden bei Ihrer Adobe Commerce in der Cloud-Infrastruktur-Benutzeroberfläche wird die Fehlermeldung *403: Umgebungszugriff verweigert* angezeigt. Dieser Fehler kann auftreten, weil beim erstmaligen Aufrufen der Cloud-URL die primäre Verzweigung geladen wird und Sie möglicherweise keinen Zugriff auf diese Verzweigung haben.

## Lösung

Wenn beim erstmaligen Zugriff auf die URL der Fehler 403 auftritt, stellen Sie sicher, dass Sie in der primären Verzweigung über eine Rolle verfügen.

1. СWenden Sie sich an den Lizenzinhaber oder einen Super User im Projekt und stellen Sie sicher, dass dieser Ihnen Zugriff als **Benutzer auf Umgebungsebene** gewährt hat, der auch unter [Cloud-Projekte > Benutzer über die Cloud-Konsole verwalten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#manage-users-from-the-cloud-console) in unserer Entwicklerdokumentation beschrieben ist.

   Wenn Sie nur in einer bestimmten Verzweigung eine entsprechende Rolle haben, müssen Sie zur URL für diese Verzweigung gehen, z. B.
   `https://console.adobecommerce.com/<owner-name>/<project-id>/<branch-name>`

   Wenn Sie das nächste Mal auf die Haupt-URL zugreifen, wird standardmäßig die zuletzt besuchte Umgebung verwendet.

1. Wenn Sie sich immer noch nicht anmelden können, wenden Sie сsich an den Lizenzinhaber oder einen Superuser des Projekts und stellen Sie sicher, dass dieser Ihnen Zugriff **Benutzer auf Projektebene** gewährt, wie unter [Cloud-Projekte > Benutzer zum Projekt hinzufügen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#add-a-user-to-the-project) in unserer Entwicklerdokumentation beschrieben.
1. Wenn der Fehler weiterhin auftritt, [&#x200B; Sie ein Support-Ticket &#x200B;](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket).
