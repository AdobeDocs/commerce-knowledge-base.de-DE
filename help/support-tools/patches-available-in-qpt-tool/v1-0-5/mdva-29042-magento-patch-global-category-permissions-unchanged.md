---
title: "MDVA-29042: Globale Kategorieberechtigungen unverändert"
description: Der Patch MDVA-29042 behebt das Problem, dass Katalogberechtigungen automatisch in "Zulassen"geändert wurden, nachdem ein neues Produkt zum freigegebenen Katalog in der Commerce-Admin hinzugefügt wurde. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.3.6 mit der B2B-Erweiterung behoben wurde.
exl-id: 491b8881-87ec-4820-8f87-54961682e961
feature: Catalog Management, Categories, Customer Service, Roles/Permissions
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# MDVA-29042: Globale Kategorieberechtigungen unverändert

Der Patch MDVA-29042 behebt das Problem, dass Katalogberechtigungen automatisch in &quot;*Allow*&quot;geändert wurden, nachdem ein neues Produkt zum freigegebenen Katalog in der Commerce Admin hinzugefügt wurde. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.3.6 mit der B2B-Erweiterung behoben wurde.

## Betroffene Produkte und Versionen

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.3 bis 2.3.4-p2 mit B2B-Erweiterung

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn Sie die Auswahl einer Kundengruppe aus den Berechtigungen für globale Kategorien in Commerce Admin aufheben, wird diese Kundengruppe in den Kategorieberechtigungen nicht automatisch auf &quot;*Ablehnen*&quot;gesetzt.

<u>Voraussetzungen</u>:

* B2B-Instanz mit einer definierten und ausgewählten Kundengruppe unter **STORES** > **Configuration** > **CATALOG** > **Catalog** > **Kategorieberechtigungen** für:
   * **Browsing-Kategorie zulassen**
   * **Produktpreise anzeigen**
   * **Hinzufügen zum Warenkorb zulassen**
* Unter jeder **Kategorie** wird die Kundengruppe für Folgendes als &quot;*Zulassen*&quot;definiert:
   * **Browsing Category**
   * **Produktpreise anzeigen**
   * **Zum Warenkorb hinzufügen**

<u>Zu reproduzierende Schritte</u>:

1. Wechseln Sie im Commerce-Admin zu **STORES** > **Configuration** > **CATALOG** > **Catalog** > **Kategorieberechtigungen** und deaktivieren Sie die Kundengruppe aus:
   * **Browsing-Kategorie zulassen**
   * **Produktpreise anzeigen**
   * **Hinzufügen zum Warenkorb zulassen**
1. Klicken Sie auf die Schaltfläche **Konfiguration speichern** .
1. Warten Sie, bis die Indexer ausgeführt werden.
1. Sehen Sie sich **KATALOG** > **Kategorien** > **Kategorieberechtigungen** an.

<u>Erwartete Ergebnisse</u>:

**Kategorieberechtigungen** wird für alle Kategorien für die Kundengruppe auf &quot;*Ablehnen*&quot;gesetzt.

<u>Tatsächliche Ergebnisse</u>:

Es wurden keine Kategorieberechtigungen für die Kundengruppe geändert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.

Weitere Informationen zur B2B-Unternehmensfunktionalität finden Sie in den folgenden Artikeln in unserer Entwicklerdokumentation:

* [B2B-Entwicklerhandbuch](https://devdocs.magento.com/guides/v2.4/b2b/bk-b2b.html)
* [Verwalten von Unternehmensrollen](https://devdocs.magento.com/guides/v2.4/b2b/roles.html)
* [Adobe Commerce Enterprise B2B Extension configuration paths reference](https://devdocs.magento.com/guides/v2.4/config-guide/prod/config-reference-b2b.html)
