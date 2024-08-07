---
title: Produktbilder werden trotz der Bildrollen "Produkt bearbeiten"nicht angezeigt
description: Dieser Artikel enthält eine Fehlerbehebung für den Fall, dass Produktbilder trotz der Bildrollen, die auf der Seite "Produktbearbeitung"festgelegt sind, nicht in der Storefront angezeigt werden.
exl-id: 456baa5a-fa16-4bc1-9d6c-54106fae58ca
feature: Cache, Products, Roles/Permissions, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 0%

---

# Produktbilder werden trotz der Bildrollen &quot;Produkt bearbeiten&quot;nicht angezeigt

Dieser Artikel enthält eine Fehlerbehebung für den Fall, dass Produktbilder trotz der Bildrollen, die auf der Seite &quot;Produktbearbeitung&quot;festgelegt sind, nicht in der Storefront angezeigt werden.

**Ursache:** Bei Adobe Commerce-Instanzen mit mehr als einem Store verfügen einige Produktbilder möglicherweise über die `no_selection` -Werte für die Bildelement-Attribute `image`, `small_image`, `thumbnail`, `swatch`. Solche `no_selection` -Werte treten auf, wenn die Rolle des Produktbilds auf den globalen Bereich des All-Stores statt auf den Umfang eines bestimmten Stores gesetzt wird (d. h. auf den **Alle Store-Ansichten** anstelle einer bestimmten **Store-Ansicht**). Um zu verstehen, ob dies der Fall ist, führen Sie das SQL-Skript aus dem Abschnitt **Ursache** unten aus.

**Lösung:** löscht Zeilen mit den `no_selection` -Werten für solche Bilder mithilfe des SQL-Skripts aus dem Abschnitt Lösung unten.

## Betroffene Versionen

* Adobe Commerce On-Premise 2.X.X
* Adobe Commerce auf Cloud-Infrastruktur 2.X.X

## Problem

Produktbilder werden möglicherweise nicht in Ihrer Storefront angezeigt, obwohl die Bildrollen (Basis, Klein, Miniatur, Muster) auf der Produktseite Ihres Admin-Bedienfelds korrekt festgelegt wurden.

Wenn Sie die Produktseite überprüfen, bei der **Store-Ansicht** auf **Alle Store-Ansichten** eingestellt ist, werden für das Bild die Rollen auf dem Bildschirm **Bilddetails** festgelegt.

![all_store_views.png](assets/all_store_views.png)

![image_roles.png](assets/image_roles.png)

Auf der Storefront wird das Bild jedoch nicht angezeigt. Wenn Sie die Produktseite auf der jeweiligen Store-Ebene überprüfen (indem Sie die **Store-Ansicht** wechseln), ist das Bild vorhanden, die Rollen sind jedoch nicht festgelegt.

![image_roles_not_set.png](assets/image_roles_not_set.png)

## Ursache

Bei Adobe Commerce-Instanzen mit mehreren Stores (mit mehr als einem Store) können einige Produktbilder die `no_selection` -Werte für die Attribute `image`, `small_image`, `thumbnail` und `swatch` aufweisen (diese Attribute entsprechen den Bildrollen). Solche `no_selection` -Werte treten auf, wenn die Rolle des Produktbilds auf den globalen Bereich des All-Stores statt auf den Umfang eines bestimmten Stores gesetzt wird (d. h. auf den **Alle Store-Ansichten** anstelle einer bestimmten **Store-Ansicht**).

Technisch gesehen: Unter `store_id=0` (der die globalen Einstellungen für alle Stores in Ihrer Adobe Commerce-Instanz enthält) können die Produktbildrollen festgelegt werden: Das bedeutet, dass die Attribute `image`, `small_image`, `thumbnail` und `swatch` gültige Werte aufweisen (Pfad zu Bildern). Gleichzeitig sind bei `store_id=1` (einer bestimmten Store-Darstellung) die Werte für diese Attribute `no_selection`.

### Überprüfen des Problems

Führen Sie diese SQL-Abfrage aus:

```sql
SELECT `cpev_s`.*, `cpev_0`.`value` AS `store_value` FROM `catalog_product_entity_varchar` `cpev_s` JOIN `eav_attribute` `ea` ON `cpev_s`.`attribute_id` = `ea`.`attribute_id` LEFT JOIN `catalog_product_entity_varchar` `cpev_0` ON `cpev_0`.`row_id` = `cpev_s`.`row_id` AND `cpev_0`.`attribute_id` = `cpev_s`.`attribute_id` AND `cpev_0`.`store_id` = 0 WHERE `cpev_s`.`value` = 'no_selection' AND `ea`.`attribute_code` IN ('image', 'small_image', 'thumbnail') AND `cpev_s`.`store_id` > 0 AND `cpev_s`.`value` != `cpev_0`.`value` AND `cpev_s`.`value` = 'no_selection';
```

