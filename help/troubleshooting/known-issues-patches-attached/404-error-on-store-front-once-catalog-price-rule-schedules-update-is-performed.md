---
title: 404 Fehler auf der Storefront, sobald die Zeitpläne der Katalogpreisregeln aktualisiert wurden
description: Dieser Artikel enthält einen Patch und die erforderlichen Schritte zum Beheben des bekannten Adobe Commerce 2.2.1-Problems beim Abrufen eines 404-Fehlers auf allen Store-Titelseiten, nachdem eine Aktualisierung der Katalogpreisregel erstellt und deren Startzeit später bearbeitet wurde. Um das Problem zu beheben, müssen Sie den Patch anwenden.
exl-id: 7ea148a5-56cb-479a-8b2f-fae8b3bd4b22
feature: Cache, Catalog Management, Marketing Tools, Orders, Price Rules
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 0%

---

# 404 Fehler auf der Storefront, sobald die Zeitpläne der Katalogpreisregeln aktualisiert wurden

Dieser Artikel enthält einen Patch und die erforderlichen Schritte zum Beheben des bekannten Adobe Commerce 2.2.1-Problems beim Abrufen eines 404-Fehlers auf allen Store-Titelseiten, nachdem eine Aktualisierung der Katalogpreisregel erstellt und deren Startzeit später bearbeitet wurde. Um das Problem zu beheben, müssen Sie den Patch anwenden.

## Problem

Storefront-Seiten sind nicht mehr verfügbar und geben den 404-Fehler zurück. Das Problem tritt auf, nachdem die Aktualisierung der aktiven Katalogpreisregel fällig wird, vorausgesetzt, das Anfangsdatum dieser Aktualisierung wurde nach der ersten Erstellung bearbeitet.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie in Commerce Admin eine neue Katalogpreisregel unter **Marketing** > **Promotions** > **Katalogpreisregel**.
1. Im **Katalogpreisregel** Raster, klicken **Bearbeiten,** eine neue Aktualisierung planen und **Status** nach *Aktiv.*
1. Navigieren Sie zu **Inhalt** > **Inhaltstaging** > **Dashboard.**
1. Wählen Sie das kürzlich erstellte Update aus und ändern Sie die Startzeit.
1. Speichern Sie die Änderungen.

<u>Erwartetes Ergebnis</u> :

Wenn das Startdatum Aktualisieren wirksam wird, wird die Katalogpreisregel erfolgreich angewendet.

<u>Tatsächliches Ergebnis</u> :

Wenn das Startdatum der Aktualisierung in Kraft tritt, sind alle Kataloge und Produkte in der Storefront nicht mehr verfügbar und geben den 404-Fehler zurück.

## Lösung

Um Katalogseiten wiederherzustellen und die Funktionen zur Aktualisierung der Katalogpreise vollständig zu nutzen, müssen Sie den Patch installieren, die Regel sowohl manuell als auch im Admin löschen und die ungültigen Links in der Datenbank korrigieren. Außerdem müssen Sie die Katalogpreisregel neu erstellen.

Im Folgenden werden die erforderlichen Schritte detailliert beschrieben:

