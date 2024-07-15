---
title: "MDVA-35982: Kann keine Bestellungen versenden"
description: Der Patch MDVA-35982 behebt den Fehler, wenn ein auf eine bestimmte Website beschränkter Admin-Benutzer keine Sendung für die auf derselben Website platzierte Bestellung erstellen kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 installiert ist. Die Patch-ID lautet MDVA-35982. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.
exl-id: f41c6572-66bb-4697-93e3-da34b81829e2
feature: Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MDVA-35982: Kann keine Bestellungen versenden

Der Patch MDVA-35982 behebt den Fehler, wenn ein auf eine bestimmte Website beschränkter Admin-Benutzer keine Sendung für die auf derselben Website platzierte Bestellung erstellen kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 installiert ist. Die Patch-ID lautet MDVA-35982. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.3.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Händler kann bestimmte Bestellungen nicht versenden.

<u>Zu reproduzierende Schritte</u>:

1. Wählen Sie eine beliebige Produktseite für das Produkt mit Ausnahme des Standardspeichers aus. Detaillierte Schritte finden Sie unter [Produkt in Websites](https://docs.magento.com/user-guide/catalog/settings-basic-websites.html) in unserem Benutzerhandbuch.
1. Erstellen Sie eine Benutzerrolle für den Administrator mit benutzerdefinierten Rollenbereichen, in denen die Standardwebsite/der Standardspeicher nicht ausgewählt ist. Detaillierte Schritte finden Sie unter [Definieren einer Rolle](https://docs.magento.com/user-guide/system/permissions-user-roles.html#define-a-role) in unserem Benutzerhandbuch.
1. Öffnen Sie das Produkt im Bearbeitungsmodus und legen Sie einen Gruppenpreis für dieses Produkt in **Erweiterter Preis** fest. Detaillierte Schritte finden Sie unter [Gruppenpreis](https://docs.magento.com/user-guide/catalog/product-price-group.html) in unserem Benutzerhandbuch.
1. Erstellen Sie eine Bestellung mit diesem Produkt.
1. Melden Sie sich mit dieser Benutzerrolle unter Admin an und erstellen Sie eine Sendung. Detaillierte Schritte finden Sie unter [Erstellen einer Sendung](https://docs.magento.com/user-guide/sales/shipments-create.html) in unserem Benutzerhandbuch.

<u>Erwartete Ergebnisse</u>:

Der Versand wird erstellt.

<u>Tatsächliche Ergebnisse</u>:

Der folgende Fehler wird angezeigt:

`"0":"Notice: Undefined offset: XX in \/vendor\/magento\/module-catalog\/Model\/Product\/Attribute\/Backend\/GroupPrice\/AbstractGroupPrice.php on line 290"`

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
