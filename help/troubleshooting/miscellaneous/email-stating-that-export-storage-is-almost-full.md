---
title: E-Mail, die besagt, dass der Exportspeicher fast voll ist
description: Dieser Artikel bietet eine Lösung für das Problem, bei dem Sie eine E-Mail erhalten, in der angegeben wird, dass der Exportspeicher fast voll ist.
feature: Cloud, Storage, Media
role: Developer
exl-id: 7dae295c-919c-46c5-bf63-7d3467c2e07f
source-git-commit: 11cf981c7ebe813219a0cd311632eafce086bbf6
workflow-type: tm+mt
source-wordcount: '427'
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

Der Warnhinweis bezieht sich auf das Dateisystem für Exporte, das das Festplatten-Volume ist, auf dem Medien und andere Dateidaten gespeichert werden. Dieses Dateisystem wird normalerweise unter `/data/exports` gemountet. Der Warnhinweis zeigt nicht an, dass ein einzelnes Verzeichnis mit dem buchstäblichen Namen „exports“ vorhanden ist.

Um zu bestätigen, worauf sich der Warnhinweis bezieht, überprüfen Sie die Speicherverwendung des Exports:

* Führen Sie `df -h | grep exports` aus. Daraufhin wird die folgende Beispielausgabe angezeigt:

  ```
  /dev/nvme1n1 50G 38G 12G 77% /data/exports
  tmpfs         7.7G 4.0K 7.7G  1% /data/exports/shared
  ```

* In diesem Beispiel ist `/data/exports` das Hauptexportdateisystem:

   * 50 GB insgesamt
   * Verwendete 38 GB
   * 12 GB verfügbar (77 % Auslastung)

* `/data/exports/shared` ist eine `tmpfs` (speicherinterne) Halterung, die für gemeinsam genutzte Daten verwendet wird und nicht wesentlich zum Festplattendruck beiträgt.

Dadurch wird bestätigt, dass der Warnhinweis durch die allgemeine Festplattenauslastung von `/data/exports` ausgelöst wird, und nicht durch einen einzelnen Ordner mit dem Namen „exports“.

Wenn `/data/exports` hohe Auslastung aufweist, sind große Verzeichnisse unter diesem Dateisystem - wie z. B. Pub/Media oder andere benutzerdefinierte Dateispeicherorte - in der Regel für die erhöhte Nutzung verantwortlich.

## Lösung

Führen Sie diese Schritte aus, um die Nutzung des Exportspeichers zu überprüfen, zu bereinigen und zu validieren.

1. Führen Sie den Befehl `df -h | grep exports` aus, um die aktuelle Verwendung des Exportspeicherdateisystems zu überprüfen. Überprüfen Sie die Spalte **Verwenden** für `/data/exports`:

   * Wenn die Nutzung zwischen 70 und 85 % liegt, beginnen Sie mit der Planung der Bereinigung.
   * Wenn die Nutzung mehr als 90 % beträgt, ergreifen Sie sofort Maßnahmen, um Schreibfehler oder Auswirkungen auf den Service zu vermeiden.

1. Ermitteln Sie Verzeichnisse, die unter `/data/exports` erheblichen Speicherplatz belegen, indem Sie Folgendes ausführen:

   ```bash
   du -sh /data/exports/* 2>/dev/null
   ```

   Die typischen Speicherorte, an denen der Dateispeicher wahrscheinlich gefüllt wird, sind `pub/media/catalog/product/cache` oder `var/log`.

1. Bereinigen von Dateien basierend auf der Umgebung:

   * Entfernen Sie zuerst alte oder nicht verwendete Exportdateien, Protokolle oder temporäre Daten.
   * In Nicht-Produktionsumgebungen können Sie Testmedien oder alte Artefakte in der Regel aggressiver entfernen.
   * Koordinieren Sie sich in Produktionsumgebungen mit Ihrem Team, bevor Sie Medien oder geschäftskritische Dateien löschen.

1. Führen Sie nach der Bereinigung den folgenden `df -h | grep exports` aus, um zu bestätigen, dass der Wert **Verwenden%** für `/data/exports` auf eine sichere Betriebsebene abgesunken ist.

## Verwandtes Lesen

[Überprüfen Sie ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#check-dedicated-clusters) dedizierten Clustern in unserer Support-Wissensdatenbank.
