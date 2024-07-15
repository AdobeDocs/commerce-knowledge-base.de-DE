---
title: 403 Fehler beim Zugriff auf das Site-weite Analyse-Tool in Adobe Commerce
description: Dieser Artikel bietet eine Lösung für Fälle, in denen Sie 403-Fehler erhalten, wenn Sie versuchen, auf das Site-weite Analyse-Tool in Adobe Commerce zuzugreifen.
exl-id: f24fad17-62d6-4a0f-bcba-983c3dbee3d7
feature: Observability
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# 403 Fehler beim Zugriff auf das Site-weite Analyse-Tool in Adobe Commerce

Dieser Artikel bietet eine Lösung für Fälle, in denen Sie 403-Fehler erhalten, wenn Sie versuchen, auf das Site-weite Analyse-Tool in Adobe Commerce zuzugreifen.

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur 2.4.1 und höher.

## Problem

Beim Zugriff auf das Site-weite Analyse-Tool erhalten Sie einen 403-Fehler.

<u>Zu reproduzierende Schritte:</u>

Melden Sie sich beim Commerce Admin-Bedienfeld an und klicken Sie auf &quot;**Berichte**&quot;> &quot;*Systemeinblicke*&quot;> &quot;**Site-weites Analyse-Tool**&quot;.

<u>Erwartetes Ergebnis:</u>

Sie sehen das Site-weite Analyse-Tool.

<u>Tatsächliches Ergebnis:</u>

Sie sehen: *Fehler 403.*


## Lösung

Um sicherzustellen, dass das Site-weite Analyse-Tool den richtigen Zugriff auf Ihre Anwendung hat, führen Sie den folgenden Befehl in der CLI aus. Ersetzen Sie `<store URL>` durch Ihre Store-URL:

```cURL
curl -sIL -X GET <store URL>/swat/key/index | grep HTTP
HTTP/2 403
```

Führen Sie Schritte entsprechend dem Antwortcode durch, den Sie erhalten.

### 403 Verbotener Antwort-Code

Wenn der Antwortcode 403 ist, verfügen Sie möglicherweise über Cloudflare-Bot-Schutz, der das Site-weite Analyse-Tool blockiert. Um auf das Tool zuzugreifen, müssen die IP-Adressen auf die Whitelist gesetzt werden:

* 107 23 33 174
* 3 225 9 244
* 3 88 83 85

### 200-Antwort-Code und JSON-Ausgabe korrigieren

Wenn die Antwort der richtige 200-Code- und JSON-Ausgabe ist, senden [ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), um das Problem mit dem Site-weiten Analyse-Tool-Zugriff zu eskalieren.


### Antwortcode 500 (Schwerwiegender Fehler)

Wenn der Antwortcode 500 (Todesfehler) beträgt, installieren Sie bitte den Patch MDVA-38526. Verwenden Sie je nach gewünschtem Patch einen der folgenden Links, um den Patch herunterzuladen:

* Adobe Commerce auf dem Cloud-Infrastruktur-Patch: [MDVA-38526_EE_2.4.1-p1_v3.patch.zip](assets/MDVA-38526_EE_2.4.1-p1_v3.patch.zip)
* Adobe Commerce on cloud Infrastructure Composer patch: [MDVA-38526_EE_2.4.1-p1_COMPOSER_v3.patch.zip](assets/MDVA-38526_EE_2.4.1-p1_COMPOSER_v3.patch.zip)

Der Patch gilt für Adobe Commerce in den Cloud-Infrastrukturversionen 2.4.1 und höher.

### Antwort nicht JSON

Wenn die Antwortausgabe nicht JSON ist, kann dies an der Implementierung von PWA/Headless liegen. Wenn Sie die Headless-Implementierung verwenden, aktualisieren Sie die UPWARD-Konfiguration, um Anforderungen an Adobe Commerce Origin zu umgehen. Fügen Sie dazu im Adobe Commerce-Admin unter **Stores** > **Konfiguration** > **Allgemein** > **Web** > **UPWARD-PWA-Konfiguration** > **Vorname** den Wert *swat* hinzu.

![Upward_configuration](assets/upward_pwa.png)

Wenn Sie immer noch nicht auf das Site-weite Analyse-Tool zugreifen können, senden Sie ein Support-Ticket ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), wenn Sie sich das nächste Mal beim Commerce Admin-Bedienfeld anmelden und zu **Berichte** > *Systemeinblicke* > **Site-Wweiter Analyse-Tool** navigieren.[

## Verwandtes Lesen

* [Handbuch für das Site-weite Analyse-Tool](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/intro.html)
