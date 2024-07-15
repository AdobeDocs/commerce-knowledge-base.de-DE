---
title: Invalidierter Cache führt zu einer Verschlechterung der Reaktionszeit
description: Dieser Artikel bietet eine Lösung, wie Sie eine Cache-Invalidierung vermeiden können, was die Leistung eines Adobe Commerce-Stores verlangsamen kann.
exl-id: 7cb6a39f-923b-4acc-965d-23cf7b52c25a
feature: Cache, Catalog Management, Categories
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# Invalidierter Cache führt zu einer Verschlechterung der Reaktionszeit

Dieser Artikel bietet eine Lösung, wie Sie eine Cache-Invalidierung vermeiden können, was die Leistung eines Adobe Commerce-Stores verlangsamen kann.

BETROFFENE PRODUKTE UND VERSIONEN:

* Adobe Commerce lokal 2.2.x, 2.3.x
* Adobe Commerce auf Cloud-Infrastruktur 2.2.x, 2.3.x

## Problem

Langsame Site-Antwort.

## Ursache

Eine lange Reaktionszeit kann dadurch verursacht werden, dass der Cache invalidiert (geleert) wird.

Der Cache wird verwendet, um schnelle Antworten auf die Anforderungen der Site-Besucher zu generieren. Wenn keine entsprechenden Cachedaten verfügbar sind, ruft die Adobe Commerce-Anwendung die Daten aus der Datenbank ab, berechnet und aggregiert die Daten und speichert sie im Cache-Speicher. Der Cache-Generierungsprozess erfordert zusätzliche Systemressourcen, die zu einer vollständigen Verschlechterung der Antwortzeit führen.

In Adobe Commerce gibt es zwei Cache-Typen:

1. Intern:
   * speichert Daten auf dem Server
   * speichert bestimmte Daten (Konfiguration, Produktdetails, Kategoriedetails usw.)
1. Extern:
   * CDN oder Varnish (im Fall von Adobe Commerce über Cloud-Infrastruktur - Schnelles CDN)
   * speichert bereits generierte vollständige Seiten. Beispiel: Katalog/Kategorie, Katalog/Produktseiten usw.

### Überprüfen, ob der Cache ungültig gemacht wurde

Informationen zu den invalidierten Cache-Typen finden Sie in der Datei &quot;`<install_directory>/var/log/debug.log`&quot;.

Gehen Sie dazu folgendermaßen vor:

1. Öffnen Sie `<install_directory>/var/log/debug.log`
1. Suchen Sie nach der Meldung &quot;*cache\_invalidate* &quot;.
1. Überprüfen Sie dann das angegebene Tag. Er gibt an, welcher Cache geleert wurde. Möglicherweise treten aufgrund des invalidierten Caches Probleme auf, wenn ein Tag ohne bestimmte Entitäts-ID angezeigt wird, z. B.:
   * `cat_p` - steht für den Cache des Katalogprodukts.
   * `cat_c` - Cache der Katalogkategorie.
   * `FPC` - Vollständiger Seiten-Cache.
   * `CONFIG` - Konfigurationscache.

   Sogar eines von ihnen würde die Antwort der Website verlangsamen. Wenn das Tag eine Entitäts-ID enthält, z. B. &quot;`category_product_1258`&quot;, würde dies den Cache für ein bestimmtes Produkt oder eine bestimmte Kategorie angeben usw. Das Leeren des Caches für ein bestimmtes Produkt oder eine bestimmte Kategorie würde nicht dazu führen, dass die Reaktionszeit signifikant zurückgeht.

Im Folgenden finden Sie ein Beispiel eines `debug.log` mit Datensätzen zum geleerten `cat_p` - und `category_product_15044` -Cache:

![Beispiel des debug.log-Inhalts](assets/debug_log_sample.png)

In der Regel wird der Cache durch Folgendes ungültig gemacht:

* Vollständige Neuindizierung.
* Zwischenspeicher aus CLI (manuell oder mithilfe von Cron) erfassen.

## Empfehlung

1. Vermeiden Sie das Leeren des Cache aus der Commerce-CLI.
1. Konfigurieren Sie die Indexer auf **Aktualisieren nach Zeitplan** anstelle von **Aktualisieren im Speichermodus** , da letztere die vollständige Neuindizierung der Trigger durchführen. Weitere Informationen finden Sie unter [Verwalten der Indexer > Konfigurieren von Indexern](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-index.html#configure-indexers) in unserer Entwicklerdokumentation.
