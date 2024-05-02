---
title: 503-Fehler auf Store-Front-Katalog-Seiten mit "Integrity-Einschränkungsverletzung"in Protokollen
description: Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce-Problem in der Cloud-Infrastruktur 2.2.0, das mit dem Problem verbunden ist, dass der Zugriff auf Vorderseiten-Katalogseiten nicht möglich ist.
exl-id: ad363744-756a-48b9-ae11-58642e0ca6a4
feature: Catalog Management, Logs
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# 503-Fehler auf Store-Front-Katalog-Seiten mit &quot;Integrity-Einschränkungsverletzung&quot;in Protokollen

>[!NOTE]
>
>Dieser Artikel enthält einen Patch als Problemumgehung, aber das Problem wurde in Adobe Commerce in der Cloud-Infrastruktur-Version 2.3.3 dauerhaft behoben. Es wird empfohlen, ein Upgrade auf Version 2.3.3 durchzuführen. Führen Sie die Schritte unter [Upgrade der Adobe Commerce-Version](https://devdocs.magento.com/cloud/project/project-upgrade.html) in unserer Entwicklerdokumentation.

Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce-Problem in der Cloud-Infrastruktur 2.2.0, das mit dem Problem verbunden ist, dass der Zugriff auf die Seiten im Front-Katalog nicht möglich ist. Die Fehlermeldung ähnelt der folgenden im Protokoll: *Integrationsbeschränkungsverletzung: 1062 Doppelter Eintrag &#39;%entry%&#39; für Schlüssel &#39;PRIMÄR&#39;, Abfrage war: INSERT IN \`search\_tmp\_%number%*.

## Problem

Die Seiten im Vordergrund-Katalog werden unerwartet barrierefrei. Das Fehlerprotokoll weist eine Fehlerbeschreibung auf, die der folgenden ähnelt: *Integrationsbeschränkungsverletzung: 1062 Doppelter Eintrag &#39;%entry%&#39; für Schlüssel &#39;PRIMÄR&#39;, Abfrage war: INSERT IN \`search\_tmp\_%number%*.

Das Problem bezieht sich auf die Suche und wird durch das Vorhandensein des veralteten Index zusammen mit dem neuen Index nach der Neuindizierung verursacht.

## Lösung

Um das Problem zu beheben, müssen Sie veraltete Indizes aus Elasticsearch entfernen und den Patch anwenden, um zu verhindern, dass sie angezeigt werden.

Verwenden Sie den folgenden Befehl, um alle Indizes aufzulisten:

<pre>curl -X GET %elasticsearch_domain%:%elasticsearch_port%/_cat/indizes</pre>

Um die veralteten Indizes zu entfernen, suchen Sie sie in der Datenbank und verwenden Sie dann den folgenden Befehl:

```bash
curl -X DELETE %elasticsearch_domain%:%elasticsearch_port%/%product_id%_v%outdated_version%
```

Beispiel:

```bash
curl -X DELETE 127.0.0.1:9200/magento2_product_8_v332
```

## Patch

Die Patches sind diesem Artikel beigefügt. Um einen Patch herunterzuladen, scrollen Sie nach unten zum Ende des Artikels und klicken Sie auf den erforderlichen Dateinamen oder klicken Sie auf einen der folgenden Links:

[MDVA-9590\_EE\_2.2.0\_COMPOSER\_v2.patch herunterladen](assets/MDVA-9590_EE_2.2.0_COMPOSER_v2.patch.zip)

[MDVA-13203\_EE\_2.2.4\_V1\_COMPOSER.patch herunterladen](assets/MDVA-13203_EE_2.2.4_V1_COMPOSER.patch.zip)

## Kompatible Adobe Commerce-Versionen

Die Patches wurden für die folgenden Editionen und Versionen erstellt:

* Adobe Commerce auf Cloud-Infrastruktur 2.2.0 (`MDVA-9590_EE_2.2.0_COMPOSER_v2.patch`)
* Adobe Commerce auf Cloud-Infrastruktur 2.2.4 (`MDVA-13203_EE_2.2.4_V1_COMPOSER.patch`)

Die `MDVA-9590_EE_2.2.0_COMPOSER_v2` Patch ist auch mit den folgenden Adobe Commerce-Versionen und -Editionen kompatibel (löst das Problem jedoch möglicherweise nicht):

* Adobe Commerce auf Cloud-Infrastruktur 2.0.X, 2.1.X, 2.2.X und 2.3.0 - 2.3.3
* Adobe Commerce lokal 2.0.X, 2.1.X, 2.2.X und 2.3.0 - 2.3.3

Die `MDVA-13203_EE_2.2.4_V1_COMPOSER` Patch ist auch mit den folgenden Adobe Commerce-Versionen und -Editionen kompatibel (löst das Problem jedoch möglicherweise nicht):

* Adobe Commerce auf Cloud-Infrastruktur 2.0.X, 2.1.X, 2.2.X und 2.3.0 - 2.3.3
* Adobe Commerce lokal 2.0.X, 2.1.X, 2.2.X und 2.3.0 - 2.3.3

## Anwenden des Pflasters

Anweisungen finden Sie unter [Anwenden eines von Adobe bereitgestellten Composer-Patches](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in unserer Wissensdatenbank.

## Nützliche Links

* [Speicherort von Protokolldateien für Adobe Commerce in der Starter-Planarchitektur der Cloud-Infrastruktur](/help/how-to/general/log-locations-directories-for-starter-plan.md) in unserer Wissensdatenbank.
* [Speicherort von Protokolldateien für Adobe Commerce in der Cloud Infrastructure Pro-Planarchitektur](/help/how-to/general/log-locations-directories-for-pro-plan-integration-staging-production.md) in unserer Wissensdatenbank.
* [Speicherort der Protokolldateien für Adobe Commerce](https://devdocs.magento.com/guides/v2.3/cloud/trouble/environments-logs.html) in unserer Entwicklerdokumentation.

## Attached Files
