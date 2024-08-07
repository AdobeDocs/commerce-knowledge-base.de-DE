---
title: Zurücksetzen von Adobe Commerce in Cloud-Infrastruktur-Cron-Aufträgen manuell zurücksetzen
description: Adobe Commerce auf Cloud-Infrastruktur-Cron-Aufträgen wird nicht ausgeführt, bleibt hängen und verhindert, dass andere Cron-Aufträge ausgeführt werden. In diesem Artikel wird gezeigt, wie die hängenden Cron-Aufträge manuell zurückgesetzt werden.
exl-id: aec6de8e-c3a9-4a6d-8ecd-a213e77c97a1
feature: Cloud
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---

# Zurücksetzen von Adobe Commerce in Cloud-Infrastruktur-Cron-Aufträgen manuell zurücksetzen

Adobe Commerce auf Cloud-Infrastruktur-Cron-Aufträgen wird nicht ausgeführt, bleibt hängen und verhindert, dass andere Cron-Aufträge ausgeführt werden. In diesem Artikel wird gezeigt, wie die hängenden Cron-Aufträge manuell zurückgesetzt werden.

Verwenden Sie diesen Befehl mit Vorsicht! Wir empfehlen, den Artikel [Cron-Aufträge zurücksetzen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html) in unserer Support-Wissensdatenbank zu lesen, um mehr zu erfahren.

## Schritte

>[!INFO]
>
>Ab [ECE-Tools v2002.0.4](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-release-archive.html#v2002.0.4) können Sie hängengebliebene Cron-Aufträge mithilfe eines CLI-Befehls über SSH-Zugriff manuell zurücksetzen.

1. [SSH in Ihre Umgebung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Führen Sie diesen Befehl aus: `./vendor/bin/ece-tools cron:unlock`

## Warnungen

* Der Befehl setzt **alle** Cron-Aufträge zurück, einschließlich der derzeit ausgeführten; **verwendet sie nur in Ausnahmefällen**.
* Vermeiden Sie die Verwendung dieser Lösung, wenn Indexer ausgeführt werden.

## Lesen Sie es in unserer Support-Wissensdatenbank:

[cron-Aufträge zurücksetzen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html)
