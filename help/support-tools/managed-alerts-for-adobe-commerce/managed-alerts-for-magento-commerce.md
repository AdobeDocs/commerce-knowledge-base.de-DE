---
title: Verwaltete Warnhinweise für Adobe Commerce
description: Wenn Sie Adobe Commerce on Cloud Infrastructure Pro Plan Architecture-Kunde sind, können Sie verwaltete Warnhinweise verwenden, um den Zustand Ihrer Site zu verstehen. Wenn Sie Adobe Commerce on Cloud Infrastructure Starter Plan Architecture-Kunde sind, erhalten Sie nur Warnhinweise zu den Apdex- und Fehlerratenbedingungen.
exl-id: 4d08eaad-a3ce-4f6c-9c32-58e44e1d6534
feature: Observability, Support, Tools and External Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# Verwaltete Warnhinweise für Adobe Commerce


Wir haben wichtige Dashboards und Warnhinweise eingerichtet, die Ihnen dabei helfen zu verstehen, wann Ihre Site kritische Speicher- und Apdex-Level erreicht (Zufriedenheit der Benutzer mit der Reaktionszeit von Anwendungen und Services). Dies kann Ihnen helfen, Maßnahmen zu ergreifen, bevor Sie langsame Antwortzeiten oder einen Ausfall bemerken. Sie können die Warnungen mit den unten aufgeführten Artikeln beheben. Bevor Sie die Warnhinweise verwenden können, richten Sie zunächst Benachrichtigungskanäle ein. Siehe [New Relic-Benachrichtigungskanäle konfigurieren](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/new-relic/new-relic-service) in unserer Entwicklerdokumentation.

>[!NOTE]
>
>Wenn verwaltete Warnhinweise für die Adobe Commerce-Warnhinweisrichtlinie nicht verfügbar sind, kann dies daran liegen, dass dieses Konto neu erstellt wurde oder dass New Relic kürzlich konfiguriert wurde. Jeden Dienstag wird ein Prozess ausgeführt, um die Warnmeldungsrichtlinie zu diesen Konten hinzuzufügen. Die Warnmeldungsrichtlinie sollte Ihnen am Tag nach der Ausführung des nächsten Prozesses zur Verfügung stehen. Wenn die Richtlinie immer noch fehlt, [ Sie eine Adobe Commerce-Support-Anfrage ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket-Submit-a-support-ticket) und geben Sie Ihre Projekt-ID an.

Unten in der Tabelle finden Sie Links zu den KB-Artikeln mit Schritten zur Fehlerbehebung bei diesen Warnhinweisen:

* Verwaltete Warnhinweise für Adobe Commerce: Warnhinweis für CPU
* Verwaltete Warnhinweise für Adobe Commerce: Kritischer Warnhinweis für CPU
* Verwaltete Warnhinweise für Adobe Commerce: Speicherwarnhinweis
* Verwaltete Warnhinweise für Adobe Commerce: Kritischer Warnhinweis zum Speicher
* Verwaltete Warnhinweise für Adobe Commerce: Apdex-Warnhinweis
* Verwaltete Warnhinweise für Adobe Commerce: Kritischer Warnhinweis von Apdex
* Verwaltete Warnhinweise für Adobe Commerce: Warnhinweis bezüglich Festplatte
* Verwaltete Warnhinweise für Adobe Commerce: Kritischer Warnhinweis auf Festplatte
* Verwaltete Warnhinweise in Adobe Commerce: MariaDB-Warnhinweise
* Verwaltete Warnhinweise auf Adobe Commerce: Warnung bei Redis-Speicher
* Verwaltete Warnhinweise auf Adobe Commerce: Kritischer Warnhinweis zu RediS-Speicher

>[!NOTE]
>
>Die festgelegten Schwellenwerte für Warnhinweise und kritische Warnhinweise basieren auf Untersuchungen, die wir auf der Grundlage historischer Leistungsdaten aus unserem Kundenstamm durchführen, und spiegeln die neuesten Erkenntnisse der Support- und Engineering-Teams von Adobe Commerce wider. Beachten Sie, dass sich diese Schwellenwerte auf der Grundlage aktueller, laufender Analysen ändern können. Der typische Warnhinweisfluss besteht darin, Warnhinweise zu erhalten, die hinsichtlich ihres Schweregrads niedriger oder höher sind. Daher erhalten Sie wahrscheinlich einen Warnhinweis, bevor Sie einen kritischen Warnhinweis erhalten. Informationen zu den Schritten zur Fehlerbehebung finden Sie in den Links zu den Artikeln.

