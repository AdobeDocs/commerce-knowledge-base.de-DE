---
title: 'Fastly-Fehler: Plug-in VCL-Version ist veraltet! Bitte erneut hochladen'
description: Dieser Artikel bietet eine Lösung für, wenn Sie die Nachricht sehen "*Plug-in VCL-Version ist veraltet! Bitte erneut hochladen.*" in der Fastly-Konfiguration in der Commerce Admin, da das neueste Fastly-Modul nicht installiert ist.
exl-id: d7870e9e-ba6b-49c2-a80c-26fb464cbae3
feature: Best Practices, Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# Fastly-Fehler: Plug-in VCL-Version ist veraltet! Bitte erneut hochladen

Dieser Artikel bietet eine Lösung für, wenn Sie die Nachricht &quot;*Plugin VCL Version ist veraltet! Bitte erneut hochladen.*&quot; in der Fastly-Konfiguration in Commerce Admin, da das neueste Fastly-Modul nicht installiert wurde.

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur 2.2.x, 2.3.x<br>
Fastly: Dieser Fehler kann alle Versionen des Fastly-Moduls betreffen, mit Ausnahme der neuesten. Informationen zur neuesten Version finden Sie unter [Versionshinweise zu Fastly](https://github.com/fastly/fastly-magento2/releases) auf GitHub.

## Problem

1. Melden Sie sich beim Commerce Admin Panel an.
1. Navigieren Sie zu **Stores** > **Konfiguration** > **Erweitert** > **System** > **Vollständiger Seitencache**   **Fastly.**
1. Im Abschnitt **Automatische Upload- und Service** Aktivierung gibt es eine &quot;*Plug-in VCL-Version ist veraltet! Bitte erneut hochladen.*&quot; Benachrichtigung.
1. Sie versuchen, die VCL-Snippets hochzuladen, indem Sie auf die Schaltfläche „Upload VCL to Fastly“ klicken, aber Sie sehen immer noch die Warnung &quot;*Plugin VCL-Version ist veraltet! Bitte erneut hochladen.*&quot;

## Ursache

Die Fastly-Erweiterung wurde aktualisiert (zusammen mit einer gebündelten VCL-Konfiguration und Vorlagen), aber die aktualisierte VCL-Konfiguration wurde nicht in den Fastly-Service hochgeladen. Wenn Sie das Adobe Commerce-Modul `Fastly_Cdn` aktualisieren, müssen Sie erneut eine aktualisierte VCL-Konfiguration auf Fastly hochladen.

## Lösung

1. Vergewissern Sie sich, dass Sie die neuesten ECE-Tools in der [ Version ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html) Entwicklerdokumentation installiert haben. ECE-Tools hat eine Version des Fastly-Pakets in seinen Abhängigkeiten.

   Dies mag nicht die neueste Version des Fastly-Plugins sein, aber es ist wahrscheinlich eine spätere Version als die, die Sie gerade installiert haben, und es ist Best Practice, die neuesten ECE-Tools zu installieren.

1. Wenn Sie die aktuelle Version von ECE-Tools nicht verwenden, führen Sie diese Schritte zum [Upgrade](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html) in unserer Entwicklerdokumentation aus.
1. Überprüfen Sie nach dem Upgrade von ECE-Tools, ob Sie jetzt eine aktuelle Version des [Fastly-Plugins](https://github.com/fastly/fastly-magento2/tree/master/etc/vcl_snippets) installiert haben.
1. Wenn das Fastly-Plug-in nicht die aktuelle Version ist, führen Sie diese Schritte aus, um [das Plug-in auf die neueste Version zu aktualisieren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#upgrade-the-fastly-module) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

* Informationen zum Einrichten und Konfigurieren von Fastly finden Sie unter [Fastly-Services konfigurieren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html) in unserer Entwicklerdokumentation.
* Allgemeine Informationen zu Fastly finden Sie unter [fastly.com](https://www.fastly.com/).
