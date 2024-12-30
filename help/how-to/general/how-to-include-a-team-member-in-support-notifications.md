---
title: Wie man ein Teammitglied in Support-Benachrichtigungen einbezieht
description: In diesem Artikel wird erläutert, wie Sie ein Team-Mitglied in Support-Benachrichtigungen einbeziehen.
feature: Cloud, Support, Admin Workspace
role: Admin, Developer
exl-id: 63ea3f60-a509-447c-ac3d-bb2133141c80
source-git-commit: 771793d45000e65c1bf41137cd984d2977b0a9ff
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---

# Wie man ein Teammitglied in Support-Benachrichtigungen einbezieht

In diesem Artikel wird erläutert, wie Sie ein Team-Mitglied einbeziehen können, um Support-Updates automatisch per E-Mail zu erhalten.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur, alle [unterstützten Versionen](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Ursache

* Das Teammitglied wurde dem [!DNL cloud project] nicht mit den erforderlichen Berechtigungen hinzugefügt.
* Das Teammitglied hat kein Support-Konto.

## Lösung

1. Navigieren Sie zur **[!DNL Cloud Project URL]** (Beispiel: `https://us-3.magento.cloud/projects/xxxxxx/edit`).
1. Überprüfen Sie, ob das Teammitglied zum Projekt hinzugefügt wurde und ein [!DNL Super User] ist.

Wenn sie dem Projekt nicht hinzugefügt wurden, müssen Sie sie als [!DNL Super User] hinzufügen und [!DNL Shared Access] gewähren:

* [Verwalten des Benutzerzugriffs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) in unserem Benutzerhandbuch.
* [Benutzer kann nicht zum Adobe Commerce-Cloud-Projekt hinzugefügt werden](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-add-user-adobe-commerce-cloud-project.html) in unserer Commerce-Wissensdatenbank.
* [Benutzerhandbuch für Adobe Commerce Help Center: Freigegebener Zugriff](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#shared-access) in unserer Commerce-Wissensdatenbank.

Wenn sie zur [!DNL cloud project] hinzugefügt wurden, aber nicht über die [!DNL Super User role] verfügen, aktualisieren Sie ihren [!DNL role] entsprechend unter [Benutzerzugriff verwalten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html).

## Verwandtes Lesen

[Ehemalige Team-Mitglieder erhalten Adobe Commerce-E-Mails zur Cloud-Benachrichtigung](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/former-teammembers-receive-cloud-notification-emails.html)
