---
title: 403-Fehler beim Zugriff auf das Site-Wide Analysis Tool in Adobe Commerce
description: Dieser Artikel bietet eine Lösung für den Fall, dass beim Versuch, auf das Site-Wide Analysis Tool in Adobe Commerce zuzugreifen, 403-Fehler auftreten.
exl-id: f24fad17-62d6-4a0f-bcba-983c3dbee3d7
feature: Observability
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# 403-Fehler beim Zugriff auf das Site-Wide Analysis Tool in Adobe Commerce

Dieser Artikel bietet eine Lösung für den Fall, dass beim Versuch, auf das Site-Wide Analysis Tool in Adobe Commerce zuzugreifen, 403-Fehler auftreten.

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur 2.4.1 und höher.

## Problem

Beim Versuch, auf das Site-Wide Analysis Tool zuzugreifen, wird eine 403-Fehlermeldung angezeigt.

<u>Schritte zur Reproduktion:</u>

Melden Sie sich beim Commerce Admin-Panel an und klicken Sie auf **Berichte** > *Systemeinblicke* > **Site-Wide Analysis Tool**.

<u>Erwartetes Ergebnis:</u>

Sie sehen das Site-Wide Analysis Tool.

<u>Tatsächliches Ergebnis:</u>

Sie sehen: *Fehler 403.*


## Lösung

Um sicherzustellen, dass das Site-Wide Analysis Tool über den richtigen Zugriff auf Ihre Anwendung verfügt, führen Sie den folgenden Befehl in der CLI aus. Ersetzen Sie `<store URL>` durch Ihre Store-URL:

```cURL
curl -sIL -X GET <store URL>/swat/key/index | grep HTTP
HTTP/2 403
```

Führen Sie Schritte abhängig vom Antwort-Code aus, den Sie erhalten.

### 403 Verbotener Antwort-Code

Wenn der Antwort-Code 403 lautet, verfügen Sie möglicherweise über einen Cloudflare-Bot-Schutz, der das Site-Wide Analysis Tool blockiert. Um auf das Tool zuzugreifen, erstellen Sie eine Whitelist der IPs:

* 107.23.33.174
* 3.225.9.244
* 3.88.83.85

### Korrigieren des 200-Antwort-Codes und der JSON-Ausgabe

Wenn die Antwort die richtige 200-Code- und JSON-Ausgabe ist, [ Sie ein Support-Ticket ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), um das Problem mit dem Zugriff auf das Site-Wide Analysis Tool zu eskalieren.


### 500-Antwort-Code (Schwerwiegender Fehler)

Wenn der Antwort-Code 500 (Schwerwiegender Fehler) lautet, installieren Sie bitte den MDVA-38526-Patch. Verwenden Sie einen der folgenden Links, um den Patch herunterzuladen, je nach dem gewünschten Patch-Typ:

* Patch für Adobe Commerce auf Cloud-Infrastruktur: [MDVA-38526_EE_2.4.1-p1_v3.patch.zip](assets/MDVA-38526_EE_2.4.1-p1_v3.patch.zip)
* Patch für Adobe Commerce on Cloud Infrastructure Composer: [MDVA-38526_EE_2.4.1-p1_COMPOSER_v3.patch.zip](assets/MDVA-38526_EE_2.4.1-p1_COMPOSER_v3.patch.zip)

Der Patch gilt für Adobe Commerce in Cloud-Infrastrukturversionen 2.4.1 und höher.

### Antwort nicht JSON

Wenn die Antwortausgabe nicht JSON ist, kann dies auf eine PWA/Headless-Implementierung zurückzuführen sein. Wenn Sie die Headless-Implementierung verwenden, aktualisieren Sie die UPWARD-Konfiguration, um Anfragen an Adobe Commerce Origin zu umgehen. Fügen Sie dazu im Adobe Commerce Admin unter **Stores** > **Configuration** > **General** > **Web** > **UPWARD PWA Auf die Zulassungsliste setzen Configuration** > **Front Name** Folgendes *swat*.

![UPWARD_CONFIGURATION](assets/upward_pwa.png)

Wenn Sie immer noch nicht auf das Site-Wide Analysis Tool zugreifen können, wenn Sie sich das nächste Mal beim Commerce Admin-Panel anmelden und zu **Berichte** > *Systemeinblicke* > **Site-Wide Analysis Tool** navigieren [ ein Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

## Verwandtes Lesen

* [Handbuch zum Site-Wide Analysis Tool](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/intro.html)
