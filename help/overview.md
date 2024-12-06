---
title: Wissensdatenbank zur Adobe Commerce-Unterstützung
description: Alles, was Sie für die Fehlerbehebung und Wartung Ihres Commerce-Stores benötigen.
exl-id: feacf38f-2803-4170-a64f-5d7c4567432d
feature: Support
role: Admin
source-git-commit: 6d22ea4725249df1528625672be405464b1411e8
workflow-type: tm+mt
source-wordcount: '920'
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
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25301">Beheben Sie [!DNL New Relic] Agentenprobleme bei der Aktualisierung von PHP 8.2 auf 8.3 in Adobe Commerce:</a> Wenn Sie PHP von Version 8.2 auf 8.3 aktualisieren, werden Sie möglicherweise feststellen, dass der [!DNL New Relic]-Agent in Ihrer Adobe Commerce-Umgebung nicht mehr funktioniert. Dieses Problem wurde in Staging- und Produktionsumgebungen beobachtet. In diesem Artikel finden Sie Schritte zur Fehlerbehebung und Lösung dieses Problems.
    </td>
    <td>Neuer Artikel </td>
    <td>5. Dezember 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25321">[!DNL Security Scan Tool] gibt "APSByy-xx-Sicherheitsupdates verfügbar"zurück, selbst wenn der Patch bereits angewendet wurde:</a> Die [!DNL Security Scan Tool] meldet für Adobe Commerce und Magento Open Source verfügbare APSByy-xx-Sicherheitsaktualisierungen, obwohl Sie den Patch bereits angewendet haben. Sie können diese Benachrichtigung ignorieren.
    </td>
    <td>Neuer Artikel </td>
    <td>5. Dezember 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-54/acsd-61845-error-occurs-for-requests-with-text-html-accept-header">ACSD-61845: Fehler tritt bei Anfragen mit text/html accept header auf:</a> Der Patch ACSD-61845 behebt das Problem, dass eine HTTP-Anfrage mit nur einem Text/html accept-Header aufgrund von Diskrepanzen beim Medientyp bei der Reaktionsverarbeitung einen 500-Fehler verursacht. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.54 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>5. Dezember 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-54/acsd-61200-fixes-discount-tax-compensation-in-sales-total-calculations">ACSD-61200: Falsche Rabattsteuervergütung bei Berechnungen der Verkaufssumme:</a> Der Patch ACSD-61200 behebt das Problem, dass bei Berechnungen von Gesamtbetrag und Gesamtbetrag der tatsächlich gezahlten Discount-Steuervergünstigungen Discount- und Versandrabatt-Steuervergünstigungen fehlen, was zu Diskrepanzen zwischen den Daten des Verkaufsauftrags und des Gutscheinberichts führt. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.54 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>5. Dezember 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-54/acsd-61199-cms-page-hierarchy-tab-doesnt-display-proper-tree-structure">ACSD-61199: Die Registerkarte [!UICONTROL Hierarchy] der CMS-Seite zeigt keine ordnungsgemäße Baumstruktur an:</a> Der Patch ACSD-61199 behebt das Problem, dass die Registerkarte [!UICONTROL Hierarchy] der CMS-Seite beim Bearbeiten einer CMS-Seite mit einer vorhandenen Hierarchie keine ordnungsgemäße Baumstruktur anzeigt. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.54 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>5. Dezember 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-60804-editing-customer-linked-to-deleted-company-causes-error">ACSD-60804: Das Bearbeiten eines Kunden, der einem gelöschten Unternehmen zugeordnet ist, führt zu einem Fehler:</a> Der Patch ACSD-60804 behebt das Problem, bei dem das Bearbeiten eines mit einem gelöschten Unternehmen verknüpften Kunden einen Fehler verursacht, <em>Aufruf an die Mitgliederfunktion getSuperUserId() auf null</em>. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.53 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>5. Dezember 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-54/acsd-61522-email-in-name-fields-sends-invalid-order-confirmations">ACSD-61522: E-Mail-Adressen in den Feldern [!UICONTROL First] und [!UICONTROL Last Name] senden ungültige Bestellbestätigungen:</a> Der Patch ACSD-61522 behebt das Problem, dass E-Mail-Adressen in die Felder [!UICONTROL First Name] und [!UICONTROL Last Name] eines Gastkunden eingegeben werden können, wodurch ungültige Bestellbestätigungs-E-Mails gesendet werden. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.54 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>5. Dezember 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-54/acsd-62485-async-operations-all-consumer-stops-working-when-company-is-created">ACSD-62485: <code>async.operations.all</code> Der Verbraucher funktioniert nicht mehr, wenn das Unternehmen erstellt wird:</a> Der Patch ACSD-62485 behebt das Problem, dass der <code>async.operations.all</code> -Verbraucher bei der Erstellung eines B2B-Unternehmens nicht mehr arbeitet. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.54 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>5. Dezember 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-60684-graphql-product-sorting-by-multiple-fields-does-not-work-as-expected">ACSD-60684: GraphQL-Produktsortierung nach mehreren Feldern funktioniert nicht wie erwartet:</a> Der Patch ACSD-60684 behebt das Problem, dass die GraphQL-Produktsortierung nach mehreren Feldern nicht funktioniert, wenn die Sortierung in Variablen übergeben wird. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.52 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>5. Dezember 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-61553-cart-price-rule-discounts-are-incorrectly-calculated-when-multiple-discounts-with-different-priorities-are-applied">ACSD-61553: [!UICONTROL Cart Price Rule] wird falsch berechnet, wenn mehrere Rabatte mit unterschiedlichen Prioritäten angewendet werden:</a> Der Patch ACSD-61553 behebt das Problem, dass der [!UICONTROL Cart Price Rule] falsch berechnet wird, wenn mehrere Rabatte mit unterschiedlichen Prioritäten angewendet werden. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.53 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>5. Dezember 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-58383-duplicate-credit-memos-from-simultaneous-refund-requests-via-rest-api">Patch ACSD-58383 Adobe Commerce: Duplizierte Kreditkarten aus gleichzeitigen Erstattungsanträgen über REST API:</a> Der Patch ACSD-58383 behebt das Problem, dass die Ausgabe einer Rückerstattung über die REST-API mit zwei identischen Anfragen, die gleichzeitig ausgeführt werden, zu doppelten Kreditmemos führt. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.55 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>5. Dezember 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-58471-dynamic-content-fails-load-product-detail-page">ACSD-58471: Dynamische Inhalte werden nicht auf der Produktdetailseite geladen, wenn die zugehörigen Katalogpreisregeln geplant wurden:</a> Der Patch ACSD-58471 behebt das Problem, dass dynamische Inhalte nicht auf der Produktdetailseite geladen werden, wenn die zugehörigen Katalogpreisregeln geplant wurden. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.55 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>5. Dezember 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-58735-restricted-admin-cant-view-abandoned-shopping-carts">ACSD-58735: Eingeschränkte Administratoren können verlassene Warenkörbe nicht im Kundenkonto für zugehörige Websites anzeigen:</a> Der Patch ACSD-58735 behebt das Problem, dass ein Administrator mit eingeschränkter Rolle nicht in der Lage ist, die Warenkörbe verlassener Kunden über die Registerkarte <strong>[!UICONTROL Commerce Admin]</strong> &gt; <strong>[!UICONTROL Reports]</strong> &gt; <strong>[!UICONTROL Abandoned Carts]</strong> &gt; <strong>[!UICONTROL Select Cart]</strong> &gt; <strong>[!UICONTROL Shopping Cart]</strong> anzuzeigen. . Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.55 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>5. Dezember 2024</td>
  </tr>
</table>
