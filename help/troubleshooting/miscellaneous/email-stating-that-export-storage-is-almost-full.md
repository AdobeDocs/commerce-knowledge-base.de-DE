---
title: E-Mail mit der Meldung, dass der Exportspeicher fast vollständig ist
description: Dieser Artikel bietet eine Lösung für das Problem, dass Sie eine E-Mail erhalten, in der Sie darauf hingewiesen werden, dass der Exportspeicher fast voll ist.
feature: Cloud, Storage, Media
role: Developer
exl-id: 7dae295c-919c-46c5-bf63-7d3467c2e07f
source-git-commit: 89f985b832545f1fbccf94aac1d60f1e767b5bc4
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# E-Mail mit der Meldung, dass der Exportspeicher fast vollständig ist

Dieser Artikel bietet eine Lösung für das Problem, dass Sie eine E-Mail erhalten, in der Sie darauf hingewiesen werden, dass der Exportspeicher fast voll ist.

## Betroffene Produkte und Versionen

Adobe Commerce in der Cloud-Infrastruktur (alle Versionen)

## Problem

Sie erhalten eine E-Mail mit folgendem Inhalt, können jedoch den Ordner *export* nicht finden:

*Unser Monitoring hat festgestellt, dass der &quot;Export&quot;-Speicher in Ihrem Cluster XXX ungefähr &#39;85 %&#39; voll ist.*
*Überprüfen Sie bei Bedarf die Verwendung, führen Sie eine Bereinigung durch oder fordern Sie eine Aktualisierung an.*
*Beachten Sie außerdem, dass wir automatisch eine Vergrößerung versuchen, wenn der Speicher den kritischen Schwellenwert erreicht.*

## Ursache

Die E-Mail bezieht sich auf den Speicher **export**, der der den Dateien/Medien zugewiesenen Menge an Speicherplatz entspricht, und nicht auf einen bestimmten Ordner mit dem Namen *exports*.

## Lösung

Sie sollten die Verwendung der Dateien in der Umgebung überprüfen. Führen Sie diesen Befehl aus, um die vorhandene Verwendung abzurufen:

`df -h |grep data`

Die typischen Speicherorte, an denen der Dateispeicher wahrscheinlich gefüllt wird, sind die Ordner *pub/media/catalog/product/cache* oder *var/log* . Um den von den Dateien verwendeten Speicherplatz zu bestimmen, führen Sie diesen Befehl mit dem entsprechenden Pfad */path/to/folder* aus:

`du -shc` */path/to/folder*

Wenn die Nutzung der Mediendatei einen großen Teil des gesamten Festplattenspeichers ausmacht, sollten Sie erwägen, die Option [Fastly Deep Image Optimization](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization#deep-image-optimization) zu aktivieren und dann die Dateien im Ordner *pub/media/catalog/product/cache* auf dem Server manuell zu löschen.

## Verwandte Informationen

[Überprüfen Sie dedizierte Cluster](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#check-dedicated-clusters) in unserer Support-Wissensdatenbank.
