---
title: Neue Domain leitet zur Standard-Domain um
description: Dieser Artikel bietet eine Lösung für das Problem, dass die neue Domain in der vorhandenen oder einer anderen Umgebung zur Standard-Domain umgeleitet wird.
exl-id: 88e9eb3f-9b82-4ca3-aa80-e49f360b3eb9
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---

# Neue Domain leitet zur Standard-Domain um

Dieser Artikel bietet eine Lösung für das Problem, dass die neue Domain in der vorhandenen oder einer anderen Umgebung zur Standard-Domain umgeleitet wird.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud Pro-Infrastruktur (alle Versionen)

## Problem

Die neue Domain leitet zur Standard-Domain in der aktuellen Umgebung oder zur Standard-Domain einer anderen Umgebung um.

## Ursache

Dies geschieht, wenn die Variablen nicht aktualisiert werden, nachdem eine neue Domain hinzugefügt wurde oder der falsche [!DNL Fastly]-Service in der Umgebung konfiguriert wurde.

## Lösung

1. Wenn die Domain innerhalb derselben Umgebung umgeleitet wird, stellen Sie sicher, dass Sie die [Variablen“ konfiguriert ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html?lang=de#modify-variables).
1. Wenn die Domain zu einer anderen Umgebung umleitet, überprüfen Sie, ob Sie den richtigen [!DNL Fastly]-Service konfiguriert haben, indem Sie den folgenden Befehl ausführen: `bin/magento fastly:conf:get -s`

>[!NOTE]
>
>Sie können die [!DNL Fastly] API-Anmeldeinformationen finden, indem Sie sich bei jeder Umgebung (Staging/Produktion) anmelden und die `/mnt/shared/fastly_tokens.txt` Datei überprüfen. Weitere Informationen finden Sie unter [configure [!DNL Fastly] services](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=de) im Handbuch Commerce on Cloud Infrastructure.

Wenn beide oben genannten Konfigurationen korrekt sind, reichen Sie ein Support-Ticket ein.

## Verwandtes Lesen

* [Checkliste für die Einrichtung einer neuen Domain](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/checklist-for-setting-up-a-new-domain.html?lang=de) in unserer Support-Wissensdatenbank.
