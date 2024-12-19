---
title: Produkt wird nicht in der Storefront angezeigt
description: Dieser Artikel bietet Lösungen für Fälle, in denen Produkte nicht in der Storefront angezeigt werden.
exl-id: 454eca5b-4722-46e0-8e5d-3daf8e3e675a
feature: Cache, Categories, Console, Products, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# Produkt wird nicht in der Storefront angezeigt

Dieser Artikel bietet Lösungen für Fälle, in denen Produkte nicht in der Storefront angezeigt werden.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premises X.X.X
* Adobe Commerce auf Cloud-Infrastruktur X.X.X

## Problem

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich beim Commerce Admin an.
1. Navigieren Sie **Katalog** > **Produkte**.

   ![open_product_page_magento_2.4.1.png](assets/open_product_page_magento_2.4.1.png)

1. Klicken Sie **Produkt hinzufügen** und durchlaufen Sie den Prozess zur Produkterstellung. Oder importieren Sie Produkte aus einer CSV-Datei.

<u>Erwartetes Ergebnis</u>:

Produkt wird in der Storefront angezeigt.

<u>Tatsächliches </u>:

Produkt wird nicht angezeigt.

## Ursache

Dies kann verschiedene Ursachen haben. Führen Sie die folgenden Schritte aus, um die wichtigsten Punkte zu überprüfen, die Ihnen bei der Identifizierung und Lösung des Problems helfen könnten.

## Lösung

Jeder der folgenden Punkte kann das Problem beheben.

* Überprüfen Sie die Produkteinstellungen in Admin. Wechseln Sie **Katalog** > **Produkte**, öffnen Sie die Produktseite und stellen Sie sicher, dass die folgenden Felder korrekt konfiguriert sind:
   * **Produkt aktivieren** = *Ja.*
   * **Lagerstatus**: *Auf Lager*. Wenn *Nicht vorrätig* der richtige Wert ist, stellen Sie sicher, dass **Nicht vorrätige Produkte anzeigen** (**STORES** > **Settings** > **Configuration** > **CATALOG** **** > **Stock Options** > **Nicht vorrätige Produkte anzeigen**) auf *Ja* (auf globaler Ebene konfiguriert) eingestellt ist.
   * **Kategorien**: Wenn Sie versuchen, das Produkt auf einer Kategorieseite zu finden, überprüfen Sie, ob das Produkt der Kategorie zugewiesen ist. Um die Fehlerbehebung zu vereinfachen, erstellen Sie eine neue Kategorie von der aktuellen Seite aus und weisen Sie ihr ein Produkt zu.
   * **visible** = *catalog, search.*
   * Stellen Sie **Abschnitt „Produkt auf Websites** sicher, dass das Produkt der richtigen Website zugewiesen ist.
   * Wechseln Sie den Bereichsselektor in die Store-Ansicht, in der Sie versuchen, Ihr Produkt in der Storefront zu finden, und überprüfen Sie dieselben Einstellungen.
* Führen Sie die vollständige Neuindizierung durch, indem Sie `bin/magento indexer:reindex` über die Konsole ausführen, und leeren Sie den gesamten Cache im Admin unter **System** > **Tools** > **Cache-Verwaltung** oder über die Konsole, indem Sie `bin/magento cache:clean` ausführen.
* Wenn das oben Genannte nicht hilfreich ist, können Sie weitere Nachforschungen anstellen, indem Sie die Protokolle im `var/log` Verzeichnis überprüfen.

## Lesen Sie diesbezüglich in unserer Support-Wissensdatenbank

* [Protokollspeicherorte (Verzeichnisse) für die Pro-Architektur](/help/how-to/general/log-locations-directories-for-pro-plan-integration-staging-production.md)
* [Protokollspeicherorte (Verzeichnisse) für Starter-Architektur](/help/how-to/general/log-locations-directories-for-starter-plan.md)
