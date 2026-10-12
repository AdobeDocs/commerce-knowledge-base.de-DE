---
title: Ehemalige Team-Mitglieder erhalten Adobe Commerce Cloud-Benachrichtigungs-E-Mails
description: Dieser Artikel bietet eine Lösung für Adobe Commerce bei E-Mails zu Cloud-Infrastrukturbenachrichtigungen, die an ehemalige Team-Mitglieder gesendet werden.
exl-id: b2535f66-8aec-4ddf-9a69-60879a0a1939
feature: Cloud, Communications, Paas
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: bb03f6c4-cab9-560e-9d02-5816e1808d17
    internal-label: Communications
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '336'
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

* Methode 1: Verwenden der Cloud-[!DNL Project URL]. Anweisungen hierzu finden [ unter &quot;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) verwalten“ im Handbuch zu Commerce in Cloud-Infrastrukturen .
* Methode 2: Verwenden der Magento-Cloud-[!DNL CLI]. Anweisungen hierzu finden [ im Handbuch zu Commerce  [!DNL CLI]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#manage-users-with-the-cli) Cloud-Infrastruktur unter Verwalten von Benutzern mit der .

Wenn Sie dies bereits getan haben und die E-Mail-Benachrichtigungen weiterhin diese Benutzer enthalten, senden Sie ein Support-Ticket, um anzufordern, dass sie aus der *[!UICONTROL Always CC]* für das Konto entfernt werden.

## Verwandtes Lesen

* [Zeigen Sie die Projektrolle eines Benutzers ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#view-a-user's-project-role) Handbuch zu Commerce in Cloud-Infrastrukturen an.
* [Wie Sie ein Teammitglied in Support-Benachrichtigungen einbeziehen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-include-a-team-member-in-support-notifications.html) in der Commerce-KB.
