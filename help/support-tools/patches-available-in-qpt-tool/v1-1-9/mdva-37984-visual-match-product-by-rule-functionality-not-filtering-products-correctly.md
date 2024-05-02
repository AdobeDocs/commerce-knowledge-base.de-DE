---
title: "MDVA-37984: Visual Merchandiser funktioniert nicht ordnungsgemäß, wenn Staging-Updates angewendet werden"
description: Der Patch MDVA-37984 behebt das Problem, dass die Funktion "Produkt nach Regel abgleichen"des Visual Merchandiser die Produkte bei Anwendung von Staging-Updates nicht korrekt filtert. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-37984. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: d806b94c-3b22-4d4c-8afb-7b57a0ebfe46
feature: Categories, Merchandising, Products, Staging
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-37984: Visual Merchandiser funktioniert nicht ordnungsgemäß, wenn Staging-Updates angewendet werden

Der Patch MDVA-37984 behebt das Problem, dass die Funktion &quot;Produkt nach Regel abgleichen&quot;des Visual Merchandiser die Produkte bei Anwendung von Staging-Updates nicht korrekt filtert. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 ist installiert. Die Patch-ID lautet MDVA-37984. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Funktion &quot;Produkt nach Regel abgleichen&quot;des Visual Merchandiser filtert Produkte nicht richtig, wenn Staging-Updates angewendet werden.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein Zeitplanupdate für jedes vorhandene Produkt.
   * Legen Sie unterschiedliche Werte für `entity_id` und `row_id`.
1. Erstellen Sie ein neues konfigurierbares Produkt und dann ein einfaches Produkt (also das neue Produkt `entity_id` und `row_ids` auch unterschiedlich sind).
   * Um das Replizieren des Problems zu vereinfachen, legen Sie einen aussagekräftigen Qty-Wert für das einfache Produkt fest, z. B. 5000.
1. Gehen Sie zu einer Kategorie > **Produkte der Kategorie** und aktivieren **Produkte nach Regel abgleichen**.
1. Wählen Sie nun &quot;Menge&quot;als Attribut, &quot;Größer&quot;als Operator und &quot;4500&quot;als Wert aus.
1. Klicks **save**.

<u>Erwartete Ergebnisse</u>:

Das neu erstellte konfigurierbare Produkt wird aufgelistet.

<u>Tatsächliche Ergebnisse</u>:

Das neu erstellte konfigurierbare Produkt wird nicht aufgeführt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
