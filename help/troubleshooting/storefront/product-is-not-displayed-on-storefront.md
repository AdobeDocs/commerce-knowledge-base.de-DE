---
title: Produkt wird nicht in der Storefront angezeigt
description: Dieser Artikel bietet Lösungen für Fälle, in denen Produkte nicht in der Storefront angezeigt werden.
exl-id: 454eca5b-4722-46e0-8e5d-3daf8e3e675a
feature: Cache, Categories, Console, Products, Storefront
role: Admin
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
  - id: c4af0798-d497-5e6b-8380-19812c26d00a
    internal-label: Console
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '327'
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
  * **Lagerstatus**: *Auf Lager*. Wenn *Nicht vorrätig* der richtige Wert ist, stellen Sie sicher, dass **Nicht vorrätige Produkte anzeigen** (**STORES** > **Settings** > **Configuration** > **CATALOG** **&#x200B;**&#x200B;> **Stock Options** > **Nicht vorrätige Produkte anzeigen**) auf *Ja* (auf globaler Ebene konfiguriert) eingestellt ist.
  * **Kategorien**: Wenn Sie versuchen, das Produkt auf einer Kategorieseite zu finden, überprüfen Sie, ob das Produkt der Kategorie zugewiesen ist. Um die Fehlerbehebung zu vereinfachen, erstellen Sie eine neue Kategorie von der aktuellen Seite aus und weisen Sie ihr ein Produkt zu.
  * **visible** = *catalog, search.*
  * Stellen Sie **Abschnitt „Produkt auf Websites** sicher, dass das Produkt der richtigen Website zugewiesen ist.
  * Wechseln Sie den Bereichsselektor in die Store-Ansicht, in der Sie versuchen, Ihr Produkt in der Storefront zu finden, und überprüfen Sie dieselben Einstellungen.
* Führen Sie die vollständige Neuindizierung durch, indem Sie `bin/magento indexer:reindex` über die Konsole ausführen, und leeren Sie den gesamten Cache im Admin unter **System** > **Tools** > **Cache-Verwaltung** oder über die Konsole, indem Sie `bin/magento cache:clean` ausführen.
* Wenn das oben Genannte nicht hilfreich ist, können Sie weitere Nachforschungen anstellen, indem Sie die Protokolle im `var/log` Verzeichnis überprüfen.



