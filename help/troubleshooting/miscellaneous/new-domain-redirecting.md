---
title: Neue Domain leitet zur Standard-Domain um
description: Dieser Artikel bietet eine Lösung für das Problem, dass die neue Domain in der vorhandenen oder einer anderen Umgebung zur Standard-Domain umgeleitet wird.
exl-id: 88e9eb3f-9b82-4ca3-aa80-e49f360b3eb9
feature: Configuration
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '254'
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

1. Wenn die Domain innerhalb derselben Umgebung umgeleitet wird, stellen Sie sicher, dass Sie die [Variablen“ konfiguriert ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#modify-variables).
1. Wenn die Domain zu einer anderen Umgebung umleitet, überprüfen Sie, ob Sie den richtigen [!DNL Fastly]-Service konfiguriert haben, indem Sie den folgenden Befehl ausführen: `bin/magento fastly:conf:get -s`

>[!NOTE]
>
>Sie können die [!DNL Fastly] API-Anmeldeinformationen finden, indem Sie sich bei jeder Umgebung (Staging/Produktion) anmelden und die `/mnt/shared/fastly_tokens.txt` Datei überprüfen. Weitere Informationen finden Sie unter [configure [!DNL Fastly] services](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) im Handbuch Commerce on Cloud Infrastructure.

Wenn beide oben genannten Konfigurationen korrekt sind, reichen Sie ein Support-Ticket ein.

## Verwandtes Lesen

* [Checkliste für die Einrichtung einer neuen Domain](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/checklist-for-setting-up-a-new-domain.html) in unserer Support-Wissensdatenbank.
