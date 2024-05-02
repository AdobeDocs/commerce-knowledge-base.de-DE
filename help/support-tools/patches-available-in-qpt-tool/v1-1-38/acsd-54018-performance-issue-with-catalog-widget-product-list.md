---
title: "ACSD-54018: Leistungsproblem mit Katalog-Widget-Produktliste"
description: Wenden Sie den Patch ACSD-54018 an, um das Adobe Commerce-Problem zu beheben, bei dem die Seite beim Hinzufügen einer Katalog-Widget-Produktliste mit dem booleschen Bedingungs- und Attributtyp langsam geladen wird.
feature: Attributes, Catalog Management, Page Builder, Page Content, Storefront
role: Admin, Developer
exl-id: 9f20484d-58c7-49d8-87df-1eeb84bee6fe
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-54018: Leistungsproblem mit Katalog-Widget-Produktliste

Der Patch ACSD-54018 behebt das Problem, dass die Seite beim Hinzufügen einer Katalog-Widget-Produktliste mit Bedingungen- und Attributtyp boolesch langsam geladen wird. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.38 installiert ist. Die Patch-ID lautet ACSD-54018. Beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.5 - p4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Seite wird beim Hinzufügen einer Katalog-Widget-Produktliste mit booleschem Bedingungs- und Attributtyp langsam geladen.

<u>Zu reproduzierende Schritte</u>:

1. Generieren Sie 100.000 Produkte.
1. Erstellen Sie ein boolesches Attribut mit dem Umfang , der auf [!UICONTROL Store View].
1. Weisen Sie allen Attributsätzen das Attribut zu.
   * Zuweisen des Attributwerts *Ja* für alle Produkte.
1. Gehen Sie jetzt zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]** und wählen Sie alle 100.000 Produkte aus.
   * Auswählen **[!UICONTROL Actions]** > **[!UICONTROL Update Attribute]**.
   * Setzen Sie das bool-Attribut auf *Ja* und speichern Sie es.
   * Wenn Sie sich bei diesem Schritt abgemeldet haben, überprüfen Sie die *Hinweise*.
1. Navigieren Sie zur CLI und führen Sie `php bin/magento queue:con:start product_action_attribute.update`.
   * Stellen Sie sicher, dass die Attribute für alle Produkte aktualisiert sind.
1. Gehen Sie jetzt zu **[!UICONTROL Content]** > **[!UICONTROL Pages]** und erstellen Sie eine neue Seite.
1. Öffnen **[!UICONTROL Page Builder]** > **[!UICONTROL Add row]** > **[!UICONTROL Add Content]** > **[!UICONTROL Products]**.
1. Auswählen *[!UICONTROL Select Products By]* = *[!UICONTROL Condition]*.
1. Bedingung festlegen *[!UICONTROL Created attribute]* nach *[!UICONTROL Yes]* und speichern Sie es.
1. Gehen Sie zum Frontend und öffnen Sie die erstellte Seite.
1. Deaktivieren Sie den vollständigen Seiten-Cache und blockieren Sie den HTML-Cache.
1. Überprüfen Sie die Seitenladegeschwindigkeit.
1. Laden Sie die Seite einige Male neu und berechnen Sie die durchschnittliche Ladezeit.

<u>Erwartete Ergebnisse</u>:

Die Seite wird schnell geladen.

<u>Tatsächliche Ergebnisse</u>:

Das Laden der Seite dauert 5-10 Sekunden.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
