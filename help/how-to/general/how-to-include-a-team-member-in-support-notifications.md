---
title: Hinzufügen eines Teammitglieds zu Support-Benachrichtigungen
description: In diesem Artikel wird erläutert, wie ein Team-Mitglied in Support-Benachrichtigungen aufgenommen wird.
feature: Cloud, Support, Admin Workspace
role: Admin, Developer
exl-id: 63ea3f60-a509-447c-ac3d-bb2133141c80
source-git-commit: 1c568d75534bbfe322d9f980b40c5dd64fc5b7a2
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# Hinzufügen eines Teammitglieds zu Support-Benachrichtigungen

In diesem Artikel wird erläutert, wie ein Team-Mitglied einbezogen werden kann, um automatisch Supportaktualisierungen über E-Mail-Benachrichtigungen zu erhalten.

## Betroffene Produkte und Versionen

* Adobe Commerce in der Cloud-Infrastruktur, alle [unterstützte Versionen](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Ursache

* Das Team-Mitglied wurde nicht zum [!DNL cloud project] mit den erforderlichen Berechtigungen.
* Das Team-Mitglied verfügt über kein Support-Konto.

## Lösung

1. Navigieren Sie zu **[!DNL Cloud Project URL]** (Beispiel: `https://us-3.magento.cloud/projects/xxxxxx/edit`).
1. Überprüfen Sie, ob das Teammitglied zum Projekt hinzugefügt wurde und eine [!DNL Super User].

Wenn sie [!DNL cloud project] Zugriff, Senden einer [Support-Anfrage beim Adobe Commerce Support Center](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) automatisch CC: sie auf allen Tickets und geben auch ihre **[!DNL MAGE ID]** (sofern verfügbar).

Wenn sie nicht zum Projekt hinzugefügt wurden, müssen Sie sie als [!DNL Super User] und Finanzhilfe [!DNL Shared Access]:

* [Verwalten des Benutzerzugriffs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) in unserem Benutzerhandbuch.
* [Benutzer kann nicht zum Adobe Commerce Cloud-Projekt hinzugefügt werden](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-add-user-adobe-commerce-cloud-project.html) in unserer Commerce-Wissensdatenbank.
* [Benutzerhandbuch zum Adobe Commerce Help Center für freigegebenen Zugriff](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#shared-access) in unserer Commerce-Wissensdatenbank.

Wenn sie zum [!DNL cloud project], aber nicht über die [!DNL Super User role], aktualisieren Sie die [!DNL role] entsprechend [Verwalten des Benutzerzugriffs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html).

## Verwandtes Lesen

[Ehemalige Teammitglieder erhalten Adobe Commerce-Cloud-Benachrichtigungs-E-Mails](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/former-teammembers-receive-cloud-notification-emails.html)
