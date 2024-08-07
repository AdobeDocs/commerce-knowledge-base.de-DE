---
title: '"MDVA-38447: "Nicht einzeln sichtbar" konfigurierbare Kinderprodukte werden in der GraphQL-Antwort und langsamen MySQL-Abfrage zurückgegeben."'
description: Der MDVA-38447 Adobe Commerce-Patch behebt das Problem, dass konfigurierbare untergeordnete Produkte vom Typ "Nicht einzeln sichtbar"in der GraphQL-Antwort zurückgegeben werden und die MySQL-Abfrage für GraphQL-Produkte mit Kategoriefilter verlangsamt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-38447. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
exl-id: 302e7458-d9ea-466a-a2ac-d86a8ee3eca3
feature: B2B, GraphQL, Categories, Configuration, Products, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# MDVA-38447: Konfigurierbare Kinderprodukte werden in der GraphQL-Antwort und langsamen MySQL-Abfragen zurückgegeben.

Der MDVA-38447 Adobe Commerce-Patch behebt das Problem, dass konfigurierbare untergeordnete Produkte vom Typ &quot;Nicht einzeln sichtbar&quot;in der GraphQL-Antwort zurückgegeben werden und die MySQL-Abfrage für GraphQL-Produkte mit Kategoriefilter verlangsamt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-38447. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Konfigurierbare untergeordnete Produkte, die nicht einzeln sichtbar sind, werden in der GraphQL-Antwort zurückgegeben und die MySQL-Abfrage für die GraphQL-Produktabfrage mit Kategoriefilter verlangsamt.

<u>Voraussetzungen</u>:

B2B-Module müssen installiert sein.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein konfigurierbares Produkt mit einfachen Produkten, die auf **Nicht einzeln sichtbar** eingestellt sind.
1. Führen Sie eine **vollständige Neuindizierung** aus.
1. Führen Sie eine **GraphQL-Abfrage** wie folgt aus:

<pre>query getFilteredProducts(
  $filter: ProductAttributeFilterInput!
  $sort: ProductAttributeSortInput!
  $search: String
  $pageSize: Int!
  $currentPage: Int!
) {
  products(
    filter: $filter
    sort: $sort
    search: $search
    pageSize: $pageSize
    currentPage: $currentPage
  ) {
    total_count
    page_info {
      total_pages
      current_page
      page_size
    }
    items {
      name
      sku
    }
  }
}</pre>

Variablen:

<pre>{"filter":{"user_group":{"eq":"},"search":"config-100","sort":{},"pageSize":200,"currentPage":1}
</pre>

<u>Erwartete Ergebnisse</u>:

Produkte mit Sichtbarkeit, die auf &quot;Nicht einzeln sichtbar&quot;gesetzt sind, werden als Antwort nicht zurückgegeben.

<u>Tatsächliche Ergebnisse</u>:

Produkte, deren Sichtbarkeit auf &quot;Nicht einzeln sichtbar&quot;festgelegt ist, werden als Antwort zurückgegeben.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungstyp die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zu Qualitäts-Patches für Adobe Commerce finden Sie unter:

* [Qualitätspatches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Überprüfen Sie mithilfe des Qualitätssicherungswerkzeugs](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md), ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) verfügbare Patches.
