---
title: 'MDVA-37984: Visual Merchandiser funktioniert nicht ordnungsgemäß, wenn Staging-Aktualisierungen angewendet werden'
description: Der Patch MDVA-37984 löst das Problem, dass die Funktion „Produkt nach Regel abgleichen“ von Visual Merchandiser Produkte nicht korrekt filtert, wenn Staging-Updates angewendet werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-37984. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
exl-id: d806b94c-3b22-4d4c-8afb-7b57a0ebfe46
feature: Categories, Merchandising, Products, Staging
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-37984: Visual Merchandiser funktioniert nicht ordnungsgemäß, wenn Staging-Aktualisierungen angewendet werden

Der Patch MDVA-37984 löst das Problem, dass die Funktion „Produkt nach Regel abgleichen“ von Visual Merchandiser Produkte nicht korrekt filtert, wenn Staging-Updates angewendet werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-37984. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Funktion „Produkt nach Regel abgleichen“ des visuellen Merchandisers filtert Produkte nicht korrekt, wenn Staging-Aktualisierungen angewendet werden.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine Zeitplanaktualisierung für ein vorhandenes Produkt.
   * Legen Sie unterschiedliche Werte für `entity_id` und `row_id` fest.
1. Erstellen Sie ein neues konfigurierbares Produkt und dann ein einfaches Produkt (sodass sich die neuen `entity_id` und `row_ids` ebenfalls unterscheiden).
   * Um das Replizieren des Problems zu vereinfachen, legen Sie einen unterscheidbaren Mengenwert für das einfache Produkt fest, z. B. 5.000.
1. Navigieren Sie zu Kategorie > **Produkte in Kategorie** und aktivieren Sie **Produkte nach Regel abgleichen**.
1. Wählen Sie nun als Attribut „Menge“, als Operator „Größer“ und als Wert „4500“.
1. Klicken Sie auf **Speichern**.

<u>Erwartete Ergebnisse</u>:

Das neu erstellte konfigurierbare Produkt wird aufgelistet.

<u>Tatsächliche Ergebnisse</u>:

Das neu erstellte konfigurierbare Produkt wird nicht aufgeführt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) in unserer Entwicklerdokumentation.
