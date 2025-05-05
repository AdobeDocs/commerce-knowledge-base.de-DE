---
title: 'MDVA-43726: Katalogpreisregel wird nach teilweiser Neuindizierung nicht angewendet'
description: Der Patch MDVA-43726 behebt das Problem, dass die Katalogpreisregel, die auf der Attributübereinstimmung auf Store-Ebene basiert, nach einer teilweisen Neuindizierung nicht angewendet werden kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-43726. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
exl-id: 70e7e1d2-e601-4fed-9274-a1a619de29e1
feature: Catalog Management, Categories, Orders, Price Rules
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# MDVA-43726: Katalogpreisregel wird nach teilweiser Neuindizierung nicht angewendet

Der Patch MDVA-43726 behebt das Problem, dass die Katalogpreisregel, die auf der Attributübereinstimmung auf Store-Ebene basiert, nach einer teilweisen Neuindizierung nicht angewendet werden kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-43726. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.3 - 2.4.2-p2

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Katalogpreisregel, die auf der Attributübereinstimmung auf Speicherebene basiert, kann nach einer teilweisen Neuindizierung nicht angewendet werden.

<u>Schritte zur Reproduktion</u>:

1. Setzen Sie den Indexermodus auf „Planmäßig ausgeführt“.
1. Erstellen Sie zwei konfigurierbare Produktattribute. Beispiel: Farbe (visuelles Farbfeld) und Größe (Textfeld).
1. Erstellen Sie ein konfigurierbares Produkt mit beiden in Schritt 2 erstellten Attributen.
1. Erstellen Sie nach dem Erstellen der Produkte **Attribut** Ja/Nein“ und machen Sie es in den Regelbedingungen sichtbar.
1. Fügen Sie dieses Attribut zum Standardattributsatz hinzu.
1. Erstellen Sie eine Katalogpreisregel, die angewendet werden soll, wenn dieses Attribut auf &quot;**&quot;** ist.
1. Öffnen Sie eines der einfachen Produkte im Zusammenhang mit dem konfigurierbaren Produkt.
1. Ändern Sie den Bereich für die Speicheransicht und aktualisieren Sie den Attributwert auf **Ja**.
1. Führen Sie die `CRON` aus und überprüfen Sie den Preis am Frontend.
1. Führen Sie eine vollständige Neuindizierung aus. Überprüfen Sie erneut den Preis am Frontend.
1. Aktualisieren Sie die konfigurierbare Produktkategorie.
1. Führen Sie die `CRON` aus und überprüfen Sie den Preis erneut am Frontend.

<u>Erwartete Ergebnisse</u>:

Die Katalogregel gilt korrekt ohne vollständige Neuindizierung mithilfe von inkrementellen Indexern.

<u>Tatsächliche Ergebnisse</u>:

Die Katalogregel gilt nicht, ohne eine vollständige Neuindizierung auszuführen.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) in unserer Entwicklerdokumentation.
