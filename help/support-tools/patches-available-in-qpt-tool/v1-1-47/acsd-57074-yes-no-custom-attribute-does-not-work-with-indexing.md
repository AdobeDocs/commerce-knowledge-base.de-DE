---
title: '"ACSD-57074: *Ja/Nein* benutzerdefiniertes Attribut mit dem Präfix "price_*"im Attribut "attribute_code"funktioniert nicht mit der Indizierung."'
description: Wenden Sie den Patch ACSD-57074 an, um das Adobe Commerce-Problem zu beheben, bei dem das benutzerdefinierte Attribut *Ja/Nein* mit dem Präfix `price_* im Attribut `attribute_code` nicht mit der Indizierung funktioniert.
feature: Products, Categories, Catalog Management
role: Admin, Developer
exl-id: c620722f-a66d-4cae-9614-becec589a78c
source-git-commit: 4197f2a8f3d4775d3459b17bd92fa51a54ff9607
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-57074: *Ja/Nein* benutzerdefiniertes Attribut mit `price_*` Präfix in `attribute_code` -Attribut funktioniert nicht mit der Indizierung

Der Patch ACSD-57074 behebt das Problem, bei dem das *Ja/Nein* benutzerdefiniertes Attribut mit `price_*` -Präfix im `attribute_code` -Attribut funktioniert nicht bei der Indizierung. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.47 ist installiert. Die Patch-ID ist ACSD-57074. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6 - p4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die *Ja/Nein* benutzerdefiniertes Attribut mit `price_*` -Präfix im `attribute_code` -Attribut funktioniert nicht bei der Indizierung.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein benutzerdefiniertes Produktattribut mit den folgenden Optionen:
   * *[!UICONTROL Catalog Input Type]*: *Ja/Nein*
   * *[!UICONTROL Scope]*: *StoreView*
   * *[!UICONTROL Use in Search]*: *Ja*
1. Weisen Sie das Attribut dem standardmäßigen Attributsatz zu.
1. Erstellen Sie ein Produkt mit dem von uns erstellten Attribut.
1. Weisen Sie das soeben erstellte Produkt einer Kategorie zu.
1. Führen Sie die vollständige Neuindizierung aus.

<u>Erwartete Ergebnisse</u>:

Das Produkt wird in der zugewiesenen Kategorie angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Das Produkt wird nicht auf der Titelkategorieseite angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
