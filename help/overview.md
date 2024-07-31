---
title: Wissensdatenbank zur Adobe Commerce-Unterstützung
description: Alles, was Sie für die Fehlerbehebung und Wartung Ihres Commerce-Stores benötigen.
exl-id: feacf38f-2803-4170-a64f-5d7c4567432d
feature: Support
role: Admin
source-git-commit: 738a5455267647d294d222d5bb6149254dcb93dd
workflow-type: tm+mt
source-wordcount: '1394'
ht-degree: 0%

---

# Wissensdatenbank zur Adobe Commerce-Unterstützung

![Knowledge Base-Homepage](../help/assets/knowledge-base-home-page-cover.jpg){width="100%"}

Die Informationen in dieser Wissensdatenbank ergänzen die [Adobe Commerce Developer Documentation](https://developer.adobe.com/commerce/docs), den [Adobe Commerce Merchant Guide](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html) und andere Adobe Commerce-Veröffentlichungen. Es behandelt Fehlerbehebung und Best Practices, hostet Ankündigungen und Antworten FAQs und hebt spezifische Szenarien hervor, die (aus irgendeinem Grund) nicht in der offiziellen Dokumentation erwähnt wurden.

## Was befindet sich in der Wissensdatenbank?

| KATEGORIE | BESCHREIBUNG |
| --- | --- |
| [Support-Tools](/help/support-tools/overview.md) | Verbessern Sie Ihre E-Commerce-Store-Erfahrung mit den verschiedenen Support-Tools von Adobe Commerce. Wir bieten personalisierte Best Practices, Diagnose- und Überwachungstools und die relevantesten Informationen über Ihre Site. |
| [Mitteilungen](/help/announcements/overview.md) | Hier erhalten Sie wichtige Updates von den Adobe Commerce-Teams. |
| [Fehlerbehebung](/help/troubleshooting/overview.md) | Erhalten Sie Self-Service-Lösungen und Patches vom Adobe Commerce-Supportteam. |
| [Benutzerhandbuch für das Help Center](/help/help-center-guide/help-center/magento-help-center-user-guide.md) | Erfahren Sie, wie Sie Ihre Support-Tickets verwalten, freigegebenen Zugriff gewähren und die Knowledge Base effektiv durchsuchen können. |
| [Gewusst wie-zu](/help/how-to/overview.md) | Hier erhalten Sie eine schrittweise Anleitung vom Adobe Commerce-Supportteam. |
| [FAQ](/help/faq/overview.md) | Hier finden Sie häufig gestellte Fragen zu Adobe Commerce-Richtlinien, -Strategien und -Besonderheiten zu Adobe Commerce-Funktionen. |

>[!NOTE]
>
>Um ein neues Ticket zu erstellen, melden Sie sich bei [Adobe Commerce Help Center](https://support.magento.com/) an und befolgen Sie die unter [Support-Ticket senden](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket) beschriebenen Schritte.
>
>Wenn Sie die Option zum Senden eines Tickets nicht sehen, lesen Sie den Abschnitt *[Link zum Senden eines Tickets wird nicht angezeigt](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#no-submit-link)* in unserem [Benutzerhandbuch für das Help Center](/help/help-center-guide/help-center/magento-help-center-user-guide.md).

## Neue Funktionen

<table style="width:100%">
  <tr>
    <th style="width:70%">Beschreibung</th>
    <th style="width:15%">Typ</th>
    <th style="width:15%">Datum</th>
  </tr>

<tr>
    <td>
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/the-magento-cloud-cli-doesnt-show-an-active-environment">Die CLI <code>Magento-cloud</code> zeigt keine aktive Umgebung an:</a> Es gibt mehrere aktive Umgebungen, und Sie versuchen, mit einer Umgebung zu interagieren, indem Sie einen Magento-Cloud-CLI-Befehl (Befehlszeilen-Tool) ausführen. Die Aufforderung zur Auswahl der gewünschten Umgebung listet diese Umgebung jedoch nicht auf.
    </td>
    <td>Neuer Artikel</td>
    <td>30. Juli 2024</td>
  </tr>

<td>
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-obtain-and-apply-security-patches">So rufen Sie einen Sicherheits-Patch ab und wenden ihn an:</a> Dieser Artikel enthält Anweisungen zum Abrufen und Anwenden eines Sicherheits-Patches, der veröffentlicht wurde, Anweisungen jedoch nicht verfügbar sind.  
    </td>
    <td>Neuer Artikel</td>
    <td>30. Juli 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/falling-back-to-elasticsearch7-when-search-engine-set-to-opensearch">Zurücksetzen auf Elasticsearch7, wenn die Suchmaschine auf OpenSearch gesetzt ist:</a> Dieser Artikel bietet eine Lösung für das Problem, wenn der Fehler "Falling back to Elasticsearch7"auftritt, wenn die Suchmaschine in Adobe Commerce auf OpenSearch gesetzt ist. 
    </td>
    <td>Neuer Artikel </td>
    <td>30. Juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/deployment/deployment-failed-there-are-no-commands-defined-in-the-cache-namespace-error">Bereitstellung fehlgeschlagen: Der Namespace-Fehler "cache"enthält keine Befehle:</a> Dieser Artikel bietet eine Lösung für das Problem, wenn Ihre Bereitstellung fehlschlägt und einer der im Protokoll angezeigten Fehler <em>Es sind keine Befehle im Namespace "cache"definiert</em>. 
    </td>
    <td>Neuer Artikel </td>
    <td>30. Juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-55566-mergecart-mutation-fails-with-an-internal-server-error-in-graphql-response">ACSD-5566: <code>mergeCart</code> Mutation schlägt mit internem Serverfehler in GraphQL-Antwort fehl:</a> Der Patch ACSD-55566 behebt das Problem, bei dem die <code>mergeCart</code>-Mutation mit einem internen Serverfehler in der GraphQL-Antwort fehlschlägt. Dieser Patch ist verfügbar, wenn <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 installiert ist.  
    </td>
    <td>Neuer Artikel </td>
    <td>30. Juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-56546-configurable-and-bundle-products-display-as-out-of-stock-on-the-storefront">ACSD-56546: Konfigurierbare und Bundle-Produkte werden auf der Storefront als nicht vorrätig angezeigt:</a> Der Patch ACSD-56546 behebt das Problem, dass die konfigurierbaren und Bundle-Produkte auf der Storefront als nicht vorrätig angezeigt werden. Dieser Patch ist verfügbar, wenn <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 installiert ist.  
    </td>
    <td>Neuer Artikel </td>
    <td>30. Juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-57565-the-order-dashboard-displays-incorrect-order-information">ACSD-57565: Das Bestell-Dashboard zeigt falsche Bestellinformationen an:</a> Der Patch ACSD-57565 behebt das Problem, dass das Bestell-Dashboard falsche Bestellinformationen anzeigt, bis der Zeitraum aktualisiert wurde. Dieser Patch ist verfügbar, wenn <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 installiert ist. 
    </td>
    <td>Neuer Artikel </td>
    <td>30. Juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-57394-incorrect-product-sorting-by-multiple-sort-fields-in-graphql">ACSD-57394: Falsche Produktsortierung nach mehreren Sortierungsattributen in GraphQL:</a> Der Patch ACSD-57394 behebt das Problem, dass Produkte bei Verwendung mehrerer Sortierungsattribute in GraphQL falsch sortiert werden. Dieser Patch ist verfügbar, wenn <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 installiert ist. 
    </td>
    <td>Neuer Artikel </td>
    <td>30. Juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-57854-graphql-response-contains-disabled-categories-that-should-not-be-listed-in-the-category-aggregations">ACSD-57854: Die GraphQL-Antwort enthält deaktivierte Kategorien, die nicht in den Kategorieaggregationen aufgeführt werden sollten:</a> Der Patch ACSD-57854 behebt das Problem, dass die GraphQL-Antwort deaktivierte Kategorien enthält, die nicht in den Kategorieaggregationen aufgeführt werden sollten. Dieser Patch ist verfügbar, wenn <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 installiert ist. 
    </td>
    <td>Neuer Artikel </td>
    <td>30. Juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-47/acsd-57074-yes-no-custom-attribute-does-not-work-with-indexing">ACSD-57074: Ja/Kein benutzerdefiniertes Attribut mit dem Präfix <code>price_*</code> im Attribut <code>attribute_code</code> funktioniert nicht bei der Indizierung:</a> Der Patch ACSD-57074 behebt das Problem, dass das benutzerdefinierte Attribut <em>Ja/Nein</em> mit dem Präfix <code>price_*</code> im Attribut <code>attribute_code</code> nicht mit der Indizierung funktioniert. Dieser Patch ist verfügbar, wenn <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.47 installiert ist. 
    </td>
    <td>Neuer Artikel </td>
    <td>30. Juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-47/acsd-55241-used-and-times-used-attributes-display-incorrect-values-for-generated-coupons">ACSD-55241: Verwendete Attribute und Verwendete Zeiten zeigen falsche Werte für generierte Gutscheine an:</a> Der Patch ACSD-55241 behebt das Problem, dass die Attribute Verwendet und Verwendete Zeiten falsche Werte für generierte Gutscheine anzeigen. Dieser Patch ist verfügbar, wenn <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.47 installiert ist. 
    </td>
    <td>Neuer Artikel </td>
    <td>30. Juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-47/acsd-56760-admin-user-is-restricted-to-a-specific-website-and-is-unable-to-sort-or-add-new-products">ACSD-56760: Admin-Benutzer sind auf eine bestimmte Website beschränkt und können keine neuen Produkte sortieren oder hinzufügen:</a> Der Patch ACSD-56760 behebt das Problem, dass der Admin-Benutzer, der auf eine bestimmte Website beschränkt ist und keine neuen Produkte innerhalb einer Kategorie sortieren oder hinzufügen kann, falls der Webspeicher über eine eigene Stammkategorie verfügt. Dieser Patch ist verfügbar, wenn <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.47 installiert ist. 
    </td>
    <td>Neuer Artikel </td>
    <td>30. Juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-56635-imported-customers-are-duplicated-with-the-same-email-address">ACSD-56635: Importierte Kunden werden mit derselben E-Mail-Adresse dupliziert, wenn die Kontofreigabe auf Global eingestellt ist:</a> Der Patch ACSD-56635 behebt das Problem, dass der importierte Kunde mit derselben E-Mail-Adresse dupliziert wird, wenn der Import mit der Kontofreigabe auf Global verwendet wird. Dieser Patch ist verfügbar, wenn <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 installiert ist. 
    </td>
    <td>Neuer Artikel </td>
    <td>30. Juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-57315-new-transaction-created-in-paypal-payflow-pro-each-time-the-fetch-button-is-clicked">ACSD-57315: Jedes Mal, wenn auf die Abruf-Schaltfläche geklickt wird, wird in PayPal Payflow Pro eine neue Transaktion erstellt:</a> Der Patch ACSD-57315 behebt das Problem, dass in PayPal Payflow Pro jedes Mal, wenn auf die Abruf-Schaltfläche im Ansichtstransaktionsbildschirm in Admin geklickt wird, eine neue Transaktion erstellt wird. Dieser Patch ist verfügbar, wenn <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 installiert ist. 
    </td>
    <td>Neuer Artikel </td>
    <td>30. Juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-56741-database-setup-upgrade-error-with-custom-mysql-trigger">ACSD-56741: Fehlerbehebung bei Datenbanksetup-Fehlern mit benutzerdefinierten MySQL-Triggern:</a> Der Patch ACSD-56741 behebt das Problem, dass während <code>setup:upgrade</code> aufgrund eines benutzerspezifischen MySQL-Triggers in der Datenbank, der nicht mit der Indizierung und MView in Zusammenhang steht, eine Fehlermeldung angezeigt wird. . <em></em> Dieser Patch ist verfügbar, wenn <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 installiert ist. 
    </td>
    <td>Neuer Artikel </td>
    <td>30. Juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-58008-editing-the-end-date-as-empty-causes-the-schedule-update-to-disappear">ACSD-58008: Wenn das Enddatum leer ist, verschwindet das Zeitplanupdate:</a> Der Patch ACSD-58008 behebt das Problem, dass das Bearbeiten des Enddatums als leer führt, dass das Zeitplanupdate verschwindet. Dieser Patch ist verfügbar, wenn <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 installiert ist. 
    </td>
    <td>Neuer Artikel </td>
    <td>30. Juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-57337-admin-user-with-access-restrictions-can-see-companies">ACSD-57337: Admin-Benutzer mit Zugriffsbeschränkungen konnten alle Unternehmen im Unternehmensraster anzeigen:</a> Der Patch ACSD-57337 behebt das Problem, dass ein Admin-Benutzer mit Zugriffsbeschränkungen auf bestimmte Websites Unternehmen von allen Websites im Unternehmensraster anzeigen konnte. Dieser Patch ist verfügbar, wenn <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 installiert ist. 
    </td>
    <td>Neuer Artikel </td>
    <td>30. Juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/deployment/deployment-failed-with-correct-access-key-env-composer-auth">Die Bereitstellung schlägt mit den richtigen Zugriffsschlüsseln in <code>env:COMPOSER_AUTH</code> oder <code>auth.json</code> fehl:</a> Dieser Artikel bietet eine Lösung für das Problem, wenn Ihre Bereitstellung mit einem Fehler wie dem im Bereitstellungsprotokoll fehlschlägt. 
    </td>
    <td>Neuer Artikel </td>
    <td>30. Juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-bypass-waf-for-graphql-requests">Umgehen von WAF für GraphQL-Anforderungen:</a> In diesem Artikel wird erläutert, wie WAF für GraphQL-Anforderungen umgangen wird, wenn der Fastly WAF Ihre GraphQL-Anforderungen blockiert. 
    </td>
    <td>Neuer Artikel </td>
    <td>30. Juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/email-stating-that-export-storage-is-almost-full">E-Mail mit der Meldung, dass der Exportspeicher fast voll ist:</a> Dieser Artikel bietet eine Lösung für das Problem, dass Sie eine E-Mail erhalten, in der erklärt wird, dass der Exportspeicher fast voll ist. 
    </td>
    <td>Neuer Artikel </td>
    <td>30. Juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/upgrade-mariadb-10-4-to-10-5-for-magento-commerce-cloud">Aktualisieren von MariaDB 10.4 auf 10.5 für Adobe Commerce in Cloud:</a> In diesem Artikel wird beschrieben, wie Sie von MariaDB 10.4 auf 10.5 aktualisieren, um Adobe Commerce weiterhin in der Cloud-Infrastruktur zu verwenden. 
    </td>
    <td>Neuer Artikel </td>
    <td>30. Juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/revised-patches-for-google-maps-access-loss-on-all-adobe-commerce-versions">Überarbeitete Patches für Google Maps-Zugriffsverlust für alle Adobe Commerce-Versionen:</a> Dieser Artikel enthält eine Fehlerbehebung für Adobe Commerce-Händler, die nicht mit aktuellen Google Maps-Versionen ab 3.54 kompatibel sind. 
    </td>
    <td>Neuer Artikel </td>
    <td>30. Juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb24-40-revised-to-include-isolated-patch-for-cve-2024-34102">Sicherheitsupdate für Adobe Commerce - APSB24-40:</a> In diesem Artikel wird eine Aktualisierung im Zusammenhang mit CVE-2024-34102 beschrieben. 
    </td>
    <td>Neuer Artikel </td>
    <td>30. Juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/poor-performance-in-integration-environments">Schlechte Leistung in Integrationsumgebungen:</a> Dieser Artikel bietet eine Lösung für das Problem, dass die Pro-Integrationsumgebungen und Starter-Staging-Umgebungen nur schlecht funktionieren. 
    </td>
    <td>Neuer Artikel </td>
    <td>30. Juli 2024</td>
 </tr>
</table>

## Beliebte Artikel

* [Wechseln zu OpenSearch für Adobe Commerce in Cloud 2.4.4](/help/announcements/adobe-commerce-announcements/switching-to-opensearch-for-adobe-commerce-on-cloud-2-4-4.md)
* [Sicherheitslücke von Apache log4j2 in Adobe Commerce](/help/announcements/adobe-commerce-announcements/apache-log4j2-adobe-commerce.md)
* [Sicherheitsupdates für Adobe Commerce APSB22-12](/help/troubleshooting/known-issues-patches-attached/0-day-vulnerability-patch.md)
* [Identifizieren und Messen von Ausfällen für Adobe Commerce in der Cloud-Infrastruktur](/help/how-to/general/how-to-identify-outages.md)
* [Anzeigen der vCPU-Umgebungsebene in Ihrem Cluster auf Adobe Commerce](/help/how-to/general/check-vcpu-using-observation-for-adobe-commerce.md)
* [Adobe Commerce über Cloud-Infrastruktur: Berechnung der CPU-Zuordnung](/help/how-to/general/magento-commerce-cloud-cpu-allocation-calculation.md)
* [Adobe Commerce in der Cloud-Infrastruktur: Überprüfen der CPU-Konfiguration des Hosts](/help/how-to/general/magento-commerce-cloud-check-hosts-cpu-configuration.md)
