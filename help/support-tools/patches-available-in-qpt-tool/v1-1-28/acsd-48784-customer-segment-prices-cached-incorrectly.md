---
title: 'ACSD-48784: Preise von Kundensegmenten wurden zwischen Kundengruppen falsch zwischengespeichert'
description: Wenden Sie den Patch ACSD-48784 an, um das Adobe Commerce-Problem zu beheben, bei dem Kundensegmentpreise zwischen Kundengruppen falsch zwischengespeichert werden.
exl-id: 6be11fd0-5c93-4ac7-8664-7e2a289c9e38
feature: Admin Workspace, Cache, Customer Service, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-48784: Preise von Kundensegmenten wurden zwischen Kundengruppen falsch zwischengespeichert

Mit dem Patch ACSD-48784 wird das Problem behoben, dass Kundensegmentpreise zwischen Kundengruppen falsch zwischengespeichert werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28 installiert ist. Die Patch-ID ist ACSD-48784. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Kundensegmentpreise werden zwischen Kundengruppen falsch zwischengespeichert.

<u>Voraussetzungen</u>:

Konfigurieren Sie [!DNL Varnish] oder [!DNL Fastly].

<u>Schritte zur Reproduktion</u>:

1. Aktivieren Sie das vollständige Seiten-Caching in Ihrem Store.
1. Melden Sie sich bei der Website als Benutzer mit speziellen Kundengruppenpreisen an.
1. Navigieren Sie zu einer Produktseite für ein Produkt mit speziellen Kundengruppenpreisen. Beachten Sie den *Sonderpreis*.
1. Öffnen Sie dieselbe Produktseite wie ein Gastbenutzer, ohne sich anzumelden, in einem separaten Browser. Beobachten Sie den regulären Preis.
1. Greifen Sie auf die Verwaltungsoberfläche von Adobe Commerce zu und löschen Sie den Adobe Commerce- und [!DNL Fastly]-Cache für diesen Store.
1. Entfernen Sie im angemeldeten Browser das `X-Magento-Vary`-Cookie.
1. Laden Sie im angemeldeten Browser dieselbe Produktseite mehrmals neu, bis das Caching vollständig geleert ist.
1. Laden Sie im nicht angemeldeten Browser die Produktseite neu, um nun die Kundengruppenpreise anzuzeigen.

<u>Erwartete Ergebnisse</u>:

Die Produktseite zeigt den korrekten Preis für bestimmte Kundengruppen an.

<u>Tatsächliche Ergebnisse</u>:

* Gastbenutzer sehen den speziellen Preis für angemeldete Benutzer.
* Der Mini-Warenkorb zeigt den richtigen Preis an, sobald das Produkt hinzugefügt wird.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
