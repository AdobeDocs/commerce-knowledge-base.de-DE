---
title: Wissensdatenbank zur Adobe Commerce-Unterstützung
description: Alles, was Sie für die Fehlerbehebung und Wartung Ihres Commerce-Stores benötigen.
exl-id: feacf38f-2803-4170-a64f-5d7c4567432d
feature: Support
role: Admin
source-git-commit: 95509b717d41436b68ad94c3c28ac72e1887fdfc
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 1%

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
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-update-the-cloud-account-profile">Aktualisierung des Cloud-Kontoprofils:</a> Dieser Artikel enthält Anweisungen zum Ändern des Profils im Cloud-Konto.
    </td>
    <td>Neuer Artikel</td>
    <td>22. April 2024</td>
  </tr>

<td>
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/payments/admin-create-order-page-in-csp-restricted-mode">Fehlerbehebung beim Erstellen einer Bestellseite im eingeschränkten CSP-Modus:</a> Dieser Artikel enthält Erklärungen und Fehlerbehebungen für die Probleme mit Adobe Commerce 2.4.7 beim Erstellen einer Bestellung auf der Admin-Seite, wenn der eingeschränkte CSP-Modus <em>Aktiviert</em> ist.  
    </td>
    <td>Neuer Artikel</td>
    <td>22. April 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/payments/storefront-checkout-page-in-csp-restricted-mode">Fehlerbehebung für die Storefront-Checkout-Seite im eingeschränkten CSP-Modus:</a> Dieser Artikel enthält Erklärungen und Fehlerbehebungen für die Adobe Commerce 2.4.7-Probleme beim Anzeigen der Checkout-Seite im eingeschränkten CSP-Modus, wobei die Fehlermeldung <em>"Inline-Skript nicht ausführen kann, da sie gegen die folgende Content Security Policy-Anweisung verstößt: "script-src ...."</em> 
    </td>
    <td>Neuer Artikel </td>
    <td>22. April 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-46/acsd-54656-invisible-recaptcha-fails-during-checkout-preventing-order-placement">ACSD-54656: Unsichtbares reCAPTCHA funktioniert beim Checkout nicht, was die Bestellplatzierung verhindert:</a> Der Patch ACSD-54656 behebt das Problem, dass das unsichtbare reCAPTCHA beim Checkout nicht ordnungsgemäß funktioniert, was die Platzierung einer Bestellung verhindert. Dieser Patch ist verfügbar, wenn <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.46 installiert ist. 
    </td>
    <td>Neuer Artikel </td>
    <td>22. April 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-46/acsd-46767-category-page-caches-invalidate-when-the-stock-quantity-changes">ACSD-46767: Die Kategorieseite speichert das Invalidierungs-Datum, wenn sich die Bestandsmenge ändert:</a> Der Patch ACSD-46767 behebt das Problem, dass die Kategorieseite die Invalidierung zwischenspeichert, wenn sich die Bestandsmenge ändert, auch wenn das Produkt noch auf Lager ist. Dieser Patch ist verfügbar, wenn <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.46 installiert ist.  
    </td>
    <td>Neuer Artikel </td>
    <td>22. April 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-45/acsd-56415-performance-of-partial-price-indexing-is-slowed-down-due-to-a-delete-query">ACSD-56415: Die partielle Preisindizierung wird aufgrund der DELETE-Abfrage verlangsamt:</a> Der Patch ACSD-56415 behebt das Problem, dass die partielle Preisindizierung aufgrund einer DELETE-Abfrage verlangsamt wird, wenn die -Datenbank über einen großen Teil des Preisdatenindex verfügt. Dieser Patch ist verfügbar, wenn <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.45 installiert ist.  
    </td>
    <td>Neuer Artikel </td>
    <td>22. April 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-47/acsd-56858-role-permissions-display-issue-in-b2b-company-admin-panel">ACSD-56858: Diskrepanz bei Rollenberechtigungen in B2B-Unternehmensadministratoren:</a> Der Patch ACSD-56858 behebt das Problem, bei dem Rollenberechtigungen fälschlicherweise für einen eingeschränkten Unternehmensadministrator in der B2B-Umgebung angezeigt werden. Dieser Patch ist verfügbar, wenn <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.47 installiert ist. 
    </td>
    <td>Neuer Artikel </td>
    <td>22. April 2024</td>
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
