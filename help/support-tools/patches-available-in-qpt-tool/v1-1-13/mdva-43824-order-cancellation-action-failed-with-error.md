---
title: '"MDVA-43824: Aktion zum Abbrechen der Bestellung fehlgeschlagen mit Fehler "Sie haben den Artikel nicht abgebrochen"'
description: '''Der Patch MDVA-43824 behebt das Problem, bei dem die Löschaktion der Bestellung mit dem Fehler fehlschlug: *Sie haben den Artikel nicht abgebrochen*. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-43824. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben werden soll."'
exl-id: e4d839d6-84ed-4157-80a1-fd482fef897c
feature: Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# MDVA-43824: Aktion zum Abbrechen der Bestellung fehlgeschlagen mit Fehler &quot;Sie haben den Artikel nicht abgebrochen&quot;

Der Patch MDVA-43824 behebt das Problem, bei dem die Aktion zum Abbrechen der Bestellung mit dem Fehler fehlgeschlagen ist: *Sie haben den Artikel* nicht abgebrochen. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-43824. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.6 - 2.3.7-p3, 2.4.1 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die von einem angemeldeten Kunden aufgegebene Bestellung kann nicht storniert werden. Die Löschaktion der Bestellung schlug mit dem folgenden Fehler fehl:

```
Zend_Db_Statement_Exception: SQLSTATE[23000]: Integrity constraint violation: 1452 Cannot add or update a child row: a foreign key constraint fails (`mer33515_ee24developpbdevelop`.`salesrule_customer`, CONSTRAINT `SALESRULE_CUSTOMER_RULE_ID_SEQUENCE_SALESRULE_SEQUENCE_VALUE` FOREIGN KEY (`rule_id`) REFERENCES `sequence_salesrule` (`sequen), query was: INSERT INTO `salesrule_customer` () VALUES (){code}
```

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine Verkaufsregel (Coupontyp ist entweder &quot;spezifischer Coupon&quot;oder &quot;Kein Coupon&quot;).
1. Gehen Sie zur Storefront und melden Sie sich als Kunde an und fügen Sie dem Warenkorb ein Produkt hinzu.
1. Gehen Sie zum Warenkorb und wenden Sie die Regel zum Warenkorbpreis an, wenn die Warenkorbpreisregel einen Gutschein als &quot;Spezifischer Coupon&quot;aufweist. Die Preisregel für den Warenkorb sollte erfolgreich angewendet werden.
1. Gehen Sie zum Checkout und platzieren Sie die Bestellung mit jeder Zahlungsmethode.
1. Navigieren Sie zu Commerce Admin > **Vertrieb** > **Bestellungen**.
1. Öffnen Sie die in Schritt 4 aufgegebene Bestellung.
1. Klicken Sie auf die Schaltfläche **Abbrechen** .

<u>Erwartete Ergebnisse</u>:

Die Bestellung wird ohne Fehler erfolgreich abgebrochen.

<u>Tatsächliche Ergebnisse</u>:

Die Aktion zum Abbrechen der Bestellung schlug mit dem folgenden Fehler fehl: *Sie haben den Artikel nicht abgebrochen.*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) verfügbar sind, in unserer Entwicklerdokumentation.
