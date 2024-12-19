---
title: 'MDVA-38728: Durch die Änderung der Produktansicht wird die URL für die Haupt-Website neu geschrieben'
description: Der MDVA-38728 Patch löst das Problem, dass eine Änderung der Produktsichtbarkeit der zweiten Website zu einer URL-Umschreibung für die Haupt-Website führt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-38728. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
exl-id: ad1d5f82-294d-485d-acd3-28c3cd0fbf56
feature: Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# MDVA-38728: Durch die Änderung der Produktansicht wird die URL für die Haupt-Website neu geschrieben

Der MDVA-38728 Patch löst das Problem, dass eine Änderung der Produktsichtbarkeit der zweiten Website zu einer URL-Umschreibung für die Haupt-Website führt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-38728. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.2 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wenn Sie die Sichtbarkeit des Produkts auf der zweiten Website ändern, wird eine URL-Umschreibung für die Haupt-Website erstellt.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine zusätzliche Website, einen Store und eine Storeview.
1. Erstellen Sie ein einfaches Produkt.
1. Legen Sie die Sichtbarkeit auf &quot;**einzeln sichtbar“**.
1. Produkt nur der zweiten Website zuweisen.
1. Füllen Sie alle anderen erforderlichen Felder aus.
1. Speichern Sie das Produkt.
1. MySQL-Warteschlangen starten:

   ```mysql
   bin/magento queue:consumers:start product_action_attribute.update &
   bin/magento queue:consumers:start product_action_attribute.website.update &
   ```

1. Zur Produktliste.
1. Wählen Sie das erstellte Produkt aus und aktualisieren Sie das Attribut für die Sichtbarkeit, indem Sie das globale Update für Katalog und Suche verwenden.
1. Überprüfen Sie die URL-Umschreibung.

<u>Erwartete Ergebnisse</u>:

Die Neufassung wird für die zweite Website erstellt, der das Produkt zugewiesen ist.

<u>Tatsächliche Ergebnisse</u>:

Die Neufassung wird für die Haupt-Website erstellt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in unserer Entwicklerdokumentation.
