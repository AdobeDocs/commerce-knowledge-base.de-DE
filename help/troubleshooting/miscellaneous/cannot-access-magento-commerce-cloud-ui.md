---
title: Zugriff auf Adobe Commerce in der Cloud-Infrastruktur-Benutzeroberfläche nicht möglich
description: Dieser Artikel bietet Lösungen für das Problem, dass Sie sich nicht in Ihrer Adobe Commerce in der Cloud-Infrastruktur-Benutzeroberfläche anmelden und den „403-Fehler“ erhalten können.
exl-id: 948e4acd-abd6-4562-b9c0-771a977188ba
feature: Cloud, Paas
role: Developer
source-git-commit: 3d3d2da45d164efbbbaf8c878967caf83f845a59
workflow-type: tm+mt
source-wordcount: '277'
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
1. Wenn der Fehler weiterhin auftritt, [ Sie ein Support-Ticket ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
