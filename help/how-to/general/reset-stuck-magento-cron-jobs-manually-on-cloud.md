---
title: Setzt fixierte Adobe Commerce in der Cloud-Infrastruktur bei Cron-Aufträgen manuell zurück
description: Adobe Commerce in der Cloud-Infrastruktur Cron-Aufträge werden nicht fertig ausgeführt, bleiben hängen und verhindern die Ausführung anderer Cron-Aufträge. Dieser Artikel zeigt, wie Sie die blockierten Cron-Aufträge manuell zurücksetzen können.
exl-id: aec6de8e-c3a9-4a6d-8ecd-a213e77c97a1
feature: Cloud
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---

# Setzt fixierte Adobe Commerce in der Cloud-Infrastruktur bei Cron-Aufträgen manuell zurück

Adobe Commerce in der Cloud-Infrastruktur Cron-Aufträge werden nicht fertig ausgeführt, bleiben hängen und verhindern die Ausführung anderer Cron-Aufträge. Dieser Artikel zeigt, wie Sie die blockierten Cron-Aufträge manuell zurücksetzen können.

Verwenden Sie diesen Befehl mit Vorsicht! Wir empfehlen, den Artikel [Reset cron jobs](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html) in unserer Support-Wissensdatenbank zu lesen, um mehr zu erfahren.

## Schritte

>[!INFO]
>
>Ab [ECE-Tools v2002.0.4](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-release-archive.html#v2002.0.4) können Sie hängengebliebene Cron-Aufträge manuell über einen CLI-Befehl per SSH-Zugriff zurücksetzen.

1. [SSH in Ihre Umgebung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Führen Sie diesen Befehl aus: `./vendor/bin/ece-tools cron:unlock`

## Warnungen

* Der Befehl setzt **alle** Cron-Aufträge zurück, einschließlich der derzeit ausgeführten; **verwenden Sie ihn nur in Ausnahmefällen**.
* Vermeiden Sie diese Lösung, wenn Indexer ausgeführt werden.

## Lesen Sie es in unserer Support-Wissensdatenbank:

[Cron-Aufträge zurücksetzen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html)
