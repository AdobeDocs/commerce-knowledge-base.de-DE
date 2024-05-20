---
title: "E-Mail mit Angabe, dass der Exportspeicher fast voll ist"
description: Dieser Artikel bietet eine Lösung für das Problem, dass Sie eine E-Mail erhalten, in der Sie darauf hingewiesen werden, dass der Exportspeicher fast voll ist.
feature: Cloud, Storage, Media
role: Developer
source-git-commit: 8f783cb4245911bded5e9946917e2f2c3e78a705
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# E-Mail mit der Meldung, dass der Exportspeicher fast vollständig ist

Dieser Artikel bietet eine Lösung für das Problem, dass Sie eine E-Mail erhalten, in der Sie darauf hingewiesen werden, dass der Exportspeicher fast voll ist.

## Betroffene Produkte und Versionen

Adobe Commerce in der Cloud-Infrastruktur (alle Versionen)

## Problem

Sie erhalten eine E-Mail mit folgendem Inhalt, können jedoch die *Exporte* Ordner:

*Unser Monitoring hat festgestellt, dass der &quot;Export&quot;-Speicher in Ihrem Cluster XXX etwa &#39;85%&#39; voll ist.*
*Überprüfen Sie bei Bedarf die Verwendung, führen Sie eine Bereinigung durch oder fordern Sie eine Aktualisierung an.*
*Beachten Sie außerdem, dass wir automatisch eine Vergrößerung versuchen, wenn der Speicher den kritischen Schwellenwert erreicht.*

## Ursache

Die E-Mail bezieht sich auf die **Exporte** storage, d. h. die Menge an Speicherplatz, die den Dateien/Medien zugeordnet ist, und nicht ein bestimmter Ordner mit dem Namen *Exporte*.

## Lösung

Sie sollten die Verwendung der Dateien in der Umgebung überprüfen. Führen Sie diesen Befehl aus, um die vorhandene Verwendung abzurufen:

`df -h |grep data`

Die typischen Speicherorte, an denen die Dateispeicherung wahrscheinlich gefüllt wird, sind die *pub/media/catalog/product/cache* oder *var/log* Ordner. Um den von den Dateien verwendeten Speicherplatz zu bestimmen, führen Sie diesen Befehl mit dem entsprechenden Pfad aus */path/to/folder*:

`du -shc` */path/to/folder*

Wenn die Nutzung des Mediums einen großen Teil des gesamten Festplattenspeichers ausmacht, sollten Sie die Aktivierung von [Fastly Deep Image Optimization](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization#deep-image-optimization)und löschen Sie dann die Dateien im *pub/media/catalog/product/cache* -Ordner manuell auf dem Server.

## Verwandte Informationen

[Überprüfen dedizierter Cluster](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#check-dedicated-clusters) in unserer Wissensdatenbank.