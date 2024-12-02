---
title: 'MDVA-37984: Visual Merchandiser funktioniert nicht ordnungsgemäß, wenn Staging-Updates angewendet werden'
description: Der Patch MDVA-37984 behebt das Problem, dass die Funktion "Produkt nach Regel abgleichen"des Visual Merchandiser die Produkte bei Anwendung von Staging-Updates nicht korrekt filtert. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-37984. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: d806b94c-3b22-4d4c-8afb-7b57a0ebfe46
feature: Categories, Merchandising, Products, Staging
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-37984: Visual Merchandiser funktioniert nicht ordnungsgemäß, wenn Staging-Updates angewendet werden

Der Patch MDVA-37984 behebt das Problem, dass die Funktion &quot;Produkt nach Regel abgleichen&quot;des Visual Merchandiser die Produkte bei Anwendung von Staging-Updates nicht korrekt filtert. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-37984. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Funktion &quot;Produkt nach Regel abgleichen&quot;des Visual Merchandiser filtert Produkte nicht richtig, wenn Staging-Updates angewendet werden.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein Zeitplanupdate für jedes vorhandene Produkt.
   * Legen Sie unterschiedliche Werte für `entity_id` und `row_id` fest.
1. Erstellen Sie ein neues konfigurierbares Produkt und dann ein einfaches Produkt (also unterscheiden sich auch das neue Produkt `entity_id` und `row_ids`).
   * Um das Replizieren des Problems zu vereinfachen, legen Sie einen aussagekräftigen Qty-Wert für das einfache Produkt fest, z. B. 5000.
1. Gehen Sie zu einer Kategorie > **Produkte in Kategorie** und aktivieren Sie die Option **Produkte nach Regel abgleichen**.
1. Wählen Sie nun &quot;Menge&quot;als Attribut, &quot;Größer&quot;als Operator und &quot;4500&quot;als Wert aus.
1. Klicken Sie auf **save**.

<u>Erwartete Ergebnisse</u>:

Das neu erstellte konfigurierbare Produkt wird aufgelistet.

<u>Tatsächliche Ergebnisse</u>:

Das neu erstellte konfigurierbare Produkt wird nicht aufgeführt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) verfügbar sind, in unserer Entwicklerdokumentation.
