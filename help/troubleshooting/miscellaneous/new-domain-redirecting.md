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

Dies geschieht, wenn die Variablen nicht aktualisiert werden, nachdem eine neue Domäne hinzugefügt wurde oder der falsche [!DNL Fastly] -Dienst in der Umgebung konfiguriert wurde.

## Lösung

1. Wenn die Domäne innerhalb derselben Umgebung umleitet, stellen Sie sicher, dass Sie die [Variablen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#modify-variables) konfiguriert haben.
1. Wenn die Domäne zu einer anderen Umgebung umleitet, überprüfen Sie, ob Sie den richtigen [!DNL Fastly]-Dienst konfiguriert haben, indem Sie den folgenden Befehl ausführen: `bin/magento fastly:conf:get -s`

>[!NOTE]
>
>Sie finden die [!DNL Fastly] -API-Anmeldeinformationen, indem Sie sich bei jeder Umgebung (Staging/Produktion) anmelden und die Datei `/mnt/shared/fastly_tokens.txt` überprüfen. Weitere Informationen finden Sie unter [Konfigurieren von [!DNL Fastly] Diensten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) im Handbuch zu Commerce on Cloud Infrastructure.

Wenn beide oben genannten Konfigurationen korrekt sind, senden Sie ein Support-Ticket.

## Verwandtes Lesen

* [Checkliste zum Einrichten einer neuen Domäne](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/checklist-for-setting-up-a-new-domain.html) in unserer Support-Wissensdatenbank.
