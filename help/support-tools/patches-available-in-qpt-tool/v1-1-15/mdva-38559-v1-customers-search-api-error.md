---
title: "MDVA-38559: /V1/Customers/search API gibt Fehler zurück"
description: Der Patch MDVA-38559 behebt das Problem, dass die API "/V1/Customers/search" einen Fehler für Kunden zurückgibt, die mehr als ein Abonnement haben. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 installiert ist. Die Patch-ID lautet MDVA-38559. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben ist.
exl-id: 434fe78c-c384-4fa8-b26a-cb00007e490e
feature: REST, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# MDVA-38559: /V1/Customers/search API gibt Fehler zurück

Der Patch MDVA-38559 behebt das Problem, bei dem die `/V1/customers/search` Die API gibt einen Fehler für Kunden zurück, die mehr als ein Abonnement haben. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 installiert ist. Die Patch-ID lautet MDVA-38559. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben ist.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

`/V1/customers/search` Die API gibt einen Fehler für Kunden mit mehr als einem Abonnement zurück.

<u>Voraussetzungen</u>:

Der Adobe Commerce-Store verwendet mehr als eine Website.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zu **Store** > **Konfiguration** > **Kunde** > **Kundenkonfiguration** > **Optionen für Kontofreigabe** und wählen **Global**.
1. Navigieren Sie zu **Kunden** > **Alle Kunden** auswählen **Bearbeiten** auf einen beliebigen Kunden klicken und dann **Newsletter**.
1. Abonnieren Sie einen Newsletter für mehr als eine Website und speichern Sie den Kunden.
1. Senden Sie die folgende Anfrage:

```REST API
V1/customers/search?searchCriteria[filterGroups][0][filters][0][field]=email&searchCriteria[filterGroups][0][filters][0][value]=test@example.com&searchCriteria[filterGroups][0][filters][0][conditionType]=eq
```

<u>Erwartete Ergebnisse</u>:

Die Suchergebnisse des Kunden werden angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Der folgende Fehler wird in der Datei exception.log protokolliert: *Element (Magento\Customer\Model\Customer\Interceptor) mit der gleichen ID &quot;1&quot;ist bereits vorhanden.*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
