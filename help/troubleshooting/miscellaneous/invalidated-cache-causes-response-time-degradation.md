---
title: Invalidierter Cache führt zu einer Verschlechterung der Antwortzeit
description: Dieser Artikel bietet eine Lösung, wie Sie die Cache-Invalidierung vermeiden können, die die langsame Leistung eines Adobe Commerce-Stores verursachen könnte.
exl-id: 7cb6a39f-923b-4acc-965d-23cf7b52c25a
feature: Cache, Catalog Management, Categories
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# Invalidierter Cache führt zu einer Verschlechterung der Antwortzeit

Dieser Artikel bietet eine Lösung, wie Sie die Cache-Invalidierung vermeiden können, die die langsame Leistung eines Adobe Commerce-Stores verursachen könnte.

BETROFFENE PRODUKTE UND VERSIONEN:

* Adobe Commerce On-Premises 2.2.x, 2.3.x
* Adobe Commerce auf Cloud-Infrastruktur 2.2.x, 2.3.x

## Problem

Langsame Site-Reaktion.

## Ursache

Lange Antwortzeiten können dadurch verursacht werden, dass der Cache invalidiert (geleert) wird.

Der Cache wird verwendet, um schnelle Antworten auf die Anfragen der Site-Besucher zu generieren. Wenn keine geeigneten Cache-Daten verfügbar sind, ruft die Adobe Commerce-Anwendung die Daten aus der Datenbank ab, berechnet und aggregiert die Daten und speichert sie im Cache-Speicher. Der Cache-Erzeugungsprozess erfordert zusätzliche Systemressourcen, was zu einer vollständigen Beeinträchtigung der Reaktionszeit führt.

In Adobe Commerce gibt es zwei Arten von Cache:

1. Intern:
   * Speichert Daten auf dem Server
   * speichert bestimmte Daten (Konfiguration, Produktdetails, Kategoriedaten usw.),
1. Extern:
   * CDN oder Lack (im Fall von Adobe Commerce auf Cloud-Infrastruktur - Fastly CDN)
   * Speichert bereits generierte vollständige Seiten. Beispiel: Katalog/Kategorie, Katalog/Produktseiten usw.

### Überprüfen, ob der Cache ungültig gemacht wurde

Informationen zu den ungültigen Cache-Typen finden Sie in der `<install_directory>/var/log/debug.log`.

Gehen Sie dazu folgendermaßen vor:

1. `<install_directory>/var/log/debug.log` öffnen
1. Suchen Sie nach *cache\_invalidate* &quot;.
1. Überprüfen Sie dann das angegebene Tag. Dies zeigt an, welcher Cache geleert wurde. Möglicherweise treten aufgrund des ungültigen Caches Probleme auf, wenn ein Tag ohne bestimmte Entitäts-ID angezeigt wird, z. B.:
   * `cat_p` - steht für Catalog Product Cache.
   * `cat_c` - Katalog-Kategorie-Cache.
   * `FPC` - Vollständiger Seiten-Cache.
   * `CONFIG` - Konfigurations-Cache.

   Selbst eine Bereinigung würde die Reaktion der Website verlangsamen. Wenn das Tag eine Entitäts-ID enthält, z. B. `category_product_1258`, würde dies den Cache für ein bestimmtes Produkt oder eine bestimmte Kategorie angeben usw. Das Leeren des Caches für ein bestimmtes Produkt oder eine bestimmte Kategorie würde nicht dazu führen, dass die Reaktionszeit signifikant abnimmt.

Im Folgenden finden Sie ein Beispiel für eine `debug.log` mit Datensätzen über die geleerte `cat_p` und `category_product_15044` Cache:

![Beispiel für den debug.log-Inhalt](assets/debug_log_sample.png)

Normalerweise wird der Cache aus folgenden Gründen ungültig:

* Vollständige Neuindizierung.
* Flash-Cache von CLI, entweder manuell oder mithilfe von Cron.

## Empfehlung

1. Vermeiden Sie es, den Cache über die Commerce-CLI zu leeren.
1. Konfigurieren Sie Indexer so **dass sie nach Zeitplan aktualisiert werden** anstelle von **Aktualisieren im Speichermodus** da letzterer eine vollständige Neuindizierung Trigger. Weitere Informationen finden Sie unter [Indexer verwalten > Indexer konfigurieren](https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/cli/manage-indexers#configure-indexers) in unserer Entwicklerdokumentation.
