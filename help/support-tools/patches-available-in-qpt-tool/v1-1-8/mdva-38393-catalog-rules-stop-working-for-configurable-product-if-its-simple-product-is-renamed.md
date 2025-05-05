---
title: 'MDVA-38393: Katalogregeln funktionieren für konfigurierbare Produkte nicht mehr, wenn deren einfaches Produkt umbenannt wird'
description: Der Patch MDVA-38393 behebt das Problem, dass Katalogregeln für ein konfigurierbares Produkt nicht mehr funktionieren, wenn dessen einfaches Produkt umbenannt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 installiert ist. Die Patch-ID lautet MDVA-38393. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
exl-id: a20856c4-8aff-427b-a404-7afe706be06f
feature: Catalog Management, Categories, Configuration, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# MDVA-38393: Katalogregeln funktionieren für konfigurierbare Produkte nicht mehr, wenn deren einfaches Produkt umbenannt wird

Der Patch MDVA-38393 behebt das Problem, dass Katalogregeln für ein konfigurierbares Produkt nicht mehr funktionieren, wenn dessen einfaches Produkt umbenannt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 installiert ist. Die Patch-ID lautet MDVA-38393. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Katalogregeln funktionieren für ein konfigurierbares Produkt nicht mehr, wenn dessen einfaches Produkt umbenannt wird.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein konfigurierbares Produkt mit einem zugehörigen einfachen Produkt.
1. Erstellen Sie eine Kategorie.
1. Weisen Sie der neuen Kategorie nur das konfigurierbare Produkt zu.
1. Erstellen neuer Katalogregeln:
   * Bedingung = Kategorie enthält \&lt;neue Kategorie-ID>
   * Aktion = 50 % Rabatt
   * Aktiv = Ja
1. Neuindizierung durchführen.
1. Überprüfen Sie das konfigurierbare Produkt im Frontend (der Rabatt sollte angewendet werden).
1. Überprüfen Sie die `catalogrule_product` Tabelle (das einfache Produkt sollte einen Rabatt haben).
1. Wechseln Sie zum Administrator und ändern Sie den Namen des einfachen Produkts. Dadurch würde der `catalogrule_product_cl`-Tabelle ein Datensatz hinzugefügt.
1. Führen Sie den Cron- oder `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1` aus.
1. Überprüfen Sie die `catalogrule_product`.

<u>Erwartete Ergebnisse</u>:

Das konfigurierbare Produkt hat einen Rabatt.

<u>Tatsächliche Ergebnisse</u>:

* Die für die einfachen Produkte erstellten Rabattdatensätze fehlen in der `catalogrule_product`.
* Das konfigurierbare Produkt am Frontend hat den vollen Originalpreis.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) in unserer Entwicklerdokumentation.
