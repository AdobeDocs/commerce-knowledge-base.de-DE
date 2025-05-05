---
title: Eingeschränkter Admin-Zugriff, der Leistungsprobleme verursacht
description: Dieser Artikel bietet Lösungen für den Fall, dass die Leistung durch die Verwendung von [Administratorrollen mit durch die Website eingeschränktem Rollenbereich](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/user-accounts/permissions-user-roles#step-2assign-resources) in unserem Benutzerhandbuch beeinträchtigt wird.
exl-id: da168d6b-9cda-41e2-aa3c-f3f0dccc803d
feature: Admin Workspace, Cache
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# Eingeschränkter Admin-Zugriff, der Leistungsprobleme verursacht

Dieser Artikel bietet Lösungen für den Fall, dass die Leistung durch die Verwendung von [Administratorrollen mit durch die Website eingeschränktem Rollenbereich](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/user-accounts/permissions-user-roles#step-2assign-resources) in unserem Benutzerhandbuch beeinträchtigt wird.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premises 2.2.x, 2.3.x
* Adobe Commerce auf Cloud-Infrastruktur 2.2.x, 2.3.x

## Problem

Wenn ein Administrator bzw. eine Administratorin mit einem durch die Website eingeschränkten Rollenbereich Vorgänge im Admin-Bedienfeld ausführt (einschließlich der Anmeldung, des Speicherns von Produkten usw.), erstellt Adobe Commerce den gespeicherten Cache neu. Die Neuerstellung des Cache wirkt sich negativ auf die Leistung aus und kann zu einem Ausfall der Site führen, insbesondere während der Geschäftszeiten und/oder bei hohem Traffic.

Das Problem wurde in Adobe Commerce 2.2.10 und 2.3.3 behoben.

## Lösung

Im Folgenden finden Sie die Optionen zum Vermeiden des Problems:

* Aktualisieren Sie die Adobe Commerce-Anwendungsversion auf 2.2.10 oder 2.3.3. (Anweisungen finden Sie unter [Upgrade von Adobe Commerce auf Cloud](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version)Infrastrukturversion in unserer Entwicklerdokumentation).
* Vermeiden Sie es nach Möglichkeit, den Umfang der Administratorrolle auf die Website einzuschränken.
* [Senden Sie ein Magento-Support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)-Ticket, um einen Patch anzufordern, falls er verfügbar ist.

## Verwandtes Lesen

* [Benutzerrollen](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/user-accounts/permissions-user-roles) in unserem Benutzerhandbuch.
