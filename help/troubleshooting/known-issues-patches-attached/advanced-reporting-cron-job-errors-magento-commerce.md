---
title: Adobe Commerce zu erweiterten Berichtfehlern bei Cron-Aufträgen
description: Dieser Artikel enthält Patches für die Probleme mit Cron-Aufträgen für erweiterte Berichte in Adobe Commerce, die Kunden, die auf erweiterte Berichte zugreifen möchten, einen 404-Fehler verursachen können.
exl-id: c11a5faf-a243-411a-af0f-585a401e6e39
feature: Cache
role: Developer
source-git-commit: 6287e708c830680e04dd068b64cf63ca13ecdedb
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Adobe Commerce zu erweiterten Berichtfehlern bei Cron-Aufträgen

Dieser Artikel enthält Patches für die Probleme mit Cron-Aufträgen für erweiterte Berichte in Adobe Commerce, die Kunden, die auf erweiterte Berichte zugreifen möchten, einen 404-Fehler verursachen können.

## Betroffene Produkte und Versionen

Adobe Commerce (alle Bereitstellungsoptionen) 2.3.x

## Problem

Ein Kunde erhält einen 404-Fehler, wenn er versucht, auf die erweiterte Berichterstellung zuzugreifen, und in den Protokollen, die mit `analytics_collect_data job` .

## Kompatible Magento-Versionen:

Die Patches sind mit den folgenden Adobe Commerce-Versionen und -Editionen kompatibel (lösen das Problem jedoch möglicherweise nicht):

* [MDVA-19391\_EE\_2.3.1\_COMPOSER\_v1.patch](assets/MDVA-19391_EE_2.3.1_COMPOSER_v1.patch.zip): Adobe Commerce (alle Bereitstellungsoptionen) 2.3.1-2.3.4-p2
* [MDVA-18980\_EE\_2.2.6\_COMPOSER\_v1.patch](assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip): Adobe Commerce (alle Bereitstellungsoptionen) 2.3.0
* [MDVA-15136\_EE\_2.2.6\_COMPOSER\_v1.patch](assets/MDVA-15136_EE_2.2.6_COMPOSER_v1.patch.zip): Adobe Commerce (alle Bereitstellungsoptionen) 2.3.0

## **Lösung**

Um das Problem zu beheben, wenden Sie bitte den entsprechenden Patch an, der an diesen Artikel angehängt ist. Um es herunterzuladen, klicken Sie auf die folgenden Links:

* Herunterladen [MDVA-19391\_EE\_2.3.1\_COMPOSER\_v1.patch](assets/MDVA-19391_EE_2.3.1_COMPOSER_v1.patch.zip)
* Herunterladen [MDVA-15136\_EE\_2.2.6\_COMPOSER\_v1.patch](assets/MDVA-15136_EE_2.2.6_COMPOSER_v1.patch.zip)
* Herunterladen [MDVA-18980\_EE\_2.3.1\_COMPOSER\_v1.patch](assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip)

So überprüfen Sie, welcher Patch verwendet werden soll:

<ol><li>Überprüfen Sie die Protokolle mithilfe des folgenden Befehls:<code>grep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz</code>
</li><li>Wählen Sie je nach angezeigtem Fehler mithilfe der Informationen aus der folgenden Tabelle einen Patch aus.<table style="width: 826px;">
<tbody>
<tr>
<td class="wysiwyg-text-align-center">
<p>Fehler</p>
</td>
<td class="wysiwyg-text-align-center">Patch</td>
</tr>
<tr>
<td>
<pre>report.CRITICAL: Fehler beim Ausführen eines Cron-Auftrags {"exception":"[object] (RuntimeException(code: 0): Fehler beim Ausführen eines Cron-Auftrags unter /srv/public_html/vendor/magento/module-cron/Observer/ProcessCronQueueObserver.php:327, TypeError(code: 0): substr_count() erwartet, dass Parameter 1 eine Zeichenfolge ist, Null angegeben unter /srv/public_html/vendor/magento/module-page-builder-analytics/Model/ContentTypeUsageReportProvider.php:106)"} []</pre>ODER<pre>report.ERROR: Cron Job analytics_collect_data hat einen Fehler: substr_count() erwartet, dass der Parameter 1 eine Zeichenfolge ist, null angegeben. Statistik: {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":224919552,"emalloc_start":216398384}
  [] []</pre>
<p> </p>
</td>
<td>Anwenden<a href="assets/MDVA-19391_EE_2.3.1_COMPOSER_v1.patch">MDVA-19391_EE_2.3.1_COMPOSER_v1.patch.zip</a>, leeren Sie den Cache und warten Sie 24 Stunden, bis der Auftrag erneut ausgeführt wird, und versuchen Sie es erneut.</td>
</tr>
<tr>
<td>
<p><em>Fehler beim Öffnen der Datei /tmp/analytics/tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/./tmp/./tmp//tmp/../tmp/../</em></p>
</td>
<td>Anwenden<a href="assets/MDVA-15136_EE_2.2.6_COMPOSER_v1.patch">MDVA-15136_EE_2.2.6_COMPOSER_v1.patch.zip</a>, leeren Sie den Cache und warten Sie 24 Stunden, bis der Auftrag erneut ausgeführt wird, und versuchen Sie es erneut.</td>
</tr>
<tr>
<td><em>Ungültige Chiffre</em></td>
<td>Anwenden<a href="assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch">MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip</a>, leeren Sie den Cache und warten Sie 24 Stunden, bis der Auftrag erneut ausgeführt wird, und versuchen Sie es erneut.</td>
</tr>
</tbody>
</table>
</li></ol>

## Anwenden des Pflasters

Entpacken Sie die Datei und befolgen Sie die Anweisungen unter [Anwenden eines von Adobe bereitgestellten Composer-Patches](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).

## Verwandte Informationen

[Die Datei kann nicht gelöscht werden. Warning!unlink: Kein solcher Datei- oder Verzeichnisfehler vom Administrator](/help/troubleshooting/miscellaneous/file-cannot-be-deleated-no-file-or-directory.md)
