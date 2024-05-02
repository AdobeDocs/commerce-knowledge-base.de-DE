---
title: "ACSD-56246: Durch die Planung von Produktaktualisierungen werden die multiselect-Attributwerte gelöscht."
description: Wenden Sie den Patch ACSD-56246 an, um das Adobe Commerce-Problem zu beheben, bei dem durch die Planung von Produktaktualisierungen die Multiselect-Attributwerte gelöscht werden.
feature: Products, Attributes, Staging
role: Admin, Developer
exl-id: ddca8ac0-6aa8-4bf1-b8c2-4819758cb198
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-56246: Bei der Planung von Produktaktualisierungen werden Werte für Mehrfachauswahl-Attribute gelöscht

Der Patch ACSD-56246 behebt das Problem, dass durch die Planung von Produktaktualisierungen Werte für Mehrfachauswahl-Attribute gelöscht werden. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 ist installiert. Die Patch-ID ist ACSD-56246. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6 - p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die geplanten Produktaktualisierungen löschen die Multiselect-Attributwerte.

<u>Zu reproduzierende Schritte</u>:

1. Installieren Sie Adobe Commerce.
1. Navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** und erstellen Sie das folgende Attribut:

   * Standardbezeichnung: Programm
   * Katalogeingabetyp für Store Owner: Mehrfachauswahl
   * Optionen verwalten (Werte Ihres Attributs): Auswahl, Querformat, SafetyShield
   * Attributcode: customer_program
   * Umfang: Global
   * Zu Spaltenoptionen hinzufügen: Nein
   * Verwendung in Filteroptionen: nein
   * Store-Eigenschaften
   * Funktion: *333*
   * HTML-Tags in der Storefront zulassen: nein

1. Ausführen
   `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`.
1. Ausführen
   `bin/magento setup:upgrade`.
1. Navigieren Sie zu **[!UICONTROL Admin]** > Einfaches Produkt auswählen > Alle Elemente im Programmattribut auswählen > Klicken Sie auf **[!UICONTROL Save the product]**.
1. Planen Sie ein Update für dieses Produkt in der nächsten Minute und führen Sie den folgenden Befehl aus, um die Inhaltsstaging-Umgebung zu nutzen:
   `for i in {1..100}; do bin/magento cron:run; done`.

<u>Erwartete Ergebnisse</u>:

Das Produkt **[!UICONTROL program]** sollte sich nicht ändern.

<u>Tatsächliche Ergebnisse</u>:

Das Produkt **[!UICONTROL program]** -Attribut gelöscht wird.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
