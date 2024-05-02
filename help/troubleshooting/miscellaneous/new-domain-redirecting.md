---
title: Neue Domäne leitet zur Standarddomäne um
description: Dieser Artikel enthält eine Fehlerbehebung für das Problem, dass die neue Domäne in der vorhandenen oder anderen Umgebung zur Standarddomäne weiterleitet.
exl-id: 88e9eb3f-9b82-4ca3-aa80-e49f360b3eb9
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---

# Neue Domäne leitet zur Standarddomäne um

Dieser Artikel enthält eine Fehlerbehebung für das Problem, dass die neue Domäne in der vorhandenen oder anderen Umgebung zur Standarddomäne weiterleitet.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-interne Infrastruktur (alle Versionen)

## Problem

Die neue Domäne leitet zur Standarddomäne in der aktuellen Umgebung oder zur Standarddomäne einer anderen Umgebung um.

## Ursache

Dies geschieht, wenn die Variablen nach dem Hinzufügen einer neuen Domäne oder der falschen nicht aktualisiert werden [!DNL Fastly] -Dienst wurde in der Umgebung konfiguriert.

## Lösung

1. Wenn die Domäne innerhalb derselben Umgebung umgeleitet wird, stellen Sie sicher, dass Sie die [Variablen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#modify-variables).
1. Wenn die Domäne zu einer anderen Umgebung umleitet, überprüfen Sie, ob Sie die richtige Konfiguration vorgenommen haben. [!DNL Fastly] -Dienst, indem Sie den folgenden Befehl ausführen: `bin/magento fastly:conf:get -s`

>[!NOTE]
>
>Sie finden die [!DNL Fastly] API-Anmeldeinformationen durch Anmelden bei jeder Umgebung (Staging/Produktion) und Überprüfen der `/mnt/shared/fastly_tokens.txt` -Datei. Weitere Informationen finden Sie unter [konfigurieren [!DNL Fastly] Dienstleistungen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) im Commerce on Cloud Infrastructure Guide.

Wenn beide oben genannten Konfigurationen korrekt sind, senden Sie ein Support-Ticket.

## Verwandtes Lesen

* [Checkliste zum Einrichten einer neuen Domäne](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/checklist-for-setting-up-a-new-domain.html) in unserer Wissensdatenbank.
