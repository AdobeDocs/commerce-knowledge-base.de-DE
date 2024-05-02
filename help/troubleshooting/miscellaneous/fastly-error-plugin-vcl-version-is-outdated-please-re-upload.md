---
title: 'Fastly Error: Plugin VCL Version ist veraltet! Bitte erneut hochladen'
description: Dieser Artikel bietet eine Lösung für den Fall, dass die Meldung "*Plugin VCL Version ist veraltet! Bitte neu hochladen.*" in der Fastly-Konfiguration in der Commerce-Admin, da das neueste Fastly-Modul nicht installiert wurde.
exl-id: d7870e9e-ba6b-49c2-a80c-26fb464cbae3
feature: Best Practices, Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# Fastly Error: Plugin VCL Version ist veraltet! Bitte erneut hochladen

Dieser Artikel bietet eine Lösung für den Fall, dass die Meldung &quot;*Plugin VCL Version ist veraltet! Bitte neu hochladen.*&quot;in der Fastly-Konfiguration in Commerce Admin, da das neueste Fastly-Modul nicht installiert wurde.

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur 2.2.x, 2.3.x<br>
Schnell: Dieser Fehler kann sich auf alle Versionen des Fastly-Moduls mit Ausnahme der neuesten Version auswirken. Informationen zur neuesten Version finden Sie unter [Schnelle Versionshinweise](https://github.com/fastly/fastly-magento2/releases) auf GitHub.

## Problem

1. Melden Sie sich beim Commerce Admin-Bedienfeld an.
1. Navigieren Sie zu **Stores** > **Konfiguration** > **Erweitert** > **System** > **Vollständiger Seiten-Cache**   **Schneller Cache.**
1. Im **Automatische Upload- und Dienstaktivierung** gibt es einen *Plugin VCL Version ist veraltet! Bitte neu hochladen.*&quot;Benachrichtigung.
1. Sie versuchen, die VCL-Snippets hochzuladen, indem Sie auf die Schaltfläche &quot;VCL auf Fastly hochladen&quot;klicken, aber dennoch wird die Warnung angezeigt *Plugin VCL Version ist veraltet! Bitte neu hochladen.*&quot;

## Ursache

Die Fastly-Erweiterung wurde aktualisiert (zusammen mit einer gebündelten VCL-Konfiguration und Vorlagen), aber die aktualisierte VCL-Konfiguration wurde nicht in den Fastly-Dienst hochgeladen. Beim Aktualisieren des Adobe Commerce-Moduls `Fastly_Cdn`, müssen Sie eine aktualisierte VCL-Konfiguration erneut auf Fastly hochladen.

## Lösung

1. Vergewissern Sie sich, dass die neuesten ECE-Tools installiert sind, und klicken Sie auf [aktuelle Version](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html) in unserer Entwicklerdokumentation. ECE-Tools verfügt über eine Version des Fastly-Pakets in seinen Abhängigkeiten.

   Dies ist möglicherweise nicht die neueste Version des Fastly-Plug-ins. Es handelt sich jedoch wahrscheinlich um eine spätere Version als die, die Sie derzeit installiert haben. Es empfiehlt sich, die neuesten ECE-Tools zu installieren.

1. Wenn Sie nicht mit der aktuellen Version der ECE-Tools arbeiten, führen Sie die folgenden Schritte aus, um [Upgrade](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html) in unserer Entwicklerdokumentation.
1. Nachdem Sie die ECE-Tools aktualisiert haben, überprüfen Sie, ob Sie jetzt über eine aktuelle Version der [Fastly-Plug-in](https://github.com/fastly/fastly-magento2/tree/master/etc/vcl_snippets) installiert.
1. Wenn das Fastly-Plug-in nicht die aktuelle Version ist, führen Sie die folgenden Schritte aus, um [Aktualisieren des Plug-ins auf die neueste Version](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#upgrade-the-fastly-module) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

* Informationen zum Einrichten und Konfigurieren von Fastly finden Sie unter [Fastly Services konfigurieren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html) in unserer Entwicklerdokumentation.
* Allgemeine Informationen zu Fastly finden Sie unter [fastly.com](https://www.fastly.com/).
