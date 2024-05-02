---
title: Eingeschränkter Administratorzugriff, der Leistungsprobleme verursacht
description: Dieser Artikel bietet Lösungen für Fälle, in denen die Leistung durch die Verwendung von [Admin-Rollen mit eingeschränktem Rollenumfang auf der Website](https://docs.magento.com/m2/ee/user_guide/system/permissions-user-roles.html#step-2assign-resources) in unserem Benutzerhandbuch negativ beeinflusst wird.
exl-id: da168d6b-9cda-41e2-aa3c-f3f0dccc803d
feature: Admin Workspace, Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# Eingeschränkter Administratorzugriff, der Leistungsprobleme verursacht

Dieser Artikel bietet Lösungen für den Fall, dass die Leistung durch die Verwendung von [Admin-Rollen mit eingeschränktem Rollenbereich nach Website](https://docs.magento.com/m2/ee/user_guide/system/permissions-user-roles.html#step-2assign-resources) in unserem Benutzerhandbuch.

## Betroffene Produkte und Versionen

* Adobe Commerce lokal 2.2.x, 2.3.x
* Adobe Commerce auf Cloud-Infrastruktur 2.2.x, 2.3.x

## Problem

Wenn ein Admin-Benutzer mit eingeschränktem Rollenumfang auf der Website Vorgänge im Admin-Bedienfeld ausführt (einschließlich Anmelden, Speichern von Produkten usw.), erstellt Adobe Commerce den gespeicherten Cache neu. Die Neuerstellung des Caches wirkt sich negativ auf die Leistung aus und kann zu einem Site-Ausfall führen, insbesondere während Geschäftszeiten und/oder Zeiten mit hohem Traffic.

Das Problem wurde in Adobe Commerce 2.2.10 und 2.3.3 behoben.

## Lösung

Im Folgenden finden Sie die Optionen, um das Problem zu vermeiden:

* Aktualisieren Sie die Adobe Commerce-Anwendungsversion auf 2.2.10 oder 2.3.3. (Anweisungen hierzu finden Sie unter [Aktualisierung der Adobe Commerce-Version der Cloud-Infrastruktur](https://devdocs.magento.com/guides/v2.3/cloud/project/project-upgrade.html) in unserer Entwicklerdokumentation).
* Vermeiden Sie, den Umfang der Benutzerrollen für Administratoren nach Website zu beschränken, sofern möglich.
* [Senden eines Magento Support-Tickets](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), um einen Patch anzufordern, falls dieser verfügbar ist.

## Verwandtes Lesen

* [Benutzerrollen](https://docs.magento.com/m2/ee/user_guide/system/permissions-user-roles.html) in unserem Benutzerhandbuch.
