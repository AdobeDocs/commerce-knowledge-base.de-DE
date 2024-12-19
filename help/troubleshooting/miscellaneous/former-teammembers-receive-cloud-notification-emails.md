---
title: Ehemalige Team-Mitglieder erhalten Adobe Commerce Cloud-Benachrichtigungs-E-Mails
description: Dieser Artikel bietet eine Lösung für Adobe Commerce bei E-Mails zu Cloud-Infrastrukturbenachrichtigungen, die an ehemalige Team-Mitglieder gesendet werden.
exl-id: b2535f66-8aec-4ddf-9a69-60879a0a1939
feature: Cloud, Communications, Paas
role: Developer
source-git-commit: 0017d43e221ef3023630f714c34aa65b368e214f
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 0%

---

# Ehemalige Team-Mitglieder erhalten Adobe Commerce Cloud-Benachrichtigungs-E-Mails

Dieser Artikel bietet eine Lösung zum Entfernen von Benutzern aus der Empfängerliste von Benachrichtigungs-E-Mails, die:
* Ehemalige Team-Mitglieder, die nicht mehr mit Ihrem Projekt verknüpft sind.
* Aktuelle Team-Mitglieder, die die Benachrichtigungen nicht erhalten sollen.

## Problem

Ihr Team wurde über einen erkannten Ausfall oder ein wichtiges Problem in Bezug auf das Cloud-Projekt/die Cloud-Umgebung informiert. Dazu gehören Mitglieder, die möglicherweise nicht mehr mit Ihrem Projekt verknüpft sind, z. B. externe Entwickler/Agenturen oder Systemintegratoren. Sie möchten, dass diese Benutzer keine Benachrichtigungen mehr erhalten.

## Lösung

Es gibt zwei Möglichkeiten, die Benachrichtigungen zu stoppen, indem die Benutzenden aus Ihrem Projekt entfernt werden:

* Methode 1: Verwenden der Cloud-[!DNL Project URL]. Anweisungen hierzu finden [ unter &quot;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) verwalten“ im Handbuch zu Commerce in Cloud-Infrastrukturen .
* Methode 2: Verwenden der Magento-Cloud-[!DNL CLI]. Anweisungen hierzu finden [ im Handbuch zu Commerce  [!DNL CLI]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#manage-users-with-the-cli) Cloud-Infrastruktur unter Verwalten von Benutzern mit der .

Wenn Sie dies bereits getan haben und die E-Mail-Benachrichtigungen weiterhin diese Benutzer enthalten, senden Sie ein Support-Ticket, um anzufordern, dass sie aus der *[!UICONTROL Always CC]* für das Konto entfernt werden.

## Verwandtes Lesen

* [Zeigen Sie die Projektrolle eines Benutzers ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#view-a-user’s-project-role) Handbuch zu Commerce in Cloud-Infrastrukturen an.
* [Wie Sie ein Teammitglied in Support-Benachrichtigungen einbeziehen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-include-a-team-member-in-support-notifications.html) in der Commerce-KB.
