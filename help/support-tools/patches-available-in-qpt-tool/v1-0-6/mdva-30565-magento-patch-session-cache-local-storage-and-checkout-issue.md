---
title: "MDVA-30565: Problem mit lokalem Speicher im Sitzungscache und Checkout"
description: Der Patch MDVA-30565 löst das Problem mit lokalem Sitzungscache-Speicher und Checkout. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 installiert ist.
exl-id: f0693f0c-fc6b-44af-a6a0-ebfa973bca65
feature: Cache, Checkout, Orders, Storage
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# MDVA-30565: Problem mit lokalem Speicher im Sitzungscache und Checkout

Der Patch MDVA-30565 löst das Problem mit lokalem Sitzungscache-Speicher und Checkout. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 installiert ist.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce auf Cloud-Infrastruktur 2.3.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.2 - 2.3.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Warenkorbelemente können weiterhin auf der Warenkorbseite angezeigt werden, wenn eine Kundensitzung mit einem Timeout beendet wird. Dies führt zu einem geschätzten Versandmethodenfehler, bei dem keine Versandmethoden für den Gastkasse verfügbar sind.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie den beständigen Warenkorb in der Commerce Admin. (**Aktivieren der Persistenz** = &quot;*Ja*&quot;)
1. Melden Sie sich als Kunde im Frontend an. Dadurch wird die `persistent_shopping_cart` und initiiert eine persistente Sitzung.
1. Fügen Sie ein Produkt in den Warenkorb.
1. Warten Sie, bis die Frontend-Sitzung abgelaufen ist, oder löschen Sie die `PHPSESSID` Cookie.
1. Jetzt sind Sie ein Gastbenutzer, aber wenn Sie zum Warenkorb gehen, können Sie weiterhin das Produkt sehen, das als angemeldeter Kunde hinzugefügt wurde.
1. Entfernen Sie das Produkt aus dem Warenkorb, und jetzt ist der Warenkorb leer. Sie sehen, dass Adobe Commerce die `persistent_shopping_cart` -Cookie in diesem Ereignis.
1. Fügen Sie ein neues Produkt in den Warenkorb und wechseln Sie zur Warenkorbseite.
1. In der Browser-Konsole wird nun Folgendes angezeigt: `V1/guest-carts/4/estimate-shipping-methods` Anfrage gibt jetzt eine 404-Antwort mit Nachricht zurück `{"message":"No such entity        with %fieldName = %fieldValue","parameters":{"fieldName":"cartId","fieldValue":0}}`

<u>Erwartete Ergebnisse</u>:

Die Anfrage für die geschätzte Versandmethode liefert korrekte Ergebnisse.

<u>Tatsächliche Ergebnisse</u>:

Die Anfrage zur Schätzung der Versandmethode schlägt mit einem Fehler wie dem folgenden fehl: &quot;*Für diese Bestellung sind derzeit leider keine Angebote verfügbar.*&quot;

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
