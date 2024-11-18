---
title: Wissensdatenbank zur Adobe Commerce-Unterstützung
description: Alles, was Sie für die Fehlerbehebung und Wartung Ihres Commerce-Stores benötigen.
exl-id: feacf38f-2803-4170-a64f-5d7c4567432d
feature: Support
role: Admin
source-git-commit: 52d07e5a5bb7be492f6799d0e5ad9fd49c3a61ae
workflow-type: tm+mt
source-wordcount: '1074'
ht-degree: 0%

---

# Wissensdatenbank zur Adobe Commerce-Unterstützung

>[!NOTE]
>
>Das Handbuch zur Wissensdatenbank des Adobe Commerce-Supports wird demnächst umstrukturiert und seine Inhalte werden an andere Stellen in Adobe Experience League verschoben. In der Zwischenzeit werden wir den Inhalt in diesem Handbuch weiterhin verwalten und aktualisieren.

![Knowledge Base-Homepage](../help/assets/knowledge-base-home-page-cover.jpg){width="100%"}

Die Informationen in dieser Wissensdatenbank ergänzen die [Adobe Commerce Developer Documentation](https://developer.adobe.com/commerce/docs), den [Adobe Commerce Merchant Guide](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html) und andere Adobe Commerce-Veröffentlichungen. Es behandelt Fehlerbehebung und Best Practices, hostet Ankündigungen und Antworten FAQs und hebt spezifische Szenarien hervor, die (aus irgendeinem Grund) nicht in der offiziellen Dokumentation erwähnt wurden.

## Was befindet sich in dieser Wissensdatenbank?

| KATEGORIE | BESCHREIBUNG |
| --- | --- |
| [Support-Tools](/help/support-tools/overview.md) | Verbessern Sie Ihre E-Commerce-Store-Erfahrung mit den verschiedenen Support-Tools von Adobe Commerce. Wir bieten personalisierte Best Practices, Diagnose- und Überwachungstools und die relevantesten Informationen über Ihre Site. |
| [Mitteilungen](/help/announcements/overview.md) | Hier erhalten Sie wichtige Updates von den Adobe Commerce-Teams. |
| [Fehlerbehebung](/help/troubleshooting/overview.md) | Erhalten Sie Self-Service-Lösungen und Patches vom Adobe Commerce-Supportteam. |
| [Benutzerhandbuch für das Help Center](/help/help-center-guide/help-center/magento-help-center-user-guide.md) | Erfahren Sie, wie Sie Ihre Support-Tickets verwalten, freigegebenen Zugriff gewähren und die Knowledge Base effektiv durchsuchen können. |
| [Gewusst wie-zu](/help/how-to/overview.md) | Hier erhalten Sie eine schrittweise Anleitung vom Adobe Commerce-Supportteam. |
| [FAQ](/help/faq/overview.md) | Hier finden Sie häufig gestellte Fragen zu Adobe Commerce-Richtlinien, -Strategien und -Besonderheiten zu Adobe Commerce-Funktionen. |

## Neue Funktionen

<table style="width:100%">
  <tr>
    <th style="width:70%">Beschreibung</th>
    <th style="width:15%">Typ</th>
    <th style="width:15%">Datum</th>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25234">Lizenzübertragung aufgrund einer Umstrukturierung:</a> Dieser Artikel hilft Ihnen, Ihr Adobe Commerce-Kontoeigentum einfach zu überarbeiten, einschließlich aller wichtigen Schritte, die erforderlich sind, um Ihre Dienste ohne Probleme laufen zu lassen.
    </td>
    <td>Neuer Artikel </td>
    <td>14. November 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25289">Für Adobe Commerce verfügbare Sicherheitsupdates (APSB24-90):</a> Am 12. November 2024 veröffentlichte Adobe ein Sicherheitsupdate für Adobe Commerce (in Cloud und On-Premise) und Magento Open Source-Funktionen, die von Commerce Services bereitgestellt und als SaaS (Software as a Service) bereitgestellt werden. Durch diese Aktualisierung wird eine <a href="https://helpx.adobe.com/security/severity-ratings.html">kritische</a> Schwachstelle behoben. 
    </td>
    <td>Neuer Artikel </td>
    <td>14. November 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25231">MageID-Kontoinhaber kann sich nicht anmelden und ein Support-Ticket senden:</a> Dieser Artikel behandelt das Adobe Commerce-Problem, bei dem Sie sich nicht bei Ihrem Konto (MageID) unter account.magento.com anmelden können, um ein Support-Ticket zu senden.
    </td>
    <td>Neuer Artikel </td>
    <td>14. November 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25135">OOTB-Braintree-Erweiterung für Adobe Commerce bietet keine Unterstützung für die neuesten Visa 3DS-Felder:</a> In diesem Artikel wird erläutert, wie die neuen Visa-Vorschriften eingehalten werden, da die vordefinierte Braintree-Erweiterung der Adobe Commerce die neuesten Visa 3DS-Felder nicht unterstützt.
    </td>
    <td>Neuer Artikel </td>
    <td>14. November 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-61528-retrieving-roles-using-graphql-returns-no-results">ACSD-61528: Beim Abrufen von Rollen mit GraphQL werden keine Ergebnisse zurückgegeben:</a> Der Patch ACSD-61528 behebt das Problem, bei dem beim Abrufen von Rollen vom Unternehmensadministrator mithilfe von GraphQL immer ein Nullergebnis zurückgegeben wird. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.53 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>14. November 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-48318-environment-emulation-nesting-error-in-system-log">ACSD-48318: Fehler bei der Verschachtelung der Umgebungsemulation in system.log:</a> Der Patch ACSD-48318 behebt das Problem, dass bei jedem Versand einer Rechnungsemail eine Fehlermeldung <em>main.ERROR:Environment Emulation nesting in <code>system.log</code> angezeigt wird. </em> Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.53 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>14. November 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-59366-delete-teams-with-deactivated-users-not-visible-in-the-team-list">ACSD-59366: Löschteams mit deaktivierten Benutzern, die nicht in der Teamliste angezeigt werden:</a> Der Patch ACSD-59366 behebt das Problem, dass ein Fehler auftritt, wenn Sie versuchen, ein Team zu löschen, das deaktivierte Benutzer enthält, die nicht in der Teamliste sichtbar sind. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.52 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>14. November 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60234-paypal-shows-an-incorrect-amount-when-discount-is-applied">ACSD-60234: PayPal zeigt bei Anwendung des Rabatts einen falschen Betrag an:</a> Der Patch ACSD-60234 behebt das Problem, dass [!DNL PayPal] einen falschen Betrag anzeigt, wenn der Rabatt über die Zahlungsmethode angewendet wird. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.51 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>14. November 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-60673-cart-price-rule-fix-for-multiple-payment-methods-at-checkout">ACSD-60673: Problem mit der Preisregel für Warenkorb behoben für mehrere Zahlungsmethoden beim Checkout:</a> Der Patch ACSD-60673 behebt das Problem, dass die Rabatte von einer [!UICONTROL Cart Price Rule], die eine Zahlungsmethode-Bedingung verwenden, nicht immer in den Gesamtsummen aufgeführt sind. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.52 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>14. November 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-60584-access-token-created-for-one-website-is-allowed-to-access-information-on-other-websites">ACSD-60584: Das Zugriffstoken, das für eine Website erstellt wurde, darf auf Informationen auf anderen Websites zugreifen:</a> Der Patch ACSD-60584 behebt das Problem, dass das Zugriffstoken, das für den Benutzer auf einer Website erstellt wurde, berechtigt ist, auf Kundeninformationen auf anderen Websites zuzugreifen oder diese zu ändern. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.53 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>14. November 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-60788-fixes-issue-where-custom-scripts-for-google-tag-manager-are-not-executed-due-to-content-security-policy-errors">ACSD-60788: Benutzerdefinierte Skripte für Google Tag Manager werden aufgrund von Fehlern in der Inhaltssicherheitsrichtlinie nicht ausgeführt:</a> Der Patch ACSD-60788 behebt das Problem, dass benutzerdefinierte Skripte für [!DNL Google Tag Manager] aufgrund von Fehlern in der Inhaltssicherheitsrichtlinie nicht ausgeführt werden. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.52 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>14. November 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-61366-setup-command-fails-with-error">ACSD-61366: Beim Befehl <code>bin/magento setup:static-content:deploy --jobs 4</code> treten mehrere Auftragsfehler mit einem Fehler auf:</a> Der Patch ACSD-61366 behebt das Problem, bei dem der Befehl <code>bin/magento setup:static-content:deploy --jobs 4</code> mehrere Auftragsfehler mit dem Fehler <em>Port muss innerhalb des Hostparameters</em> konfiguriert werden, obwohl der Port für die DB-Verbindung angegeben wurde. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.52 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>14. November 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60816-newrelic-browser-monitoring-scripts-injected-by-apm-agent-are-not-compliant-with-csp">ACSD-60816: Vom APM-Agenten eingeführte New Relic-Browserüberwachungsskripte sind nicht mit CSP konform:</a> Der Patch ACSD-60816 behebt das Problem, dass die vom APM-Agenten eingebrachten Browserüberwachungsskripte von [!DNL New Relic] nicht mit der Content Security Policy (CSP) konform sind. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.51 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>14. November 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-59952-error-on-deleting-shared-catalog-with-same-group-id-as-another-shared-catalog">ACSD-59952: Fehler beim Löschen des freigegebenen Katalogs mit derselben Gruppen-ID wie einem anderen freigegebenen Katalog:</a> Der Patch ACSD-59952 behebt den Fehler, der beim Löschen freigegebener Kataloge mit demselben <code>customer_group_id</code> als einem anderen freigegebenen Katalog ausgegeben wird. Außerdem werden Benutzer daran gehindert, solche freigegebenen Kataloge zu erstellen. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.52 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>14. November 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-59786-graphql-returns-an-error-when-fetching-a-quote-id-for-an-expired-quote">ACSD-59786: GraphQL gibt beim Abrufen eines <code>quote_id</code> für ein abgelaufenes Anführungszeichen einen Fehler zurück:</a> Der Patch ACSD-59786 behebt das Problem, bei dem eine GraphQL-Abfrage beim Abrufen eines <code>quote_id</code> für ein abgelaufenes Anführungszeichen einen Fehler zurückgibt. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.51 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>14. November 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-59967-javascript-error-prevents-google-maps-from-rendering-correctly">ACSD-59967: JavaScript-Fehler verhindert, dass Google Maps korrekt dargestellt werden:</a> Der Patch ACSD-59967 behebt das Problem, bei dem der JavaScript-Fehler verhindert, dass [!DNL Google Maps] korrekt dargestellt wird. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.51 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>14. November 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-59930-improves-performance-of-company-flows">ACSD-59930: Verbessert die Leistung der Unternehmensflüsse:</a> Der Patch ACSD-59930 behebt das Problem, dass beim Erstellen, Speichern oder Löschen eines Unternehmens mit einem Administrator mit 1000+ Adressen im Adressbuch ein Fehler vom Typ <em>Timeout</em> im Admin Panel angezeigt wird. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.53 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>14. November 2024</td>
  </tr>
</table>
