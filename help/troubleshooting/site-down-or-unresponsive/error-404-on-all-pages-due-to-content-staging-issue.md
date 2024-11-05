---
title: Fehler 404 auf allen Seiten aufgrund eines Problems beim Staging von Inhalten
description: Dieser Artikel enthält eine Fehlerbehebung für das Problem mit der Cloud-Infrastruktur in Adobe Commerce vor Ort und Adobe Commerce, bei dem beim Zugriff auf eine Storefront-Seite oder die [!UICONTROL Commerce Admin] ein 404-Fehler ausgegeben wird.
exl-id: 62d8ba6e-8550-4e1e-8e8d-8f319c92778a
feature: CMS, Catalog Management, Categories, Page Content, Staging
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# Fehler 404 auf allen Seiten aufgrund eines Problems beim Staging von Inhalten

Dieser Artikel enthält eine Fehlerbehebung für das Problem mit der Cloud-Infrastruktur in Adobe Commerce vor Ort und Adobe Commerce, bei dem beim Zugriff auf eine Storefront-Seite oder die [!UICONTROL Commerce Admin] ein 404-Fehler ausgegeben wird.

## Betroffene Produkte und Versionen

* Adobe Commerce lokal 2.2.x, 2.3.x
* Adobe Commerce auf Cloud-Infrastruktur 2.2.x, 2.3.x

## Problem

>[!NOTE]
>
>Dieser Artikel gilt nicht für die Situation, in der Sie einen 404-Fehler erhalten, wenn Sie versuchen, [eine Vorschau des Staging-Updates anzuzeigen](https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/guide-overview#preview-the-scheduled-change). Wenn dieses Problem auftritt, öffnen Sie bitte ein [Support-Ticket](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case).

Der Zugriff auf eine Storefront-Seite oder den Admin-Server führt zum 404-Fehler (die Seite &quot;Ups, unser schlechtes ...&quot;), nachdem Vorgänge mit geplanten Aktualisierungen für Store-Content-Assets unter Verwendung von [Content Staging](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html) ausgeführt wurden (Aktualisierungen für Store-Inhalts-Assets, die mit dem [Magento\_Staging-Modul](https://developer.adobe.com/commerce/php/module-reference/) geplant wurden). Beispielsweise können Sie ein Produkt mit einer geplanten Aktualisierung gelöscht oder das Enddatum für die geplante Aktualisierung entfernt haben.

Ein Store-Inhalts-Asset umfasst:

* Produkt
* Kategorie
* Katalogpreisregel
* Preisregel für Warenkorb
* CMS-Seite
* CMS Block
* Widget

Einige Szenarien werden im Abschnitt Ursache weiter unten erläutert.

## Ursache

Die Tabelle `flag` in der Datenbank (DB) enthält ungültige Links zur Tabelle `staging_update`.

Das Problem bezieht sich auf die Inhaltstaging-Umgebung. Im Folgenden finden Sie zwei besondere Szenarien. Bitte beachten Sie, dass es möglicherweise mehr Situationen gibt, die das Problem Trigger haben.

**Szenario 1:** Löschen eines Store-Inhalts-Assets, das:

* hat eine Aktualisierung geplant, die mit Content Staging durchgeführt wird.
* Die Aktualisierung hat ein Enddatum (d. h. das Ablaufdatum, nach dem das aktualisierte Asset zur vorherigen Version zurückkehrt).
* das Enddatum der Aktualisierung liegt in der Vergangenheit

Das Problem tritt möglicherweise nicht auf, wenn ein gelöschtes Asset kein Enddatum für die geplante Aktualisierung hat.

**Szenario 2:** Entfernung des Enddatums/der Endzeit einer geplanten Aktualisierung.

### Identifizieren, ob Ihr Problem damit in Zusammenhang steht

Um festzustellen, ob das in diesem Artikel beschriebene Problem vorliegt, führen Sie die folgende DB-Abfrage aus:

```sql
   SELECT f.flag_data >'$.current_version' as flag_version, (su.id IS NOT NULL) as update_exists
   -> FROM flag f
   -> LEFT JOIN staging_update su
   -> ON su.id = f.flag_data >'$.current_version'
   -> WHERE flag_code = 'staging';
```

Wenn die Abfrage eine Tabelle zurückgibt, bei der der `update_exists`-Wert &quot;0&quot;ist, ist in Ihrer Datenbank ein ungültiger Link zur `staging_update`-Tabelle vorhanden. Die im Abschnitt [Lösung](#solution) beschriebenen Schritte helfen bei der Lösung des Problems. Im Folgenden finden Sie ein Beispiel des Abfrageergebnisses mit dem Wert `update_exists` gleich &quot;0&quot;:

![update_exists_0.png](assets/update_exists_0.png)

Wenn die Abfrage eine Tabelle zurückgibt, bei der der `update_exists`-Wert &quot;1&quot;oder ein leeres Ergebnis ist, bedeutet dies, dass Ihr Problem nicht mit Staging-Updates in Zusammenhang steht. Im Folgenden finden Sie ein Beispiel des Abfrageergebnisses mit dem Wert `update_exists` gleich &quot;1&quot;:

![updates_exists_1.png](assets/updates_exist_1.png)

In diesem Fall finden Sie möglicherweise Informationen zur Fehlerbehebung in der [Site-Down-Fehlerbehebung](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter).

## Lösung

1. Führen Sie die folgende Abfrage aus, um den ungültigen Link zur Tabelle `staging_update` zu löschen:

   ```sql
   DELETE FROM flag WHERE flag_code = 'staging';
   ```

1. Warten Sie, bis der Auftrag [!DNL cron] ausgeführt wird (er wird bis zu fünf Minuten ausgeführt, wenn er ordnungsgemäß eingerichtet ist), oder führen Sie ihn manuell aus, wenn Sie [!DNL cron] nicht eingerichtet haben.

Das Problem sollte sofort behoben werden, nachdem der ungültige Link behoben wurde. Wenn das Problem weiterhin besteht, senden [ein Support-Ticket](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case).

## Verwandtes Lesen

[Best Practices für die Änderung von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Playbook für die Commerce-Implementierung
