---
title: Zugriff auf Adobe Commerce über die Benutzeroberfläche der Cloud-Infrastruktur nicht möglich
description: Dieser Artikel enthält Lösungen für das Problem, dass Sie sich nicht bei Ihrer Adobe Commerce in der Cloud-Infrastruktur-Benutzeroberfläche anmelden und den "403-Fehler"erhalten können.
exl-id: 948e4acd-abd6-4562-b9c0-771a977188ba
feature: Cloud, Paas
role: Developer
source-git-commit: 3d3d2da45d164efbbbaf8c878967caf83f845a59
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# Zugriff auf Adobe Commerce über die Benutzeroberfläche der Cloud-Infrastruktur nicht möglich

Dieser Artikel enthält Lösungen für das Problem, dass Sie sich nicht in der Benutzeroberfläche der Cloud-Infrastruktur bei Ihrer Adobe Commerce anmelden und den Fehler *403* erhalten können.

## Problem

Wenn Sie zum ersten Mal versuchen, sich bei Ihrer Adobe Commerce auf der Benutzeroberfläche der Cloud-Infrastruktur anzumelden, erhalten Sie den Fehler &quot;*403: Zugriff auf die Umgebung verweigert*&quot;. Dieser Fehler kann auftreten, weil Sie zum ersten Mal die Masterverzweigung in die Cloud-URL laden und möglicherweise keinen Zugriff auf diese Verzweigung haben.

## Lösung

Wenn beim erstmaligen Zugriff auf die URL ein 403-Fehler auftritt, stellen Sie sicher, dass Sie in der Masterverzweigung über eine Rolle verfügen.

1. С Sie sich an den Lizenzinhaber oder einen Superuser im Projekt wenden und stellen Sie sicher, dass dieser Ihnen als **Benutzer auf Umgebungsebene** Zugriff gewährt hat. Dies wird auch in der Entwicklerdokumentation unter [Cloud-Projekte > Verwalten von Benutzern über die Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#manage-users-from-the-cloud-console) beschrieben.

   Wenn Sie nur eine entsprechende Rolle in einem bestimmten Zweig haben, müssen Sie zur URL für diesen Zweig navigieren, z. B.
   `https://console.adobecommerce.com/<owner-name>/<project-id>/<branch-name>`

   Wenn Sie das nächste Mal auf die Haupt-URL zugreifen, wird standardmäßig die zuletzt besuchte Umgebung verwendet.

1. Wenn Sie sich immer noch nicht anmelden können, wenden с sich an den Lizenzinhaber oder einen Superuser im Projekt und stellen Sie sicher, dass dieser Ihnen als **Benutzer auf Projektebene** Zugriff gewährt hat, wie in [Cloud-Projekte > Benutzer zum Projekt hinzufügen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#add-a-user-to-the-project) in unserer Entwicklerdokumentation beschrieben.
1. Wenn der Fehler weiterhin auftritt, senden [ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
