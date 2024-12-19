---
title: Fehler 404 auf allen Seiten aufgrund eines Problems mit der Inhalts-Staging-Umgebung
description: Dieser Artikel bietet eine Fehlerbehebung für das Problem mit der Cloud-Infrastruktur, dass bei Adobe Commerce On-Premise und Adobe Commerce auftritt, wenn beim Zugriff auf eine Storefront-Seite oder die [!UICONTROL Commerce Admin] ein 404-Fehler auftritt.
exl-id: 62d8ba6e-8550-4e1e-8e8d-8f319c92778a
feature: CMS, Catalog Management, Categories, Page Content, Staging
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# Fehler 404 auf allen Seiten aufgrund eines Problems mit der Inhalts-Staging-Umgebung

Dieser Artikel bietet eine Fehlerbehebung für das Problem mit der Cloud-Infrastruktur, dass bei Adobe Commerce On-Premise und Adobe Commerce auftritt, wenn beim Zugriff auf eine Storefront-Seite oder die [!UICONTROL Commerce Admin] ein 404-Fehler auftritt.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premises 2.2.x, 2.3.x
* Adobe Commerce auf Cloud-Infrastruktur 2.2.x, 2.3.x

## Problem

>[!NOTE]
>
>Dieser Artikel gilt nicht für die Situation, in der beim Versuch, die Staging-Aktualisierung in der Vorschau anzuzeigen[ der Fehler 404 ](https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/guide-overview#preview-the-scheduled-change). Wenn dieses Problem auftritt, öffnen Sie ein [Support-Ticket](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case).

Der Zugriff auf eine Storefront-Seite oder auf den Admin-Bereich führt zu einem 404-Fehler (die Seite „Hoppla, unsere schlechte …„), nachdem Vorgänge mit geplanten Aktualisierungen für Store-Content-Assets mithilfe von [Content-Staging](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html) durchgeführt wurden (Aktualisierungen für Store-Content-Assets, die mit dem [Magento\_Staging-Modul](https://developer.adobe.com/commerce/php/module-reference/) geplant wurden). Sie haben beispielsweise ein Produkt mit einer geplanten Aktualisierung gelöscht oder das Enddatum für die geplante Aktualisierung entfernt.

Ein Store-Content-Asset umfasst:

* Produkt
* Kategorie
* Katalogpreisregel
* Warenkorb-Preisregel
* CMS-Seite
* CMS-Block
* Widget

Einige Szenarien werden im folgenden Abschnitt Ursache erläutert.

## Ursache

Die `flag` in der Datenbank (DB) enthält ungültige Verknüpfungen zur `staging_update`.

Das Problem betrifft das Staging von Inhalten. Im Folgenden finden Sie zwei spezifische Szenarien. Beachten Sie, dass es weitere Situationen geben kann, in denen das Problem Trigger hat.

**Szenario 1:** Löschen eines Store-Content-Assets, das:

* für eine Aktualisierung mit Inhalts-Staging geplant
* Die Aktualisierung hat ein Enddatum (d. h. das Ablaufdatum, nach dem das aktualisierte Asset auf seine vorherige Version zurückgesetzt wird)
* Das Enddatum der Aktualisierung liegt in der Vergangenheit

Gleichzeitig tritt das Problem möglicherweise nicht auf, wenn ein gelöschtes Asset kein Enddatum für die geplante Aktualisierung hat.

**Szenario 2:** Entfernen des Enddatums/der Endzeit einer geplanten Aktualisierung.

### Identifizieren, ob Ihr Problem im Zusammenhang steht

Um festzustellen, ob es sich bei dem Problem, das Sie haben, um das in diesem Artikel beschriebene handelt, führen Sie die folgende DB-Abfrage aus:

```sql
   SELECT f.flag_data >'$.current_version' as flag_version, (su.id IS NOT NULL) as update_exists
   -> FROM flag f
   -> LEFT JOIN staging_update su
   -> ON su.id = f.flag_data >'$.current_version'
   -> WHERE flag_code = 'staging';
```

Wenn die Abfrage eine Tabelle mit `update_exists` Wert „0“ zurückgibt, ist in Ihrer Datenbank ein ungültiger Link zur `staging_update`-Tabelle vorhanden, und die im Abschnitt [Lösung](#solution) beschriebenen Schritte helfen bei der Lösung des Problems. Im Folgenden finden Sie ein Beispiel für das Abfrageergebnis mit `update_exists` Wert gleich „0“:

![update_exists_0.png](assets/update_exists_0.png)

Wenn die Abfrage eine Tabelle mit `update_exists` Wert „1“ oder ein leeres Ergebnis zurückgibt, bedeutet dies, dass Ihr Problem nicht mit Staging-Aktualisierungen verbunden ist. Im Folgenden finden Sie ein Beispiel für das Abfrageergebnis mit `update_exists` Wert gleich „1“:

![updates_exist_1.png](assets/updates_exist_1.png)

In diesem Fall finden Sie unter &quot;[-Fehlerbehebung“ ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter) Fehlerbehebungsideen.

## Lösung

1. Führen Sie die folgende Abfrage aus, um den ungültigen Link zur `staging_update`-Tabelle zu löschen:

   ```sql
   DELETE FROM flag WHERE flag_code = 'staging';
   ```

1. Warten Sie, bis der [!DNL cron] ausgeführt wird (wird bei ordnungsgemäßer Einrichtung in bis zu fünf Minuten ausgeführt), oder führen Sie ihn manuell aus, wenn Sie [!DNL cron] eingerichtet haben.

Das Problem sollte direkt nach der Behebung des ungültigen Links behoben werden. Wenn das Problem weiterhin besteht[ reichen Sie ein Support-Ticket ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case).

## Verwandtes Lesen

[Best Practices zum Ändern von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook
