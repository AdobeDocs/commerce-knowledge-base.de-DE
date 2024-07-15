---
title: Ehemalige Teammitglieder erhalten Adobe Commerce-Cloud-Benachrichtigungs-E-Mails
description: Dieser Artikel bietet eine Lösung für Adobe Commerce, bei der Benachrichtigungen über Cloud-Infrastrukturen an frühere Teammitglieder gesendet werden.
exl-id: b2535f66-8aec-4ddf-9a69-60879a0a1939
feature: Cloud, Communications, Paas
role: Developer
source-git-commit: 0017d43e221ef3023630f714c34aa65b368e214f
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 0%

---

# Ehemalige Teammitglieder erhalten Adobe Commerce-Cloud-Benachrichtigungs-E-Mails

Dieser Artikel bietet eine Lösung zum Entfernen von Benutzern aus der Liste der Benachrichtigungs-E-Mails, die sich wie folgt verhalten:
* Ehemalige Teammitglieder, die nicht mehr mit Ihrem Projekt verbunden sind.
* Aktuelle Teammitglieder, die die Benachrichtigungen nicht erhalten sollten.

## Problem

Ein Hinweis auf einen festgestellten Ausfall oder ein wichtiges Problem in Bezug auf das Cloud-Projekt/die Cloud-Umgebung wurde an Ihr Team gesendet. Dies umfasst Mitglieder, die möglicherweise nicht mehr mit Ihrem Projekt verknüpft sind, z. B. externe/Agenturentwickler oder Systemintegratoren. Sie möchten, dass diese Benutzer keine Benachrichtigungen mehr erhalten.

## Lösung

Es gibt zwei Möglichkeiten, die Benachrichtigungen zu stoppen, indem Sie die Benutzer aus Ihrem Projekt entfernen:

* Methode 1: Verwenden der Cloud [!DNL Project URL]. Anweisungen finden Sie unter [Verwalten des Benutzerzugriffs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) im Handbuch zur Cloud-Infrastruktur von Commerce .
* Methode 2: Verwenden der magento-cloud [!DNL CLI]. Anweisungen finden Sie unter [Verwalten von Benutzern mit dem  [!DNL CLI]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#manage-users-with-the-cli) im Handbuch zur Cloud-Infrastruktur von Commerce .

Wenn dies bereits geschehen ist und die E-Mail-Benachrichtigungen diese Benutzer dennoch weiterhin enthalten, senden Sie ein Support-Ticket, um anzufordern, dass sie aus der Einstellung *[!UICONTROL Always CC]* im Konto entfernt werden.

## Verwandtes Lesen

* [Anzeigen der Projektrolle eines Benutzers](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#view-a-user&#39;s-project-role) im Handbuch zur Cloud-Infrastruktur von Commerce.
* [So schließen Sie ein Teammitglied in Support-Benachrichtigungen ein](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-include-a-team-member-in-support-notifications.html) in die Commerce-KB ein.
