---
title: Wissensdatenbank zur Adobe Commerce-Unterstützung
description: Alles, was Sie für die Fehlerbehebung und Wartung Ihres Commerce-Stores benötigen.
exl-id: feacf38f-2803-4170-a64f-5d7c4567432d
feature: Support
role: Admin
source-git-commit: 607b835da518536196654734f62d78d095099476
workflow-type: tm+mt
source-wordcount: '1615'
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
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25075">Das Sicherheitsscan-Tool gibt "Kann nicht bestimmen, ob Ihr Server 2FA verwendet":</a> Um den Fehler zu beheben, überprüfen Sie, ob das <code>Magento_TwoFactorAuth</code>-Modul deaktiviert wurde. Um die Prüfung zu bestehen, sollte sie im Allgemeinen aktiviert sein.
    </td>
    <td>Neuer Artikel </td>
    <td>17. Oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60632-address-saved-on-every-order-attempt">ACSD-60632: Bei jedem Bestellversuch gespeicherte Adresse:</a> Der Patch ACSD-60632 behebt das Problem, dass bei jedem Bestellplatzierungsversuch eine neue Adresse gespeichert wird, unabhängig davon, ob die Bestellung erfolgreich erstellt wurde oder nicht. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.51 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>17. Oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60326-graphql-query-error-customer-return-status">ACSD-60326: GraphQL-Abfrage zum Status der Kundenrückgabe gibt einen Fehler zurück:</a> Der Patch ACSD-60326 behebt das Problem, dass in der GraphQL-Abfrage nach dem Status der Kundenrückgabe ein Fehler auftritt. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.51 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>17. Oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-59925-sorting-items-in-media-gallery">ACSD-59925: Sortieren von Elementen in der Media Gallery nach Position in GraphQL:</a> Der Patch ACSD-59925 behebt das Problem, dass Elemente in der Media Gallery nicht nach Position sortiert werden, was zu einer falschen Anzeigereihenfolge führt. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.52 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>17. Oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-61322-products-not-assigned-to-shared-catalogue">ACSD-61322: Produkte, die nicht dem freigegebenen Katalog zugewiesen sind, sind in der XML-Sitemap enthalten:</a> Der Patch ACSD-61322 behebt das Problem, dass Produkte/Kategorien, die nicht dem freigegebenen Katalog für die Standardgruppe (Allgemein) zugewiesen sind, weiterhin in der XML-Sitemap enthalten sind. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.52 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>17. Oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-60590-optimized-bestseller-report-generation">ACSD-60590: Verbesserte Leistung der aggregierten täglichen Bestsellers-Berichtserstellung:</a> Der Patch ACSD-60590 behebt das Problem, dass der aggregierte tägliche Bestseller-Bericht für eine große Menge von aufgegebenen Bestellungen viel Zeit in Anspruch nimmt. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.52 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>17. Oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-59865-cart-price-rule-fix-for-insufficient-quantity-issue">ACSD-59865: Die Preisregel für Warenkorb kann vorherige Regeln aufgrund unzureichender Produktmenge nicht aufheben:</a> Der Patch ACSD-59865 behebt das Problem, bei dem der Wert <em>Mengenrabatt-Schritt</em> in <em>Fester Rabatt für Betrag</em>, <em>Prozent des Produktpreises</em> und <em>Kaufen Y</em>} Preisregeln für Warenkorb brechen die Aktion früherer Regeln nicht mehr ab. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.52 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>17. Oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/error-when-filtering-orders-in-admin">Fehler beim Filtern von Bestellungen in Admin:</a> Dieser Artikel enthält einen Patch für das Adobe Commerce-Problem, bei dem beim Versuch, Bestellungen im Admin nach Datum zu filtern, ein Fehler auftritt, der die Meldung <em>Verletzung der Integritätsbeschränkung: Spalte 'created_at', wobei die Klausel mehrdeutig ist</em>.
    </td>
    <td>Neuer Artikel </td>
    <td>17. Oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25030">Adobe Commerce: Inline-JavaScript-Probleme auf der Checkout-Seite im eingeschränkten Modus der Content Security Policy (CSP):</a> Dieser Artikel enthält detaillierte Erklärungen und Lösungen für Probleme, die bei über Adobe Commerce Admin und Google Tag Manager in Adobe Commerce 2.4.7 hinzugefügten benutzerdefinierten JavaScript beim Checkout auftreten, wenn der eingeschränkte Modus <strong>CSP</strong> aktiviert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>17. Oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-61195-empty-cart-on-final-graphql-page">ACSD-61195: GraphQL-Anfrage zum Warenkorb gibt keine Artikel auf der endgültigen Seite zurück:</a> Der Patch ACSD-61195 behebt das Problem, dass auf der letzten Seite der GraphQL-Anfrage zum Warenkorb keine Artikel zum Warenkorb zurückgegeben werden. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.51 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>17. Oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-50/acsd-59514-forms-in-admin-with-page-builder-throw-error-in-browser-console">ACSD-59514: Forms in Admin mit Page Builder gibt in der Browser-Konsole einen Fehler aus:</a> Der Patch ACSD-59514 behebt das Problem, dass die Formulare in Admin mit Page Builder den Fehler <em>Page Builder 5 Sekunden lang gerendert haben, ohne Sperren zu lösen</em> in der Browser-Konsole, nachdem das Formular gesendet wurde. Änderungen können nicht gespeichert werden. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.50 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>17. Oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60538-if-product-is-disabled-attributes-dont-show">ACSD-60538: Attribute werden nicht korrekt angezeigt, wenn das Produkt in <em>Alle Store-Ansichten</em> deaktiviert ist:</a> Der Patch ACSD-60538 behebt das Problem, dass, wenn ein Produkt in <em>Alle Store-Ansichten</em> deaktiviert und nur in bestimmten Speicheransichtsbereichen aktiviert ist, die Produktattribute in der GraphQL-Antwort nicht korrekt angezeigt werden. dazu führen, dass das Produkt nicht richtig angezeigt wird. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.51 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>17. Oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-50/acsd-58352-return-attribute-labels-for-the-default-store-are-returned-via-graphql-api">ACSD-58352: Rückgabeattributbeschriftungen für den Standardspeicher werden über die GraphQL-API zurückgegeben:</a> Der Patch ACSD-58352 behebt das Problem, dass Rückgabeattributbeschriftungen für den Standardspeicher über die GraphQL-API zurückgegeben werden, wenn eine nicht standardmäßige Store-Ansicht im Anfrageheader angegeben ist. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.50 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>17. Oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href = "https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-24983">Das Dropdown-Menü <em>Konten wechseln</em> fehlt in Ihrem Konto:</a> Dieser Artikel bietet eine Lösung für das Adobe Commerce-Problem, bei dem das Dropdown-Menü <em>Konten wechseln</em> in Ihrem Konto fehlt und Sie den Zugriff auf Tickets für den Händler verloren haben.
    </td>
    <td>Neuer Artikel</td>
    <td>17. Oktober 2024</td>
  </tr>