Wenn die Abfrage ein Ergebnis wie unten zurückgibt, haben Sie es mit dem in diesem Artikel dokumentierten Problem zu tun:

```sql
+----------+--------------+----------+--------+--------------+----------------------------+
| value_id | attribute_id | store_id | row_id | value        | store_value                |
+----------+--------------+----------+--------+--------------+----------------------------+
|    67722 |           87 |        1 |    481 | no_selection | /3/5/355sss1_main.jpg      |
|    67723 |           88 |        1 |    481 | no_selection | /3/5/355sss1_main.jpg      |
|    67724 |           89 |        1 |    481 | no_selection | /3/5/355sss1_main.jpg      |
|    67814 |           87 |        1 |    503 | no_selection | /s/k/skb2031_main.jpg      |
|     6769 |           87 |        2 |    503 | no_selection | /s/k/skb2031_main.jpg      |
|    67815 |           88 |        1 |    503 | no_selection | /s/k/skb2031_main.jpg      |
|     6770 |           88 |        2 |    503 | no_selection | /s/k/skb2031_main.jpg      |
|    67816 |           89 |        1 |    503 | no_selection | /s/k/skb2031_main.jpg      |
|     6771 |           89 |        2 |    503 | no_selection | /s/k/skb2031_main.jpg      |
+----------+--------------+----------+--------+--------------+----------------------------+
9 rows in set (0.06 sec)
```

### Warum passiert das?

Wenn die Adobe Commerce-Anwendung über mehr als einen Store verfügt, werden die Daten zwischen einem bestimmten Store und den globalen Store-Einstellungen möglicherweise nicht synchronisiert.

Die Werte für `store_id=1` haben eine höhere Priorität als der standardmäßige (globale) Speicher (`store_id=0`). Daher kann das Programm die globalen Bildeinstellungen ignorieren und die Speicherbereichskonfiguration (`no_selection` für Bildelement-Attribute) bei der Anzeige eines Bildes verwenden.

## Lösung {#solution}

Löschen Sie mithilfe dieses SQL-Skripts Attribute mit den `no_selection` -Werten:

```
DELETE `cpev_s`.* FROM `catalog_product_entity_varchar` `cpev_s` JOIN `eav_attribute` `ea` ON `cpev_s`.`attribute_id` = `ea`.`attribute_id` LEFT JOIN `catalog_product_entity_varchar` `cpev_0` ON `cpev_0`.`row_id` = `cpev_s`.`row_id` AND `cpev_0`.`attribute_id` = `cpev_s`.`attribute_id` AND `cpev_0`.`store_id` = 0 WHERE `cpev_s`.`value` = 'no_selection' AND `ea`.`attribute_code` IN ('image', 'small_image', 'thumbnail') AND `cpev_s`.`store_id` > 0 AND `cpev_s`.`value` != `cpev_0`.`value` AND `cpev_s`.`value` = 'no_selection';
```

Nachdem diese Attribute entfernt wurden, werden die Rollen für bestimmte Stores festgelegt und Bilder auf der Storefront angezeigt.

## Zusätzliche Details

Wenn der vollständige Seiten-Cache in Ihrer Adobe Commerce-Instanz aktiviert ist, können Sie die Fixergebnisse nicht sofort sehen.

Damit die Änderungen angezeigt werden, aktualisieren Sie den Seiten-Cache mithilfe des Menüs **Cache-Verwaltung** im Admin-Bedienfeld.

## Weitere Informationen

### Stores und Bereiche

[Speichern und Speichern von Bereichen](/docs/commerce-admin/stores-sales/site-store/stores.html) in unserem Benutzerhandbuch

### Bilder

[Hochladen von Produktbildern](/docs/commerce-admin/catalog/products/digital-assets/product-image.html#upload-an-image) in unserem Benutzerhandbuch

### Cache

* [Cache-Verwaltung](/docs/commerce-admin/systems/tools/cache-management.html) in unserem Benutzer-Administratorsystem-Handbuch.
* [Verwalten des Cache](/docs/commerce-operations/configuration-guide/cli/manage-cache.html) in unserer Entwicklerdokumentation