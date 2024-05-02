---
title: "MDVA-34189: Visual Merchandiser führt lange MySQL-Abfragen aus"
description: Der Patch MDVA-34189 behebt das Problem, bei dem Adobe Commerce beim Laden der Kategorieseite "Admin"große Visual Merchandiser-Abfragen ausführt.
exl-id: 94143d80-3240-4a18-890d-fb759ea9c30d
feature: Categories, Merchandising, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# MDVA-34189: Visual Merchandiser führt lange MySQL-Abfragen aus

Der Patch MDVA-34189 behebt das Problem, bei dem Adobe Commerce beim Laden der Kategorieseite &quot;Admin&quot;große Visual Merchandiser-Abfragen ausführt.

Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 installiert ist. Die Patch-ID lautet MDVA-34189. Bitte beachten Sie, dass das Problem in Adobe Commerce-Version 2.4.3 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce auf Cloud-Infrastruktur 2.3.5-p2

**Kompatibel mit Adobe Commerce-Versionen:** Adobe Commerce vor Ort und Adobe Commerce über Cloud-Infrastruktur 2.3.4-2.4.2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Website führt große MySQL-Abfragen auf dem Produktionsserver aus.

<u>Zu reproduzierende Schritte</u>:

1. Um auf Visual Merchandiser zuzugreifen, navigieren Sie zum *Admin* Seitenleiste, klicken Sie **Katalog** > **Kategorien**.
1. Laden Sie die **Kategorien** im Admin-Bereich (beim ersten Laden der Stamm-Kategorie) und beobachten Sie die ausgeführten Abfragen.

<u>Erwartetes Ergebnis</u>:

Der Administrator **Kategorien** -Seite geladen werden, ohne dass langsame Abfragen generiert werden.

<u>Tatsächliches Ergebnis</u>:

Dies hängt von Ihrer PHP-Konfiguration ab. Das häufigste Beispiel für diesen Fehler ist, dass die **Kategorien** Seite wird nicht geöffnet und es wird ein Fehler ausgegeben *Fehler 503: erstes Byte-Timeout* angezeigt.

Wenn Adobe Commerce den Visual Merchandiser lädt, wird eine langsame MySQL-Abfrage ausgeführt. Diese Abfrage enthält viele Produkt-IDs, die in `ORDER BY FIELD(`e`.`entity_id`,  ...)`

in `app/code/Magento/VisualMerchandiser/Model/Category/Products.php:: applyPositions`

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie im Abschnitt [In QPT verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) Abschnitt.
