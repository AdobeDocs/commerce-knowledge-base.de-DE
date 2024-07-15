---
title: "MDVA-38666: Admin-Benutzer kann konfigurierbare Produktoptionen nicht ändern"
description: Der Patch MDVA-38666 behebt das Problem, dass der Admin-Benutzer nicht in der Lage ist, konfigurierbare Produktoptionen im Warenkorb des Kunden zu ändern. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-38666. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: 72440e47-1deb-41da-a225-d4bc73029ad5
feature: Admin Workspace, Configuration, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# MDVA-38666: Admin-Benutzer kann konfigurierbare Produktoptionen nicht ändern

Der Patch MDVA-38666 behebt das Problem, dass der Admin-Benutzer nicht in der Lage ist, konfigurierbare Produktoptionen im Warenkorb des Kunden zu ändern. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-38666. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.2 - 2.3.5-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Admin-Benutzer kann die konfigurierbaren Produktoptionen im Warenkorb des Kunden nicht ändern.

<u>Zu reproduzierende Schritte</u>:

1. Stellen Sie den Kundenkontobereich auf Global ein.
1. Erstellen Sie zwei Websites mit Geschäften.
1. Erstellen Sie zwei konfigurierbare Produkte und weisen Sie sie jeder Website zu.
1. Erstellen Sie ein Kundenkonto im Frontend und melden Sie sich an.
1. Fügen Sie ein Produkt zum Warenkorb hinzu und führen Sie einen Checkout durch (dies geschieht, um die Anführungszeichen auf jeder Website zu unterscheiden).
1. Fügen Sie ein Produkt zum Warenkorb hinzu und lassen Sie es.
1. Wechseln Sie zur zweiten Website und fügen Sie das Produkt zum Warenkorb hinzu (dieselbe Anmeldung sollte funktionieren, da der Kundenkontobereich auf Global eingestellt ist).
1. Öffnen Sie den Kunden über den Administrator und navigieren Sie zur Registerkarte Warenkorb .
1. Schalten Sie den Speicher aus der Dropdown-Liste aus und versuchen Sie, die Konfiguration zu ändern.

<u>Erwartete Ergebnisse</u>:

Benutzer erhält ein Popup mit konfigurierbaren Optionen.

<u>Tatsächliche Ergebnisse</u>:

Es wird kein Popup-Formular angezeigt. Der Benutzer kann die Konfiguration nicht ändern.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
