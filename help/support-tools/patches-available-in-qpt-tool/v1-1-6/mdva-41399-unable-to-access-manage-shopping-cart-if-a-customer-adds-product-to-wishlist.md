---
title: '"MDVA-41399: Zugriff auf den "Warenkorb verwalten"ist nicht möglich, wenn ein Kunde Produkte auf die Wunschliste setzt."'
description: Der Patch MDVA-41399 behebt das Problem, dass Admin-Benutzer nicht auf die Seite "Warenkorb verwalten"zugreifen können, wenn ein Kunde ein Produkt zur Wunschliste hinzufügt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6 installiert ist. Die Patch-ID lautet MDVA-41399. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.
exl-id: 227653c6-2d20-4475-b973-b9fa58db815b
feature: Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# MDVA-41399: Zugriff auf den Warenkorb verwalten nicht möglich, wenn ein Kunde Produkte auf die Wunschliste setzt

Der Patch MDVA-41399 behebt das Problem, dass Admin-Benutzer nicht auf die Seite &quot;Warenkorb verwalten&quot;zugreifen können, wenn ein Kunde ein Produkt zur Wunschliste hinzufügt. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6 installiert ist. Die Patch-ID lautet MDVA-41399. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.3 - 2.4.1-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Admin-Benutzer können nicht auf die Seite &quot;Warenkorb verwalten&quot;zugreifen, wenn ein Kunde ein Produkt zur Wunschliste hinzufügt.

<u>Voraussetzungen</u>:

1. Erstellen Sie zwei oder mehr Produkte.
1. Erstellen Sie einen Kunden.
1. Aktivieren Sie den Entwicklermodus.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zur Storefront und melden Sie sich als Kunde unter den Voraussetzungen an.
1. Fügen Sie ein Produkt zur Wunschliste hinzu.
1. Navigieren Sie zum Admin-Bedienfeld, navigieren Sie zur Bearbeitungsseite für den erstellten Kunden und klicken Sie auf die **Warenkorb verwalten** Schaltfläche.

<u>Erwartete Ergebnisse</u>:

Der Admin-Benutzer kann den Warenkorb verwalten.

<u>Tatsächliche Ergebnisse</u>:

Der Admin-Benutzer erhält eine Fehlermeldung: *Es ist ein Fehler aufgetreten. Weitere Informationen finden Sie unter Fehlerprotokoll .*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) Abschnitt.
