---
title: Adobe Commerce Support-Wissensdatenbank
description: Alles, was Sie für die Fehlerbehebung und Wartung Ihres Commerce-Stores wissen müssen.
exl-id: feacf38f-2803-4170-a64f-5d7c4567432d
feature: Support
role: Admin
source-git-commit: 6d22ea4725249df1528625672be405464b1411e8
workflow-type: tm+mt
source-wordcount: '920'
ht-degree: 0%

---

# Adobe Commerce Support-Wissensdatenbank

>[!NOTE]
>
>Das Handbuch zur Adobe Commerce Support-Wissensdatenbank wird bald umstrukturiert und die darin enthaltenen Inhalte werden an andere Stellen in Adobe Experience League verschoben. In der Zwischenzeit werden wir den Inhalt in diesem Handbuch weiter pflegen und aktualisieren.

![Homepage der Wissensdatenbank](../help/assets/knowledge-base-home-page-cover.jpg){width="100%"}

Die Informationen in dieser Wissensdatenbank ergänzen die [Adobe Commerce-Entwicklerdokumentation](https://developer.adobe.com/commerce/docs) und das [Adobe Commerce-Händlerhandbuch](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html) sowie andere Adobe Commerce-Publikationen. Es behandelt Fehlerbehebung und Best Practices, enthält Ankündigungen, beantwortet häufig gestellte Fragen und zeigt bestimmte Szenarien auf, die (aus welchen Gründen auch immer) in der offiziellen Dokumentation nicht erwähnt wurden.

## Was befindet sich in dieser Wissensdatenbank?

| KATEGORIE | BESCHREIBUNG |
| --- | --- |
| [Support-Tools](/help/support-tools/overview.md) | Verbessern Sie Ihr E-Commerce-Store-Erlebnis mit den verschiedenen Support-Tools, die von Adobe Commerce bereitgestellt werden. Wir bieten personalisierte Best Practices, Diagnose- und Überwachungs-Tools sowie die relevantesten Informationen zu Ihrer Site. |
| [Ankündigungen](/help/announcements/overview.md) | Hier erhalten Sie wichtige Updates von den Adobe Commerce-Teams. |
| [Fehlerbehebung](/help/troubleshooting/overview.md) | Holen Sie sich Self-Service-Lösungen und Patches vom Adobe Commerce Support-Team. |
| [Hilfe-Center-Benutzerhandbuch](/help/help-center-guide/help-center/magento-help-center-user-guide.md) | Erfahren Sie, wie Sie Ihre Support-Tickets verwalten, gemeinsamen Zugriff gewähren und die Wissensdatenbank effektiv durchsuchen können. |
| [Anleitung](/help/how-to/overview.md) | Erhalten Sie vom Adobe Commerce-Supportteam Schritt für Schritt klare Anweisungen. |
| [FAQ](/help/faq/overview.md) | Hier finden Sie häufig gestellte Fragen zu Adobe Commerce-Richtlinien, -Strategien und -Besonderheiten in Bezug auf Adobe Commerce-Funktionen. |

## Neue Funktionen

<table style="width:100%">
  <tr>
    <th style="width:70%">Beschreibung</th>
    <th style="width:15%">Typ</th>
    <th style="width:15%">Datum</th>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25301">Beheben Sie [!DNL New Relic] Agentenprobleme mit der Aktualisierung von PHP 8.2 auf 8.3 in Adobe Commerce:</a> Wenn Sie PHP von Version 8.2 auf 8.3 aktualisieren, werden Sie möglicherweise feststellen, dass der [!DNL New Relic]-Agent in Ihrer Adobe Commerce-Umgebung nicht mehr funktioniert. Dieses Problem wurde in Staging- und Produktionsumgebungen beobachtet. In diesem Artikel finden Sie Schritte zur Fehlerbehebung und Lösung dieses Problems.
    </td>
    <td>Neuer Artikel </td>
    <td>5. Dezember 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25321">[!DNL Security Scan Tool] gibt „APSByy-xx-Sicherheitsupdates verfügbar“ zurück, auch wenn der Patch bereits angewendet wurde:</a> Das [!DNL Security Scan Tool] meldet APSByy-xx-Sicherheitsupdates, die für Adobe Commerce und Magento Open Source verfügbar sind, auch wenn Sie den Patch bereits angewendet haben. Sie können diese Benachrichtigung ignorieren.
    </td>
    <td>Neuer Artikel </td>
    <td>5. Dezember 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-54/acsd-61845-error-occurs-for-requests-with-text-html-accept-header">ACSD-61845: Fehler tritt bei Anfragen mit text/html Accept-Header auf:</a> Der Patch von ACSD-61845 behebt das Problem, dass eine HTTP-Anfrage mit nur einer text/html Accept-Header einen 500-Fehler verursacht, da der Medientyp bei der Antwortverarbeitung nicht übereinstimmt. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.54 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>5. Dezember 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-54/acsd-61200-fixes-discount-tax-compensation-in-sales-total-calculations">ACSD-61200: Falsche Rabattsteuervergütung in Berechnungen der Verkaufssumme: </a> Der Patch „ACSD-61200“ behebt das Problem, dass der Rabattsteuervergütungsbetrag und der Versandrabatt-Steuervergütungsbetrag in den Berechnungen „Gesamtbetrag“ und „Gesamtbetrag - Ist“ fehlen, was zu Diskrepanzen zwischen den Daten des Kundenauftrags und der Couponberichterstellung führt. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.54 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>5. Dezember 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-54/acsd-61199-cms-page-hierarchy-tab-doesnt-display-proper-tree-structure">ACSD-61199: Auf der Registerkarte "[!UICONTROL Hierarchy]" der CMS-Seite wird keine ordnungsgemäße Baumstruktur angezeigt:</a> Der Patch „ACSD-61199“ behebt das Problem, dass auf der Registerkarte "[!UICONTROL Hierarchy]" der CMS-Seite beim Bearbeiten einer CMS-Seite mit einer bestehenden Hierarchie keine ordnungsgemäße Baumstruktur angezeigt wird. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.54 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>5. Dezember 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-60804-editing-customer-linked-to-deleted-company-causes-error">ACSD-60804: Das Bearbeiten eines Kunden, der mit einer gelöschten Firma verknüpft ist, führt zu einem Fehler:</a> Der Patch „ACSD-60804“ behebt das Problem, dass das Bearbeiten eines Kunden, der mit einer gelöschten Firma verknüpft ist, einen Fehler verursacht <em>Aufruf einer Memberfunktion getSuperUserId() auf null</em>. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.53 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>5. Dezember 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-54/acsd-61522-email-in-name-fields-sends-invalid-order-confirmations">ACSD-61522: E-Mail-Adressen in den Feldern [!UICONTROL First] und [!UICONTROL Last Name] senden ungültige Bestellbestätigungen:</a> Der Patch ACSD-61522 behebt das Problem, dass E-Mail-Adressen in die Felder [!UICONTROL First Name] und [!UICONTROL Last Name] eines Gastkunden eingegeben werden können, was dazu führt, dass ungültige Bestellbestätigungs-E-Mails gesendet werden. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.54 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>5. Dezember 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-54/acsd-62485-async-operations-all-consumer-stops-working-when-company-is-created">ACSD-62485: <code>async.operations.all</code> Verbraucher funktioniert nicht mehr, wenn ein Unternehmen erstellt wird:</a> Mit dem Patch „ACSD-62485“ wird das Problem behoben, dass der <code>async.operations.all</code> Verbraucher nicht mehr funktioniert, wenn ein B2B-Unternehmen erstellt wird. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.54 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>5. Dezember 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-60684-graphql-product-sorting-by-multiple-fields-does-not-work-as-expected">ACSD-60684: Die Sortierung von GraphQL-Produkten nach mehreren Feldern funktioniert nicht wie erwartet:</a> Der Patch von ACSD-60684 behebt das Problem, dass die Sortierung von GraphQL-Produkten nach mehreren Feldern nicht funktioniert, wenn die Sortierung in Variablen übergeben wird. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.52 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>5. Dezember 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-61553-cart-price-rule-discounts-are-incorrectly-calculated-when-multiple-discounts-with-different-priorities-are-applied">ACSD-61553: [!UICONTROL Cart Price Rule] wird falsch berechnet, wenn mehrere Rabatte mit unterschiedlichen Prioritäten angewendet werden:</a> Das Patch „ACSD-61553“ behebt das Problem, dass der [!UICONTROL Cart Price Rule] falsch berechnet wird, wenn mehrere Rabatte mit unterschiedlichen Prioritäten angewendet werden. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.53 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>5. Dezember 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-58383-duplicate-credit-memos-from-simultaneous-refund-requests-via-rest-api">ACSD-58383 Adobe Commerce-Patch: Doppelte Gutschriften aus gleichzeitigen Erstattungsanfragen über die REST-API:</a> Der ACSD-58383-Patch behebt das Problem, dass die Ausstellung einer Erstattung über die REST-API mit zwei identischen Anfragen, die gleichzeitig ausgeführt werden, zu doppelten Gutschriften führt. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.55 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>5. Dezember 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-58471-dynamic-content-fails-load-product-detail-page">ACSD-58471: Dynamische Inhalte können nicht auf der Produktdetailseite geladen werden, wenn die zugehörigen Katalogpreisregeln geplant wurden:</a> Der Patch „ACSD-58471“ löst das Problem, dass dynamische Inhalte nicht auf der Produktdetailseite geladen werden, wenn die zugehörigen Katalogpreisregeln geplant wurden. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.55 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>5. Dezember 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-58735-restricted-admin-cant-view-abandoned-shopping-carts">ACSD-58735: Ein eingeschränkter Administrator kann abgebrochene Warenkörbe nicht im Kundenkonto der zugehörigen Website anzeigen:</a> Mit dem Patch „ACSD-58735“ wird das Problem behoben, dass ein Admin-Benutzer mit eingeschränkter Rolle die Warenkörbe von abgebrochenen Kunden nicht über die Registerkarte <strong>[!UICONTROL Commerce Admin]</strong> &gt; <strong>[!UICONTROL Reports]</strong> &gt; <strong>[!UICONTROL Abandoned Carts]</strong> &gt; <strong>[!UICONTROL Select Cart]</strong> &gt; <strong>[!UICONTROL Shopping Cart]</strong> anzeigen kann. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.55 installiert ist.
    </td>
    <td>Neuer Artikel </td>
    <td>5. Dezember 2024</td>
  </tr>
</table>
