---
title: Fehler bei der Validierung der  [!DNL Fastly] -Anmeldeinformationen
description: Dieser Artikel bietet eine Lösung für das Problem, dass ein Benutzer beim Überprüfen der Anmeldeinformationen einen Fehler  [!DNL Fastly] .
exl-id: 02104731-6666-47a6-abc6-215812f09915
feature: Configuration
role: Developer
source-git-commit: 838f0c5d55c29d026dc37a8f7e5214b9880a4353
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# Fehler bei der Validierung der [!DNL Fastly] Anmeldedaten

In diesem Artikel wird erläutert, wie Sie Fehler *Token abgelaufen* beheben können, die beim Überprüfen [!DNL Fastly] Anmeldeinformationen aufgetreten sind.

Die in diesem Artikel beschriebenen Schritte gelten auch, wenn Sie Ihr [!DNL Fastly]-API-Token aus Sicherheitsgründen rotieren (zyklieren) müssen. In diesen Fällen sollten Sie ein Adobe Commerce-Support-Ticket einreichen, um ein neues [!DNL Fastly]-API-Token anzufordern.

## Problem

* Bei der Validierung der [!DNL Fastly]-Anmeldeinformationen wird ein Fehler angezeigt.
* Sie vermuten, dass Ihr [!DNL Fastly]-Token möglicherweise beschädigt wurde, z. B. wenn es versehentlich in einem Support-Ticket geteilt oder in einem öffentlichen Forum veröffentlicht wurde.

## Betroffene Produkte und Versionen

* Adobe Commerce (alle Bereitstellungsmethoden): Alle Versionen
* Erweiterungs- oder Technologieversion ([!DNL Fastly], [!DNL New Relic] usw.) [!DNL Fastly]

## Lösung

1. Vergewissern Sie sich, dass Sie die richtige [!DNL Fastly]-Service-ID und das richtige API-Token haben, und versuchen Sie es erneut. Detaillierte Anweisungen finden Sie unter [Testen der  [!DNL Fastly] Anmeldeinformationen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration?lang=en#test-the-fastly-credentials) in unserer Entwicklerdokumentation.
1. Wenn die Überprüfung der Anmeldeinformationen fehlschlägt, führen Sie den folgenden curl-Befehl aus, um den Status des Services zu bestätigen:

   ```curl
   curl -H "Fastly-Key: <API key>" https://api.fastly.com/service/<service ID>/version/active
   ```

1. Wenn der obige Befehl einen Fehler wie den folgenden zurückgibt: `{"msg":"Token $TOKEN expired at 2021-09-28T02:03:37Z"}`, senden Sie ein Support-Ticket, um ein neues API-Token anzufordern. Nachdem Sie Ihr neues Token erhalten haben, aktualisieren Sie die Konfiguration in Ihrer Umgebung.

   Informationen zum Einreichen eines Support-Tickets finden Sie im [Benutzerhandbuch für das Adobe Commerce Help Center > SUPPORT-TICKETS](/help/help-center-guide/help-center/magento-help-center-user-guide.md#support-tickets) in unserer Support-Wissensdatenbank.

   >[!NOTE]
   >
   >Geben Sie niemals Passwörter oder gültige/aktive API-Token direkt im Ticket frei, da wir das aktuelle Token widerrufen und aus Sicherheitsgründen ein neues generieren müssen.
   >
   >Der Adobe Commerce-Support hat Zugriff auf die Token. Daher sollten Sie diese Informationen nicht in das Ticket aufnehmen müssen.

1. Wenn der Befehl den Fehler nicht zurückgibt, stellen Sie sicher, dass Sie die neueste Version der [!DNL Fastly]-Erweiterung ausführen. Wenn Sie eine ältere Version vor 1.2.203 verwenden, müssen Sie zunächst auf **[!UICONTROL Save Config]** klicken, bevor Sie die Anmeldeinformationen testen können.

## Weitere Informationen finden Sie in unserer Entwicklerdokumentation:

* [Cloud für Adobe Commerce > [!DNL Fastly] > [!DNL Fastly] Service-Konto und Anmeldedaten](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly?lang=en#fastly-service-account-and-credentials)

* [Cloud für Adobe Commerce > Einrichten [!DNL Fastly] > Testen der  [!DNL Fastly] Anmeldeinformationen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration?lang=en#test-the-fastly-credentials)
