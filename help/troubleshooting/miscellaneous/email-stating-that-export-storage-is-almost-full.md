---
title: E-Mail, die besagt, dass der Exportspeicher fast voll ist
description: Dieser Artikel bietet eine Lösung für das Problem, bei dem Sie eine E-Mail erhalten, in der angegeben wird, dass der Exportspeicher fast voll ist.
feature: Cloud, Storage, Media
role: Developer
exl-id: 7dae295c-919c-46c5-bf63-7d3467c2e07f
source-git-commit: 89f985b832545f1fbccf94aac1d60f1e767b5bc4
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# E-Mail, die besagt, dass der Exportspeicher fast voll ist

Dieser Artikel bietet eine Lösung für das Problem, bei dem Sie eine E-Mail erhalten, in der angegeben wird, dass der Exportspeicher fast voll ist.

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur (alle Versionen)

## Problem

Sie erhalten eine E-Mail mit folgendem Inhalt, können jedoch den Ordner *Exporte* nicht finden:

*Unsere Überwachung hat ergeben, dass der „Export“-Speicher auf Ihrem Cluster XXX zu etwa „85 %&quot; voll ist.*
*Überprüfen Sie bei Bedarf die Nutzung, führen Sie eine Bereinigung durch oder fordern Sie eine Vergrößerung an.*
*Beachten Sie außerdem, dass wir automatisch versuchen werden, die Größe zu erhöhen, wenn der Speicher den kritischen Schwellenwert erreicht.*

## Ursache

Die E-Mail bezieht sich auf den **Exporte**-Speicher, d. h. die den Dateien/Medien zugeordnete Festplattenmenge, und nicht auf einen bestimmten Ordner mit dem Namen *Exporte*.

## Lösung

Sie sollten die Datennutzung in der Umgebung überprüfen. Führen Sie diesen Befehl aus, um die vorhandene Verwendung abzurufen:

`df -h |grep data`

Die typischen Speicherorte, an denen der Dateispeicher wahrscheinlich gefüllt wird, sind die Ordner *pub/media/catalog/product/cache* oder *var/log*. Um den von den Dateien verwendeten Speicherplatz zu ermitteln, führen Sie diesen Befehl mit dem entsprechenden Pfad */path/to/folder aus*:

`du -shc` */path/to/folder*

Wenn die Nutzung der Medien einen großen Teil des gesamten Festplattenspeichers ausmacht, sollten Sie [Fastly Deep Image Optimization](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization#deep-image-optimization) aktivieren und dann die Dateien im Ordner *pub/media/catalog/product/cache* auf dem Server manuell löschen.

## Verwandtes Lesen

[Überprüfen Sie ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#check-dedicated-clusters) dedizierten Clustern in unserer Support-Wissensdatenbank.