1. [Wenden Sie den Patch an](#patch).
1. Löschen Sie in Commerce Admin die Katalogpreisregel für das Problem (wo die Startzeit aktualisiert wurde). Öffnen Sie dazu die Regelseite unter **Marketing** > **Promotions** > **Katalogpreisregel** und klicken Sie auf **Regel löschen**.
1. Durch manuellen Zugriff auf die Datenbank wird der zugehörige Datensatz aus der `catalogrule` Tabelle.
1. Korrigieren Sie die ungültigen Links in der Datenbank. Siehe [verwandter Absatz](#fix_links) für Details.
1. In Commerce Admin unter **Marketing**, gehen Sie zu **Promotions** > **Katalogpreisregel** und erstellen Sie die neue Regel mit der erforderlichen Konfiguration.
1. Löschen Sie den Browsercache unter **System** > **Cacheverwaltung**.
1. Stellen Sie sicher, dass die Cron-Aufträge ordnungsgemäß konfiguriert sind und erfolgreich ausgeführt werden können.

## Patch {#patch}

Der Patch ist an diesen Artikel angehängt. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link:

[MDVA-7392\_EE\_2.2.1\_COMPOSER\_v2.patch herunterladen](assets/MDVA-7392_EE_2.2.1_COMPOSER_v2.patch.zip)

## Kompatible Adobe Commerce-Versionen:

Der Patch wurde für erstellt:

* Adobe Commerce 2.2.1

Der Patch ist auch mit den folgenden Adobe Commerce-Versionen und -Editionen kompatibel (löst das Problem jedoch möglicherweise nicht):

* Adobe Commerce auf Cloud-Infrastruktur 2.2.0 - 2.2.4
* Adobe Commerce vor Ort 2.2.0 und 2.2.2 - 2.2.4

## Anwenden des Pflasters

Anweisungen finden Sie unter [Anwenden eines von Adobe bereitgestellten Composer-Patches](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in unserer Wissensdatenbank.

## Beheben Sie die ungültigen Links zum Staging in DB {#fix_links}

>[!WARNING]
>
>Es wird dringend empfohlen, vor der Bearbeitung der Datenbank eine Datenbanksicherung zu erstellen. Wir empfehlen auch, Abfragen zur Entwicklungsumgebung zuerst zu testen.

Führen Sie die folgenden Schritte aus, um die Zeilen mit ungültigen Links zum `staging_update` Tabelle.

1. Überprüfen Sie, ob die ungültigen Links zur `staging_update` -Tabelle in `flag` Tabelle. Dies wären Datensätze, bei denen `flag_code=staging`.
1. Identifizieren Sie die ungültige Version aus der `flag` Tabelle mit der folgenden Abfrage:

   ```sql
   SELECT flag_data FROM flag WHERE flag_code = 'staging';
   ```

1. Aus dem `staging_update` -Tabelle, wählen Sie die vorhandene Version aus, die kleiner als die aktuelle (ungültige) Version ist, und rufen Sie den Versionswert ab, der zwei Zahlen zurückgibt. Sie nehmen es, nicht die vorherige Version, um die Situation zu vermeiden, in der die vorherige Version die maximale Version in der `staging_update` -Tabelle, die angewendet werden könnte, und wir müssen sie noch einmal anwenden.

   ```sql
   SELECT id FROM staging_update WHERE id < %current_id% ORDER BY id DESC LIMIT 1, 1
   ```

   Die Version, die Sie erhalten, ist Ihre gültige Version `id`.

1. Für Zeilen mit ungültigen Links im `flag` -Tabelle, legen Sie die `flag_data` -Werte zu Daten, die eine gültige Versions-ID enthalten. Dies hilft, die Leistung beim Neuindizierungsschritt zu speichern, und ermöglicht es, eine Neuindizierung aller Entitäten zu vermeiden.

   ```sql
   UPDATE flag SET flag_data=REPLACE(flag_data, '%invalid_id%', '%new_valid_id%') WHERE flag_code='staging';
   ```

<u>Beispiel:</u>

```sql
SELECT flag_data FROM flag WHERE flag_code = 'staging'; <code class="language-bash">Response < 2.2 version</code>
```

```bash
+-------------------------------------------------+
```

```bash
| flag_data                                       |
```

```bash
+-------------------------------------------------+
```

```bash
| a:1:{s:15:"current_version";s:10:"1490005140";} |
```

```bash
+-------------------------------------------------+
```

```bash
Response from 2.2 version
```

```bash
+-------------------------------------------------+
```

```bash
| flag_data                                       |
```

```bash
+-------------------------------------------------+
```

```bash
| {"current_version":"1490005140"} |
```

```bash
+-------------------------------------------------+
```

```sql
SELECT id FROM staging_update WHERE id < 1490005140 <code class="language-sql">ORDER BY id DESC LIMIT 1, 1</code>;
```

```bash
Response:
```

```bash
1490005138
```

```sql
UPDATE flag SET flag_data=REPLACE(flag_data, '1490005140', '1490005138') WHERE flag_code='staging';
```

## Attached Files
