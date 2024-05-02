---
title: Fehler bei der Überprüfung der Fastly-Anmeldedaten
description: Dieser Artikel bietet eine Lösung für das Problem, bei dem ein Benutzer beim Überprüfen der Fastly-Anmeldedaten einen Fehler erhält.
exl-id: 02104731-6666-47a6-abc6-215812f09915
feature: Configuration
role: Developer
source-git-commit: 831a928dbe8fd6b37f3fe9ad5dc35ee80e11a578
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# Fehler bei der Überprüfung der Fastly-Anmeldedaten

Dieser Artikel bietet eine Lösung für das Problem, bei dem ein Benutzer beim Überprüfen der Fastly-Anmeldedaten einen Fehler erhält.

## Problem

Der Benutzer erhält bei der Validierung der Fastly-Anmeldedaten einen Fehler.

## Betroffene Produkte und Versionen

* Adobe Commerce (alle Bereitstellungsmethoden): Alle Versionen
* Erweiterung oder Technologie (Fastly, New Relic usw.) Version Fastly

## Lösung

1. Vergewissern Sie sich, dass Sie über die richtige Fastly-Dienst-ID und das richtige API-Token verfügen, und versuchen Sie erneut, die Überprüfung durchzuführen. Detaillierte Anweisungen finden Sie unter [Testen der Fastly-Anmeldeinformationen](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#test-the-fastly-credentials) in unserer Entwicklerdokumentation.
1. Wenn die Überprüfung der Anmeldeinformationen fehlschlägt, führen Sie den folgenden curl-Befehl aus, um den Status des Dienstes zu bestätigen:

   ```curl
   curl -H "Fastly-Key: <API key>" https://api.fastly.com/service/<service ID>/version/active
   ```

1. Wenn der obige Befehl einen Fehler wie den folgenden zurückgibt: *{&quot;msg&quot;:&quot;Token $TOKEN ist 2021-09-28T02 abgelaufen:03:37Z&quot;}* senden, senden Sie ein Support-Ticket, um ein neues API-Token anzufordern.

   Informationen zum Senden eines Support-Tickets finden Sie unter [Adobe Commerce Help Center-Benutzerhandbuch > SUPPORT-TICKETS](/help/help-center-guide/help-center/magento-help-center-user-guide.md#support-tickets) in unserer Wissensdatenbank.

   >[!NOTE]
   >
   >Geben Sie nie direkt im Ticket Kennwörter oder gültige/aktive API-Token frei, da wir das aktuelle Token aus Sicherheitsgründen widerrufen und ein neues generieren müssen.

1. Wenn der Befehl den Fehler nicht zurückgibt, stellen Sie sicher, dass Sie die neueste Version der [!DNL Fastly] -Erweiterung. Wenn Sie eine ältere Version vor dem 1.2.203 verwenden, müssen Sie zuerst auf **[!UICONTROL Save Config]** bevor Sie die Anmeldeinformationen testen können.

## Weitere Informationen finden Sie in unserer Entwicklerdokumentation:

* [Cloud für Adobe Commerce > Schnell > Fastly-Service-Konto und -Anmeldedaten](https://devdocs.magento.com/cloud/cdn/cloud-fastly.html#fastly-service-account-and-credentials)

* [Cloud für Adobe Commerce > Schnelles Einrichten > Testen der Fastly-Anmeldedaten](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#test-the-fastly-credentials)
