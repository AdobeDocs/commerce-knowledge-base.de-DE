---
title: Erhöhte Ausführungszeit für asynchrone Massenwebendpunkte nach dem APSB25-08-Sicherheits-Patch
description: Dieser Artikel bietet einen Hotfix für das Problem, dass POST-REST/all/async/bulk/V1/products-Anfragen für mehr als 1000 Einträge nach der Anwendung des APSB25-08-Sicherheits-Patches eine erheblich längere Ausführungszeit erfahren.
feature: Security, Cache, REST, Products, Customers
role: Admin, Developer
source-git-commit: fce7f860b9fddd694b311ffc4acd56a48c06e14b
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# Erhöhte Ausführungszeit für alle asynchronen Massenwebendpunkte nach dem APSB25-08-Sicherheits-Patch

Dieser Artikel enthält einen Hotfix für alle asynchronen Massenwebendpunkte, z. B. `POST rest/all/async/bulk/V1/products` mit über 1.000 Einträgen, die nach der Anwendung des Sicherheits-Patches APSB25-08 deutlich längere Ausführungszeiten aufweisen.

## Betroffene Produkte und Versionen

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4, 2.4.4-p1, 2.4.4-p2, 2.4.4-p3, 2.4.4-p4, 2.4.4-p5, 2.4.4-p6, 2.4.4-p7, 2.4.4-p8, 2.4.4-p9, 2.4.4-p10, 2.4.4-p11, 2.4.4-p12

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5, 2.4.5-p1, 2.4.5-p2, 2.4.5-p3, 2.4.5-p4, 2.4.5-p5, 2.4.5-p6, 2.4.5-p7, 2.4.5-p8, 2.4.5-p9, 2.4.5-p10, 2.4.5-p11

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6, 2.4.6-p1, 2.4.6-p2, 2.4.6-p3, 2.4.6-p4, 2.4.6-p5, 2.4.6-p6, 2.4.6-p7, 2.4.6-p8, 2.4.6-p9

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7, 2.4.7-p1, 2.4.7-p2, 2.4.7-p3, 2.4.7-p4

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.8

## Problem

Nach der Installation des Sicherheits-Patches APSB25-08 dauert die Ausführung von `POST rest/all/async/bulk/V1/products` mit über 1.000 Einträgen erheblich länger.

<u>Schritte zur Reproduktion</u>:

1. Stellen Sie eine `POST rest/all/async/bulk/V1/products` Anfrage mit mehr als 1000 Einträgen (Name, SKU und Beschreibung sind ausreichend).
1. Notieren Sie die für die Anfrage benötigte Zeit.
1. Wenden Sie den APSB25-08-Sicherheits-Patch an und bereinigen Sie die generierten Daten und den Cache mithilfe von `se:di:co`.
1. `bin/magento c:f` ausführen.
1. Wechseln Sie zur Storefront, um sicherzustellen, dass der Cache und die generierten Dateien vorhanden sind.
1. Wiederholen Sie die Anfrage aus Schritt 1.
1. Beachten Sie, dass die Anfrage länger dauert.
1. Entfernen Sie den APSB25-08-Sicherheits-Patch, leeren Sie den Cache, generieren Sie den Code neu und wiederholen Sie die Anfrage aus Schritt 1, um zu bestätigen, dass die Ausführungszeit wieder normal ist. (Optional)

<u>Erwartete Ergebnisse</u>:

Die Ausführungszeit für `async/bulk`-Anfragen hat sich nach der Anwendung des Sicherheits-Patches erheblich verlängert.

<u>Tatsächliche Ergebnisse</u>:

Die Ausführungszeit für `async/bulk`-Anfragen sollte nach der Anwendung des Sicherheits-Patches nicht wesentlich verlängert worden sein, obwohl ein gewisser Anstieg der Zeit erwartet wird.

## Lösung

Um das Problem zu beheben, wenden Sie [AC-14078-2-4x-composer-patch.zip](assets/AC-14078-2-4x-composer-patch.zip) an.

## Anbringen des Pflasters

Entpacken Sie die Datei und [ Sie in unserer Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html)Wissensdatenbank die Anleitung „So wenden Sie einen von Adobe bereitgestellten Composer-Patch an“.

## Verwandtes Lesen

* [Sicherheitsupdate für Adobe Commerce verfügbar - APSB25-08](/help/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-08.md)
