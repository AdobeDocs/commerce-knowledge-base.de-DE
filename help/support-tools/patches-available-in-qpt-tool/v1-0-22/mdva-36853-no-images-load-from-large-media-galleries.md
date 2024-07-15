---
title: "MDVA-36853: Keine Bilder aus großen Mediengalerien geladen"
description: Der Patch MDVA-36853 behebt das Problem, dass keine Bilder geladen werden, da das Media Galerie-Widget des Seiten-Builders nicht geladen wird, wenn Sie über ein großes Medienverzeichnis verfügen.
exl-id: 64e089d9-d443-4aa7-8e04-a3598b05958d
feature: CMS, Cache, Media
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# MDVA-36853: Keine Bilder aus großen Mediengalerien geladen

Der Patch MDVA-36853 behebt das Problem, dass keine Bilder geladen werden, da das Media Galerie-Widget des Seiten-Builders nicht geladen wird, wenn Sie über ein großes Medienverzeichnis verfügen.

Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 installiert ist. Die Patch-ID lautet MDVA-36853. Bitte beachten Sie, dass das Problem in Adobe Commerce-Version 2.4.3 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce in der Cloud-Infrastruktur 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:** Adobe Commerce On-Premise und Adobe Commerce in Cloud-Infrastruktur 2.4.2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Legen Sie **Enable Old Media Gallery** = *Ja* in **Admin > Stores > Configuration > Advanced > System > Media Gallery** fest.
1. Navigieren Sie zu **Inhalt > Blöcke** und erstellen Sie einen neuen CMS-Block oder bearbeiten Sie einen vorhandenen CMS-Block.
1. Klicken Sie auf die Schaltfläche **Mit Pagebuilder bearbeiten** .
1. Fügen Sie ein Medienelement hinzu.
1. Klicken Sie auf die Schaltfläche **Aus Galerie auswählen** .

<u>Erwartete Ergebnisse</u>:

Sowohl das Mediensalerie-Widget als auch die Bilder der Mediengalerie werden wie erwartet geladen.

<u>Tatsächliche Ergebnisse</u>:

Die Bilder des Mediensalerie-Widgets und der Mediengalerie werden nicht geladen, wenn Sie ein großes `pub/media/catalog/product/cache/` -Verzeichnis haben.

## Wenden Sie den Patch an

Verwenden Sie je nach Adobe Commerce-Produkt die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie im Abschnitt [Im QPT-Tool verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
