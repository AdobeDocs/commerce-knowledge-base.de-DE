---
title: 'MDVA-42326: Kunden erhalten nach Sitzungs-Timeout einen Fehler beim Auschecken'
description: Der Patch MDVA-42326 löst das Problem, dass Kunden nach dem Sitzungs-Timeout einen Fehler beim Checkout erhalten, auch wenn der persistente Warenkorb aktiviert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 installiert ist. Die Patch-ID lautet MDVA-42326. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
exl-id: bc9b71de-510d-4c4e-8b0d-9abf9a3e447f
feature: Checkout, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# MDVA-42326: Kunden erhalten nach Sitzungs-Timeout einen Fehler beim Auschecken

Der Patch MDVA-42326 löst das Problem, dass Kunden nach dem Sitzungs-Timeout einen Fehler beim Checkout erhalten, auch wenn der persistente Warenkorb aktiviert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 installiert ist. Die Patch-ID lautet MDVA-42326. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Kunden erhalten nach der Sitzungs-Zeitüberschreitung einen Fehler beim Auschecken, auch wenn der persistente Warenkorb aktiviert ist.

<u>Voraussetzungen</u>:

1. Gehen Sie zu **Konfiguration** > **Allgemein** > **Web** > **Standard-Cookie-Einstellungen** > **Cookie Lifetime** und setzen Sie auf **120**.
1. Gehen Sie zu **Konfiguration** > **Kunden** > **Kundenkonfiguration** > **Online-Kundenoptionen** und setzen Sie beide Werte auf **2**.
1. Wechseln Sie zu **Konfiguration** > **Kunden** > **Persistenter Warenkorb** und setzen Sie auf **Aktivieren**.
1. Gehen Sie zu **Konfiguration** > **Verkauf** > **Zahlungsmethoden** und deaktivieren Sie alle Zahlungsmethoden außer **Scheck/Zahlungsanweisung** (sie sollte aktiviert sein).

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich als Kunde an und fügen Sie einige Produkte zum Warenkorb hinzu.
1. Überprüfen Sie den Warenkorb.
1. Warten Sie zwei Minuten (in der Voraussetzung festgelegt). Die Sitzung sollte eine Zeitüberschreitung aufweisen.
1. Klicken Sie **Zum Auschecken gehen** und aktualisieren Sie die Seite nicht.
1. Checken Sie als Gast aus, geben Sie die Lieferadresse ein und wählen Sie eine Versandart.
1. Klicken Sie **Weiter**.
1. Klicken Sie auf **Seite &quot;** &amp; Zahlungen **auf „Bestellung**. Da nur eine Zahlungsmethode zulässig ist, sollte der Kunde die Bestellung aufgeben können, ohne die Zahlungsmethode auszuwählen.

<u>Erwartete Ergebnisse</u>:

Der Kunde sollte in der Lage sein, die Bestellung aufzugeben.

<u>Tatsächliche Ergebnisse</u>:

Der Kunde erhält die folgende Fehlermeldung: *Fehlgeschlagene Adressvalidierung: E-Mail hat ein falsches Format*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) in unserer Entwicklerdokumentation.