<tr>  
    <td>
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/acsd-56979-product-images-removed-after-staging-update-deleted">ACSD-56979: Produktbilder, die nach dem Löschen des Staging-Updates entfernt wurden:</a> Der Patch ACSD-56979 behebt das Problem, dass Produktbilder nach dem Löschen eines Staging-Updates entfernt werden. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.49 installiert ist.  
    </td>
    <td>Neuer Artikel</td>
    <td>17. Oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-48210-store-view-specific-scope-attribute-overrides-global-values">ACSD-48210: Store view specific scope attributes override global values:</a> Der Patch ACSD-48210 behebt das Problem, bei dem beim Aktualisieren eines <em>Website Scope</em> -Attributs in einer bestimmten Store-Ansicht die Attributwerte im globalen Gültigkeitsbereich außer Kraft gesetzt werden. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.50 installiert ist. 
    </td>
    <td>Neuer Artikel </td>
    <td>17. Oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-59280-fix-for-reflection-union-type-error">ACSD-59280: ReflectionUnionType::getName() -Fehler in 2.4.4-pX-Installationen:</a> Der Patch ACSD-59280 behebt das Problem, bei dem der Aufruf der nicht definierten Methode <code>ReflectionUnionType::getName()</code> während der Installation von 2.4.4-pX-Versionen auftritt. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.50 installiert ist. 
    </td>
    <td>Neuer Artikel </td>
    <td>17. Oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-54887-customer-shopping-cart-gets-cleared-after-session-expiry">ACSD-54887: Der Einkaufswagen des Kunden wird gelöscht, nachdem die Kundensitzung abgelaufen ist:</a> Der Patch ACSD-54887 behebt das Problem, dass der Einkaufswagen des Kunden gelöscht wird, nachdem die Kundensitzung abgelaufen ist und <em>Warenkorb für beständige Artikel</em> aktiviert ist. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.50 installiert ist. 
    </td>
    <td>Neuer Artikel </td>
    <td>17. Oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-60303-admin-order-placement-fix">ACSD-60303: Problem bei der Platzierung von Administratorbestellungen behoben, das durch die aktivierte HTML-Minimierung behoben wurde:</a> Der Patch ACSD-60303 behebt das Problem, dass eine Bestellung von Admin nicht platziert werden kann, wenn die HTML-Minimierung aktiviert ist. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.50 installiert ist. 
    </td>
    <td>Neuer Artikel </td>
    <td>17. Oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/acsd-57045-url-rewrites-cause-infinite-page-looping-after-website-root-unchecked-hierarchy">ACSD-57045: URL-Neuschreibungen führen zu unbegrenzter Seitenschleife, nachdem der <em>Website-Stamm</em> aus der Hierarchie deaktiviert wurde:</a> Der Patch ACSD-57045 behebt das Problem, dass URL-Neuschreibungen dazu führen, dass unendliche Seiten nach dem Deaktivieren von <em>Website-Stamm</em> aus der Hierarchie gelöscht werden. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.49 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>17. Oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/ascd-58446-deleting-a-team-with-child-users-or-teams-via-graphql-gives-an-uninformative-error-message">ACSD-58446: Durch das Löschen eines Teams mit untergeordneten Benutzern oder Teams über GraphQL erhalten Sie eine informative Fehlermeldung:</a> Der Patch ACSD-58446 behebt das Adobe Commerce-Problem, bei dem beim Löschen eines Teams mit untergeordneten Benutzern oder Teams über GraphQL eine nicht informative Fehlermeldung zurückgegeben wird, die mit der Benutzeroberfläche unvereinbar ist. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.49 installiert ist. 
    </td>
    <td>Neuer Artikel </td>
    <td>17. Oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/acsd-58375-wrong-youtube-api-key-configuration-causes-an-error-when-adding-a-youtube-video-at-the-store-view-level">ACSD-58735: Falsch konfigurierter YouTube-API-Schlüssel verursacht Fehler beim Hinzufügen von Videos auf Store-Ansichtsebene:</a> Der Patch ACSD-58735 behebt das Problem, bei dem die falsche YouTube API-Schlüsselkonfiguration beim Hinzufügen eines YouTube-Videos auf der Store-Ansichtsebene einen Fehler verursacht. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.49 installiert ist. 
    </td>
    <td>Neuer Artikel </td>
    <td>17. Oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/acsd-57086-orders-placed-from-non-default-websites-with-terms-conditions-processed-incorrectly">ACSD-57086: Bestellungen von nicht standardmäßigen Websites mit aktivierten Geschäftsbedingungen werden falsch verarbeitet:</a> Der Patch ACSD-57086 behebt das Problem, dass Bestellungen von nicht standardmäßigen Websites mit aktivierten Geschäftsbedingungen nicht korrekt verarbeitet werden. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.49 installiert ist. 
    </td>
    <td>Neuer Artikel </td>
    <td>17. Oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-58141-phpsessid-regenerates-on-post-requests-for-logged-in-customers-with-l2-redis-cache-enabled">ACSD-58141: PHPSESSID generiert bei POST-Anfragen für angemeldete Kunden neu, wenn der L2 Redis-Cache aktiviert ist:</a> Der Patch ACSD-58141 behebt das Problem, dass PHPSESSID bei POST-Anfragen für einen angemeldeten  neu generiert wird, wenn der L2-Redis-Cache aktiviert ist und der Kunde von Admin aktualisiert wird min. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.50 installiert ist. 
    </td>
    <td>Neuer Artikel </td>
    <td>17. Oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-58790-fixes-pinch-to-zoom-functionality-on-the-product-detail-page-images-in-mobile-view-on-chrome">ACSD-58790: Behebt die Pinch-to-Zoom-Funktionalität für die Produktdetailseiten-Bilder in der Mobile-Ansicht in Chrome:</a> Der Patch ACSD-58790 behebt das Adobe Commerce-Problem, bei dem das Bild in der Mobile-Ansicht in Chrome nicht wie erwartet vergrößert wurde. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.50 installiert ist. 
    </td>
    <td>Neuer Artikel </td>
    <td>17. Oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-58442-fixes-issue-devices-768px-mobile-view-instead-desktop">ACSD-58442: Behebung des Problems, bei dem Geräte mit 768 px Breite als Mobilgeräte behandelt wurden, wodurch Menü und Kopfzeile in der Mobile-Ansicht statt Desktop geladen wurden.</a> Der Patch ACSD-58442 behebt das Adobe Commerce-Problem, bei dem Geräte mit einer Breite von 768 px als Mobilgeräte behandelt werden, wodurch das Menü und die Kopfzeile in einer mobilen Ansicht geladen wird einen Desktop. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.50 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>17. Oktober 2024</td>
  </tr>
</table>
