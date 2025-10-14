---
title: Ehemalige Team-Mitglieder erhalten Adobe Commerce Cloud-Benachrichtigungs-E-Mails
description: Dieser Artikel bietet eine Lösung für Adobe Commerce bei E-Mails zu Cloud-Infrastrukturbenachrichtigungen, die an ehemalige Team-Mitglieder gesendet werden.
exl-id: b2535f66-8aec-4ddf-9a69-60879a0a1939
feature: Cloud, Communications, Paas
role: Developer
source-git-commit: bd199fac6d8f33491b9fa0f508b2bb52d56b46a5
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 0%

---

# Ehemalige Team-Mitglieder erhalten Adobe Commerce Cloud-Benachrichtigungs-E-Mails

Dieser Artikel bietet eine Lösung zum Entfernen von Benutzern aus der Empfängerliste von Benachrichtigungs-E-Mails, die:

* Ehemalige Team-Mitglieder, die nicht mehr mit Ihrem Projekt verknüpft sind.
* Aktuelle Team-Mitglieder, die die Benachrichtigungen nicht erhalten sollen.

## Problem

Ihr Team wurde über einen erkannten Ausfall oder ein wichtiges Problem in Bezug auf das Cloud-Projekt/die Cloud-Umgebung informiert. Dazu gehören Mitglieder, die möglicherweise nicht mehr mit Ihrem Projekt verknüpft sind, z. B. externe Entwickler/Agenturen oder Systemintegratoren. Sie möchten, dass diese Benutzer keine Benachrichtigungen mehr erhalten.

## Lösung

>[!NOTE]
>
>Wenn Sie ein externer Entwickler/eine Agentur oder ein Systemintegrator sind und nicht mehr mit dem Projekt verknüpft sind, müssen Sie sich an den Projektbesitzer oder den Projektadministrator für dieses Projekt wenden, um Hilfe zu erhalten.

Es gibt zwei Möglichkeiten, die Benachrichtigungen zu stoppen, indem die Benutzenden aus Ihrem Projekt entfernt werden:

* Methode 1: Verwenden der Cloud-[!DNL Project URL]. Anweisungen hierzu finden [&#x200B; unter &quot;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=de) verwalten“ im Handbuch zu Commerce in Cloud-Infrastrukturen .
* Methode 2: Verwenden der Magento-Cloud-[!DNL CLI]. Anweisungen hierzu finden [&#x200B; im Handbuch zu Commerce  [!DNL CLI]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=de#manage-users-with-the-cli) Cloud-Infrastruktur unter Verwalten von Benutzern mit der .

Wenn Sie dies bereits getan haben und die E-Mail-Benachrichtigungen weiterhin diese Benutzer enthalten, senden Sie ein Support-Ticket, um anzufordern, dass sie aus der *[!UICONTROL Always CC]* für das Konto entfernt werden.

## Verwandtes Lesen

* [Zeigen Sie die Projektrolle eines Benutzers &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=de#view-a-user&?lang=de#39;s-project-role) Handbuch zu Commerce in Cloud-Infrastrukturen an.
* [Wie Sie ein Teammitglied in Support-Benachrichtigungen einbeziehen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-include-a-team-member-in-support-notifications.html?lang=de) in der Commerce-KB.
