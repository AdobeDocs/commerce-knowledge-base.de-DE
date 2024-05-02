---
title: 'MDVA-32634 Patch: Kategorie in Hierarchie url_path falsch verschieben'
description: Der Patch MDVA-32634 behebt das Problem, dass sich der url\_path der Katalogkategorie nach dem Verschieben der Kategorie in der Hierarchie nicht ändert. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben sein soll.
exl-id: a445dea6-3834-479b-9044-b6d2b863a0b5
feature: Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 0%

---

# MDVA-32634 Patch: Kategorie in Hierarchie url_path verschieben falsch

Der Patch MDVA-32634 behebt das Problem, dass sich der url\_path der Katalogkategorie nach dem Verschieben der Kategorie in der Hierarchie nicht ändert. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.3.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce über Cloud-Infrastruktur und Adobe Commerce vor Ort 2.3.1 - 2.4.1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das Verschieben einer Katalogkategorie in die Hierarchie führt zu einer falschen URL\_path. Die URL\_path der Kategorie, die dem standardmäßigen Speicherbereich \[ zugewiesen ist **id:0** \] bleibt nach dem Verschieben der Kategorie in der Hierarchie unverändert.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich bei Commerce Admin an. Erstellen Sie die folgende Kategoriestruktur unter der Stammkategorie: move-cat sub-move-cat sub-move-cat2 new-cat-move
1. Überprüfen Sie Kategorie \[ url\_path \] Attribut \[ id: 120 \] für die Wertezuweisung in der Tabelle \[ catalog\_category\_entity\_varchar \] mit der folgenden Abfrage:

   ```sql
   SELECT * FROM catalog_category_entity_varchar WHERE attribute_id = 120 ORDER BY value_id DESC LIMIT 4;
   ```

   Es sollte folgendes Ergebnis liefern:

   ```sql
   MariaDB [m24dev]> SELECT * FROM catalog_category_entity_varchar WHERE attribute_id = 120 ORDER BY value_id DESC LIMIT 4;
   ```

   \[ url\_path \] Werte wurden generiert und dem Bereich &quot;Alle Stores&quot;\[ 0 \] zugewiesen. Dies ist im Vergleich zu einer Instanz ohne B2B korrekt.
1. Gehen Sie zur Backend-Kategorienliste, ziehen Sie \[ move-cat \] und legen Sie sie in \[ new-cat-move \] ab. Jetzt sollte die Kategorie wie folgt aussehen: new-cat-move-cat sub-move-cat sub-move-cat2
1. Überprüfen Sie die Tabelle \[ catalog\_category\_entity\_varchar \] mit der folgenden Abfrage:

   ```sql
   SELECT * FROM catalog_category_entity_varchar WHERE attribute_id = 120 ORDER BY value_id DESC LIMIT 16;
   ```

<u>Erwartete Ergebnisse</u>:

Die url\_path, die dem gesamten Speicherbereich \[ 0 \] zugewiesen ist, sollte auch mit dem neuen Pfad aktualisiert werden.

<u>Tatsächliche Ergebnisse</u>:

Die URL\_path, die dem gesamten Speicherbereich \[ 0 \] zugewiesen ist, bleibt unverändert, auch wenn nach dem Verschieben kein solcher Pfad verfügbar ist. Außerdem werden für jeden Store neue url\_path -Werte erstellt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
