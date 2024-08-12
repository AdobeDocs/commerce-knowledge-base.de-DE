---
title: Hinzufügen eines Teammitglieds zu Support-Benachrichtigungen
description: In diesem Artikel wird erläutert, wie ein Team-Mitglied in Support-Benachrichtigungen aufgenommen wird.
feature: Cloud, Support, Admin Workspace
role: Admin, Developer
exl-id: 63ea3f60-a509-447c-ac3d-bb2133141c80
source-git-commit: 771793d45000e65c1bf41137cd984d2977b0a9ff
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---

# Hinzufügen eines Teammitglieds zu Support-Benachrichtigungen

In diesem Artikel wird erläutert, wie ein Team-Mitglied einbezogen werden kann, um automatisch Supportaktualisierungen über E-Mail-Benachrichtigungen zu erhalten.

## Betroffene Produkte und Versionen

* Adobe Commerce in der Cloud-Infrastruktur, alle [unterstützten Versionen](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Ursache

* Das Teammitglied wurde nicht mit den erforderlichen Berechtigungen zum [!DNL cloud project] hinzugefügt.
* Das Team-Mitglied verfügt über kein Support-Konto.

## Lösung

1. Navigieren Sie zu &quot;**[!DNL Cloud Project URL]**&quot;(Beispiel: `https://us-3.magento.cloud/projects/xxxxxx/edit`).
1. Überprüfen Sie, ob das Teammitglied zum Projekt hinzugefügt wurde und eine [!DNL Super User] ist.

Wenn sie nicht zum Projekt hinzugefügt wurden, müssen Sie sie als [!DNL Super User] hinzufügen und [!DNL Shared Access] gewähren:

* [Verwalten des Benutzerzugriffs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) in unserem Benutzerhandbuch.
* [ Benutzer kann nicht zum Adobe Commerce-Cloud-Projekt hinzugefügt werden](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-add-user-adobe-commerce-cloud-project.html) in unserer Commerce-Wissensdatenbank.
* [Adobe Commerce Help Center-Benutzerhandbuch: Freigegebener Zugriff](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#shared-access) in unserer Commerce-Wissensdatenbank.

Wenn sie zum [!DNL cloud project] hinzugefügt wurden, aber nicht über den [!DNL Super User role] verfügen, aktualisieren Sie ihre [!DNL role] entsprechend in [Benutzerzugriff verwalten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html).

## Verwandtes Lesen

[Ehemalige Teammitglieder erhalten Adobe Commerce-Cloud-Benachrichtigungs-E-Mails ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/former-teammembers-receive-cloud-notification-emails.html)