<table style="width: 128.434%; height: 660px;" width="100%">
<tbody>
<tr style="height: 44px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 44px;">
<p><strong>Schweregrad</strong></p>
</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 44px;">
<p><strong>CPU</strong></p>
</td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 44px;">
<p><strong>Arbeitsspeicher</strong></p>
</td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 44px;">
<p><strong>Festplatte</strong></p>
</td>
<td class='"wysiwyg-text-align-center wysiwyg-text-align-center' style="width: 9%; height: 44px;">
<p><strong>APDEX</strong></p>
</td>
<td style="width: 7.058036%; height: 44px;">
<p><strong>MariaDB</strong></p>
</td>
<td class="wysiwyg-text-align-center med-col">
<p><strong>Redis-Speicher</strong></p>
</td>
<td class="wysiwyg-text-align-center large-col" style="width: 24.5638%; height: 44px;">
<p><strong>Artikel zur Fehlerbehebung</strong></p>
</td>
</tr>
<tr style="height: 66px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 66px;">Warnung</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 66px;">✅</td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 9%; height: 66px;"> </td>
<td style="width: 0.058036%; height: 66px;"> </td>
<td style="width: 24.5638%; height: 66px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 66px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-cpu-warning-alert.md">Verwaltete Warnhinweise für Adobe Commerce: Warnhinweis für CPU</a><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-cpu-warning-alert.md"></a></p>
</td>
</tr>
<tr style="height: 66px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 66px;">Kritisch</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 66px;">✅</td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 9%; height: 66px;"> </td>
<td style="width: 0.058036%; height: 66px;"> </td>
<td style="width: 24.5638%; height: 66px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 66px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-on-magento-commerce-cpu-critical-alert.md">Verwaltete Warnhinweise für Adobe Commerce: Kritischer Warnhinweis für CPU</a></p>
</td>
</tr>
<tr style="height: 66px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 66px;">Warnung</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 66px;">✅</td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 9%; height: 66px;"> </td>
<td style="width: 0.058036%; height: 66px;"> </td>
<td style="width: 24.5638%; height: 66px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 66px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-memory-warning-alert.md">Verwaltete Warnhinweise für Adobe Commerce: Speicherwarnhinweis</a></p>
</td>
</tr>
<tr style="height: 66px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 66px;">Kritisch</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 66px;">
<p> </p>
<p>✅</p>
</td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 9%; height: 66px;"> </td>
<td style="width: 0.058036%; height: 66px;"> </td>
<td style="width: 24.5638%; height: 66px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 66px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-on-magento-commerce-memory-critical-alert.md#_critical_memory">Verwaltete Warnhinweise für Adobe Commerce: Kritischer Warnhinweis zum Speicher</a></p>
</td>
</tr>
<tr style="height: 66px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 66px;">Warnung</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 9%; height: 66px;">✅</td>
<td style="width: 0.058036%; height: 66px;"> </td>
<td style="width: 24.5638%; height: 66px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 66px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md">Verwaltete Warnhinweise für Adobe Commerce: Apdex-Warnhinweis</a></p>
</td>
</tr>
<tr style="height: 66px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 66px;">Kritisch</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 9%; height: 66px;">✅</td>
<td style="width: 0.058036%; height: 66px;"> </td>
<td style="width: 24.5638%; height: 66px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 66px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-critical-alert.md">Verwaltete Warnhinweise für Adobe Commerce: Kritischer Warnhinweis von Apdex</a></p>
</td>
</tr>
<tr style="height: 66px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 66px;">Warnung</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 66px;">✅</td>
<td class="wysiwyg-text-align-center" style="width: 9%; height: 66px;"> </td>
<td style="width: 0.058036%; height: 66px;"> </td>
<td style="width: 24.5638%; height: 66px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 66px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-disk-warning-alert.md" title="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-disk-warning-alert.md">Verwaltete Warnhinweise für Adobe Commerce: Warnhinweis bezüglich Festplatte</a></p>
</td>
</tr>
<tr style="height: 66px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 66px;">Kritisch</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 66px;">✅</td>
<td class="wysiwyg-text-align-center" style="width: 9%; height: 66px;"> </td>
<td style="width: 0.058036%; height: 66px;"> </td>
<td style="width: 24.5638%; height: 66px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 66px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-disk-critical-alert.md" title="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-disk-critical-alert.md">Verwaltete Warnhinweise für Adobe Commerce: Kritischer Warnhinweis auf Festplatte</a></p>
</td>
</tr>
<tr style="height: 44px;">
<td style="width: 17.8571%; height: 44px;">Warnung und Kritisch</td>
<td style="width: 6.14286%; height: 44px;"> </td>
<td style="width: 10.5714%; height: 44px;"> </td>
<td style="width: 7.14286%; height: 44px;"> </td>
<td style="width: 9%; height: 44px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 0.058036%; height: 44px;">✅</td>
<td style="width: 24.5638%; height: 44px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 44px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-on-magento-commerce-mariadb-alerts.md">Verwaltete Warnhinweise in Adobe Commerce: MariaDB-Warnhinweise</a></p>
</td>
</tr>
<tr style="height: 22px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 22px;">Warnung</td>
<td style="width: 6.14286%; height: 22px;"> </td>
<td style="width: 10.5714%; height: 22px;"> </td>
<td style="width: 7.14286%; height: 22px;"> </td>
<td style="width: 9%; height: 22px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 0.058036%; height: 22px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 24.5638%; height: 22px;">
<p>✅</p>
</td>
<td style="width: 24.5638%; height: 22px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-on-magento-commerce-redis-memory-warning-alert.md">Verwaltete Warnhinweise auf Adobe Commerce: Warnung bei Redis-Speicher</a></p>
</td>
</tr>
<tr style="height: 22px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 22px;">Kritisch</td>
<td style="width: 6.14286%; height: 22px;"> </td>
<td style="width: 10.5714%; height: 22px;"> </td>
<td style="width: 7.14286%; height: 22px;"> </td>
<td style="width: 9%; height: 22px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 0.058036%; height: 22px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 24.5638%; height: 22px;">
<p>✅</p>
</td>
<td style="width: 24.5638%; height: 22px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-on-magento-commerce-redis-memory-critical-alert.md">Verwaltete Warnhinweise auf Adobe Commerce: Kritischer Warnhinweis zu RediS-Speicher</a></p>
</td>
</tr>
</tbody>
</table>
