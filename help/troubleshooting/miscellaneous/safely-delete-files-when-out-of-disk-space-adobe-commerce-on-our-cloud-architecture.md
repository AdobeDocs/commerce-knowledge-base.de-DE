---
title: Sicheres Löschen von Dateien, wenn in Adobe Commerce in der Cloud-Infrastruktur nicht genügend Speicherplatz vorhanden ist
description: Dieser Artikel bietet eine Lösung für den Fall, dass Ihnen der Speicherplatz ausgeht und Sie Dateien sicher entfernen müssen. Bevor Sie diese Aktion in Erwägung ziehen, lesen Sie [Verwalten von Speicherplatz](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#no-space-left) in unserer Entwicklerdokumentation. Wenn die Schritte in diesem Artikel für Sie nicht geeignet sind oder das Problem nicht lösen, überprüfen Sie die Schritte in diesem Artikel.
exl-id: 6b0a5c1a-8db4-49d7-a785-b4e0bbaea0df
feature: Cloud, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# Sicheres Löschen von Dateien, wenn in Adobe Commerce in der Cloud-Infrastruktur nicht genügend Speicherplatz vorhanden ist

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.4.2 - 2.4.7
* Dies gilt speziell für dedizierte Pro-Cluster. Starter- und Integrationsumgebungen sind nur ein Knoten und haben nicht den Ordner &quot;`/data/exports`&quot;.

## Anzeichen für geringen Festplattenspeicher

Wenn Ihnen der Speicherplatz ausgeht, kann die Bereitstellung blockiert, die vollständige Warnungen auf der Festplatte und die schlechte Leistung beeinträchtigt werden.
Führen Sie den folgenden Befehl in der CLI/Terminal aus, um den vom Dateisystem verwendeten Speicherplatz anzuzeigen:

`df -h`


## Sicheres Löschen von Dateien zur Erhöhung des Festplattenspeicherplatzes

Sie können Dateien aus den Bereitstellungspunkten der Anwendung löschen, aus Ihrem `/app` Pfad oder über `/mnt/shared`. Es gibt zwei verschiedene Möglichkeiten, auf dieselben Dateien zuzugreifen.

>[!WARNING]
>
>**Ändern oder löschen Sie niemals den Inhalt von`/data/exports`**.
>
>`/data/exports` ist der zugrunde liegende Speicher hinter dem freigegebenen Dateisystem und wird von GlusterFS verwaltet.
>
>Das Dateisystem dort enthält nicht nur den Dateiinhalt, sondern Metadaten zum Status des Dateisystems, um eine Synchronisation zwischen den Knoten Ihres Clusters zu ermöglichen. **Das Ändern oder Löschen von Dateien direkt in diesem Dateisystem beschädigt das freigegebene Dateisystem, was umfangreiche Reparaturen oder Datenwiederherstellungen erfordert.**

Um die größten Dateien zu finden, die für das Löschen geeignet sein könnten, führen Sie den folgenden Befehl aus (bei großen oder ausgelasteten Projekten kann es bis zu einer Stunde dauern):

```bash
FS='/data/exports';NUMRESULTS=20;resize;clear; echo "Please find below the Largest Directories and Files:";date;df -h $FS; echo "Largest Directories:";nice -n 19 find /app/*/ -type d -ls 2>/dev/null| sort -rnk1| head -n $NUMRESULTS| awk '
{printf "%d MB %s\n", $1/1024,$2}
';echo "Largest Files:"; nice -n 19 find /app/*/ -type f -ls 2>/dev/null| sort -rnk7| head -n $NUMRESULTS|awk '
{printf "%d MB\t%s\n", ($7/1024)/1024,$NF}
'; echo "Please use the above information to clear any unwanted data from the server, it is important this is done as soon as possible to ensure your server stays functional.";
```

Die Ausgabe des Befehls enthält eine Liste der größten Dateien und Verzeichnisse mit den angegebenen Größen.

## Verwandtes Lesen

In unserer Support-Wissensdatenbank:

* [Erhöhen Sie den Speicherplatz für die Integrationsumgebung in Cloud.](/help/how-to/general/increase-disk-space-for-integration-environment-on-cloud.md)
* [Geringer Festplattenspeicher](/help/troubleshooting/miscellaneous/low-disk-space.md)

In unserer Entwicklerdokumentation:

* [Verwalten des Festplattenspeichers](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space)
