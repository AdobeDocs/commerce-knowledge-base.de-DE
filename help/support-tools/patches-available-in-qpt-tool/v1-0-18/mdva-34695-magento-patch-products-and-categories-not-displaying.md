---
title: "MDVA-34695: Produkte und Kategorien werden nicht angezeigt"
description: Der Patch MDVA-34695 behebt das Problem, dass Produkte und Kategorien nicht im Kategorienraster in Admin angezeigt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 installiert ist. Die Patch-ID lautet MDVA-34695. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.3 behoben wurde.
exl-id: 0c2e50c1-648b-480a-a768-72af721950d8
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# MDVA-34695: Produkte und Kategorien werden nicht angezeigt

Der Patch MDVA-34695 behebt das Problem, dass Produkte und Kategorien nicht im Kategorienraster in Admin angezeigt werden. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 installiert ist. Die Patch-ID lautet MDVA-34695. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce in Cloud-Infrastruktur 2.3.4

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce On-Premise und Adobe Commerce über Cloud-Infrastruktur 2.3.0-2.4.0-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Negative Werte für `children_count` in der Datenbank angezeigt werden, nachdem Kategorien gelöscht wurden.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich beim Admin-Backend an.
1. Navigieren Sie zu **Katalog > Kategorien**.
1. Klicks **Unterkategorie hinzufügen**.
1. Satz **Kategoriename** = *Übergeordnetes Element 1*, dann Speichern.
1. Klicks **Unterkategorie hinzufügen**.
1. Satz **Kategoriename** = *Kind 1*, dann Speichern.
1. Klicks **Unterkategorie hinzufügen**.
1. Satz **Kategoriename** = *Kind 2*, dann Speichern.
1. Klicks **Unterkategorie hinzufügen**.
1. Satz **Kategoriename** = *Kind 3*, dann Speichern. An dieser Stelle sollte diese Kategorie eine Ebene haben = *5*.
1. Klicken Sie auf **Kind 1** Kategorie.
1. Löschen Sie die Kategorie.

<u>Erwartete Ergebnisse</u>:

Das Kategorienraster zeigt wie erwartet Produkte und Kategorien an.

<u>Tatsächliche Ergebnisse</u>:

Das Kategorienraster ist leer. Überprüfen Sie die `catalog_category_entity` in der Datenbank. Beachten Sie Folgendes: `children_count` wurde negativ.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) Abschnitt.
