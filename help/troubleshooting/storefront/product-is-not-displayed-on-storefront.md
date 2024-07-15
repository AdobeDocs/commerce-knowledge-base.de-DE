---
title: Das Produkt wird nicht auf der Storefront angezeigt
description: Dieser Artikel bietet Lösungen für Fälle, in denen Produkte nicht auf der Storefront angezeigt werden.
exl-id: 454eca5b-4722-46e0-8e5d-3daf8e3e675a
feature: Cache, Categories, Console, Products, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# Das Produkt wird nicht auf der Storefront angezeigt

Dieser Artikel bietet Lösungen für Fälle, in denen Produkte nicht auf der Storefront angezeigt werden.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premise X.X.X
* Adobe Commerce in der Cloud-Infrastruktur X.X.X

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich bei Commerce Admin an.
1. Navigieren Sie zu **Katalog** > **Produkte**.

   ![open_product_page_magento_2.4.1.png](assets/open_product_page_magento_2.4.1.png)

1. Klicken Sie auf **Produkt hinzufügen** und gehen Sie zum Erstellungsvorgang für das Produkt. Oder importieren Sie Produkte aus einer CSV-Datei.

<u>Erwartetes Ergebnis</u>:

Das Produkt wird auf der Storefront angezeigt.

<u>Tatsächliches Ergebnis</u>:

Das Produkt wird nicht angezeigt.

## Ursache

Dies kann aus verschiedenen Gründen geschehen. Führen Sie die folgenden Schritte aus, um die wichtigsten Punkte zu prüfen, die bei der Identifizierung und Lösung des Problems hilfreich sein könnten.

## Lösung

Jeder der folgenden Punkte kann das Problem lösen.

* Überprüfen Sie die Produkteinstellungen in Admin. Navigieren Sie zu **Katalog** > **Produkte**, öffnen Sie die Produktseite und stellen Sie sicher, dass die folgenden Felder korrekt konfiguriert sind:
   * **Produkt aktivieren** = *Ja.*
   * **Lagerstatus**: *Auf Lager*. Oder wenn *Nicht auf Lager* der richtige Wert ist, stellen Sie sicher, dass **Nicht vorrätige Produkte anzeigen** (**STORES** > **Einstellungen** > **Konfiguration** > **KATALOG** > **Lagerbestand** > **Lageroptionen** > **}Nicht vorrätige Produkte anzeigen**) auf *Ja* eingestellt ist (global konfiguriert).
   * **Kategorien**: Wenn Sie versuchen, das Produkt auf einer Kategorieseite zu finden, überprüfen Sie, ob das Produkt der Kategorie zugewiesen ist. Um die Fehlerbehebung zu vereinfachen, erstellen Sie auf der aktuellen Seite eine neue Kategorie und weisen Sie ihr ein Produkt zu.
   * **Sichtbarkeit** = *Katalog, Suche.*
   * Stellen Sie im Abschnitt **Produkt in Websites** sicher, dass das Produkt der richtigen Website zugewiesen ist.
   * Wechseln Sie in der Scope-Auswahl zur Store-Ansicht, in der Sie versuchen, Ihr Produkt in der Storefront zu finden, und überprüfen Sie dieselben Einstellungen.
* Führen Sie die vollständige Neuindizierung durch, indem Sie `bin/magento indexer:reindex` aus der Konsole ausführen und den gesamten Cache im Admin unter **System** > **Tools** > **Cache-Verwaltung** oder aus der Konsole leeren, indem Sie `bin/magento cache:clean` ausführen.
* Wenn die obigen Schritte nicht hilfreich sind, können Sie mit der weiteren Untersuchung beginnen, indem Sie die Protokolle im Verzeichnis `var/log` überprüfen.

## Verwandtes Lesen in unserer Wissensdatenbank

* [Protokollspeicherorte (Verzeichnisse) für die Pro-Architektur](/help/how-to/general/log-locations-directories-for-pro-plan-integration-staging-production.md)
* [Protokollspeicherorte (Verzeichnisse) für Starter-Architektur](/help/how-to/general/log-locations-directories-for-starter-plan.md)
