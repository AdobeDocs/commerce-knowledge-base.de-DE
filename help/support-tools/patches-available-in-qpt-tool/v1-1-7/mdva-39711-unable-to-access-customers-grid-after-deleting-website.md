---
title: "MDVA-39711: Nach dem Löschen der Website kann nicht auf das Kundennetz zugegriffen werden."
description: Der Patch MDVA-39711 behebt das Problem, dass der Admin-Benutzer nach dem Löschen der Website nicht auf das Kundennetz zugreifen kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 installiert ist. Die Patch-ID lautet MDVA-39711. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.
exl-id: 46bef304-9360-4b69-b064-631725de381c
feature: Configuration
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-39711: Nach dem Löschen einer Website kann nicht auf das Kundennetz zugegriffen werden

Der Patch MDVA-39711 behebt das Problem, dass der Admin-Benutzer nach dem Löschen der Website nicht auf das Kundennetz zugreifen kann. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 ist installiert. Die Patch-ID lautet MDVA-39711. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7-p2, 2.3.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.2-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Admin-Benutzer kann nach dem Löschen der Website nicht auf das Kundenraster zugreifen.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine neue Website-, Store- und Store-Ansicht.
1. Erstellen Sie einen neuen Kunden im Admin und verknüpfen Sie ihn mit der erstellten Website.
1. Navigieren Sie zu **Stores** > **Alle Geschäfte** und löschen Sie die erstellte Website.
1. Navigieren Sie zu **Kunden** > **Alle Kunden**.

<u>Erwartete Ergebnisse</u>:

* Es gibt keine Fehlermeldung.
* Alle Kunden sind im Raster sichtbar.

<u>Tatsächliche Ergebnisse</u>:

* Der Benutzer erhält eine Fehlermeldung: *Die Webseite mit ID 2, die angefordert wurde, wurde nicht gefunden. Website überprüfen und erneut versuchen*
* Nicht alle Kunden werden angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
