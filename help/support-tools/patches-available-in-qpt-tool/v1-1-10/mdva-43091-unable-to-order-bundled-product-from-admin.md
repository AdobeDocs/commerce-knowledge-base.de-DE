---
title: "MDVA-43091: Gebündeltes Produkt kann nicht von Admin bestellt werden"
description: Der Patch MDVA-43091 behebt das Problem, dass Benutzer gebündelte Produkte nicht vom Commerce-Administrator bestellen können. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-43091. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
exl-id: 77dff356-4f75-4b06-b62b-5379a4eec273
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# MDVA-43091: Gebündeltes Produkt kann nicht von Admin bestellt werden

Der Patch MDVA-43091 behebt das Problem, dass Benutzer gebündelte Produkte nicht vom Commerce-Administrator bestellen können. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-43091. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn Sie versuchen, ein gebündeltes Produkt vom Administrator zu bestellen, wird der folgende Fehler ausgegeben: *Sie können die Dezimalzahl für dieses Produkt nicht verwenden.*

<u>Zu reproduzierende Schritte</u>:

1. Installieren Sie einen sauberen Adobe Commerce.
1. Erstellen Sie zwei einfache Produkte.
1. Erstellen Sie ein gebündeltes Produkt mit zwei Optionen.
1. Erstellen Sie ein Kundenkonto auf der Vorderseite.
1. Gehen Sie zu **Admin** > **Vertrieb** > **Bestellungen** > **Neue Bestellung erstellen**.
   * Wählen Sie das soeben erstellte Kundenkonto aus.
   * Versuchen Sie, das gebündelte Produkt zum Warenkorb hinzuzufügen.

<u>Erwartete Ergebnisse</u>:

Administratoren können das Produkt mit einer Menge zum Warenkorb hinzufügen.

<u>Tatsächliche Ergebnisse</u>:

Der Admin-Benutzer erhält den folgenden Fehler: *Sie können die Dezimalzahl für dieses Produkt nicht verwenden.*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
