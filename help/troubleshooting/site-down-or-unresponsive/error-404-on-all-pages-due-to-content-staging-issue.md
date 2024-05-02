---
title: Fehler 404 auf allen Seiten aufgrund eines Problems beim Staging von Inhalten
description: Dieser Artikel enthält eine Fehlerbehebung für das Problem mit der Cloud-Infrastruktur in Adobe Commerce vor Ort und Adobe Commerce, bei dem beim Zugriff auf eine Storefront-Seite oder den Commerce-Administrator ein 404-Fehler ausgegeben wird.
exl-id: 62d8ba6e-8550-4e1e-8e8d-8f319c92778a
feature: CMS, Catalog Management, Categories, Page Content, Staging
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 0%

---

# Fehler 404 auf allen Seiten aufgrund eines Problems beim Staging von Inhalten

Dieser Artikel enthält eine Fehlerbehebung für das Problem mit der Cloud-Infrastruktur in Adobe Commerce vor Ort und Adobe Commerce, bei dem beim Zugriff auf eine Storefront-Seite oder den Commerce-Administrator ein 404-Fehler ausgegeben wird.

## Betroffene Produkte und Versionen

* Adobe Commerce lokal 2.2.x, 2.3.x
* Adobe Commerce auf Cloud-Infrastruktur 2.2.x, 2.3.x

## Problem

>[!NOTE]
>
>Dieser Artikel gilt nicht für die Situation, in der Sie beim Versuch, [Vorschau der Staging-Aktualisierung](https://docs.magento.com/user-guide/cms/content-staging-scheduled-update.html#preview-the-scheduled-change). Wenn dieses Problem auftritt, öffnen Sie bitte eine [Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

Der Zugriff auf eine Storefront-Seite oder den Admin-Server führt zum 404-Fehler (die Seite &quot;Ups, unser schlechtes ...&quot;), nachdem Vorgänge mit geplanten Aktualisierungen für Store-Inhalts-Assets ausgeführt wurden, die Folgendes verwenden: [Inhaltstaging](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html) (Aktualisierungen für die Speicherung von Inhalts-Assets, die mithilfe der [Magento\_Staging-Modul](https://developer.adobe.com/commerce/php/module-reference/)). Beispielsweise können Sie ein Produkt mit einer geplanten Aktualisierung gelöscht oder das Enddatum für die geplante Aktualisierung entfernt haben.

Ein Store-Inhalts-Asset umfasst:

* Produkt
* Kategorie
* Katalogpreisregel
* Preisregel für Warenkorb
* CMS-Seite
* CMS-Block
* Widget

Einige Szenarien werden im Abschnitt Ursache weiter unten erläutert.

## Ursache

Die `flag` -Tabelle in der Datenbank (DB) enthält ungültige Links zur `staging_update` Tabelle.

Das Problem bezieht sich auf die Inhaltstaging-Umgebung. Im Folgenden finden Sie zwei besondere Szenarien. Bitte beachten Sie, dass es möglicherweise mehr Situationen gibt, die das Problem Trigger haben.

**Szenario 1:** Löschen eines Inhalts-Assets, das:

* hat eine Aktualisierung geplant, die mit Content Staging durchgeführt wird.
* Die Aktualisierung hat ein Enddatum (d. h. das Ablaufdatum, nach dem das aktualisierte Asset zur vorherigen Version zurückkehrt).
* das Enddatum der Aktualisierung liegt in der Vergangenheit

Das Problem tritt möglicherweise nicht auf, wenn ein gelöschtes Asset kein Enddatum für die geplante Aktualisierung hat.

**Szenario 2:** Entfernung des Enddatums/der Endzeit eines geplanten Updates.

### Identifizieren, ob Ihr Problem damit in Zusammenhang steht

Um festzustellen, ob das in diesem Artikel beschriebene Problem vorliegt, führen Sie die folgende DB-Abfrage aus:

```sql
   SELECT f.flag_data >'$.current_version' as flag_version, (su.id IS NOT NULL) as update_exists
   -> FROM flag f
   -> LEFT JOIN staging_update su
   -> ON su.id = f.flag_data >'$.current_version'
   -> WHERE flag_code = 'staging';
```

Wenn die Abfrage eine Tabelle zurückgibt, in der `update_exists` den Wert &quot;0&quot;hat, ist ein ungültiger Link zum `staging_update` -Tabelle in Ihrer Datenbank vorhanden ist und die Schritte, die im Abschnitt [Lösungsabschnitt](#solution) wird dazu beitragen, das Problem zu lösen. Im Folgenden finden Sie ein Beispiel für das Abfrageergebnis mit `update_exists` Wert gleich &quot;0&quot;:

![update_exists_0.png](assets/update_exists_0.png)

Wenn die Abfrage eine Tabelle zurückgibt, in der `update_exists` den Wert &quot;1&quot;oder ein leeres Ergebnis hat, bedeutet dies, dass Ihr Problem nicht mit Staging-Updates in Zusammenhang steht. Im Folgenden finden Sie ein Beispiel für das Abfrageergebnis mit `update_exists` Wert gleich &quot;1&quot;:

![updates_exists_1.png](assets/updates_exist_1.png)

In diesem Fall können Sie die Variable [Site-Down-Fehlerbehebung](/help/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.md) für Informationen zur Fehlerbehebung.

## Lösung

1. Führen Sie die folgende Abfrage aus, um den ungültigen Link zum `staging_update` table:

   ```sql
   DELETE FROM flag WHERE flag_code = 'staging';
   ```

1. Warten Sie, bis der Cron-Auftrag ausgeführt wird (wird bis zu fünf Minuten ausgeführt, wenn er ordnungsgemäß eingerichtet ist), oder führen Sie ihn manuell aus, wenn kein Cron eingerichtet ist.

Das Problem sollte sofort behoben werden, nachdem der ungültige Link behoben wurde. Wenn das Problem weiterhin besteht, [Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
