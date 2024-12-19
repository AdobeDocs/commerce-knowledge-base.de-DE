---
title: 'MDVA-41350: Ausnahme, wenn Admin Produkte außerhalb ihres Zugriffs hinzufügt'
description: Mit dem Patch MDVA-41350 wird das Problem behoben, dass ein Ausnahmefehler anstelle einer Benachrichtigung mit eingeschränktem Zugriff ausgelöst wird, wenn ein Administrator ein Produkt in der Reihenfolge nach SKU hinzufügt, auf das er keinen Zugriff hat. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 installiert ist. Die Patch-ID lautet MDVA-41350. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
exl-id: 3a96d029-5350-4dd6-aad3-2f2cdd5e65ac
feature: Admin Workspace, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-41350: Ausnahme, wenn Admin Produkte außerhalb ihres Zugriffs hinzufügt

Mit dem Patch MDVA-41350 wird das Problem behoben, dass ein Ausnahmefehler anstelle einer Benachrichtigung mit eingeschränktem Zugriff ausgelöst wird, wenn ein Administrator ein Produkt in der Reihenfolge nach SKU hinzufügt, auf das er keinen Zugriff hat. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 installiert ist. Die Patch-ID lautet MDVA-41350. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wenn ein Admin-Benutzer mit eingeschränktem Zugriff ein Produkt über eine SKU außerhalb seines Zugriffs in der Bestellung hinzufügt, tritt eine Ausnahme anstelle einer Meldung auf, die den Benutzer über seinen eingeschränkten Zugriff informiert.

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich bei Admin als Benutzer an, der nur Zugriff auf eine bestimmte Website hat.
1. Gehen Sie zu **Verkauf** > **Bestellungen** und klicken Sie auf **Neue Bestellung erstellen**.
1. Kunden- und Shop-Ansicht auswählen.
1. Klicken Sie auf **Produkte hinzufügen nach SKU**.
1. Suchen Sie nach einer SKU, die keiner Website zugewiesen ist oder der Website, auf die Sie Zugriff haben, nicht zugewiesen ist.
1. Klicken Sie **Zur Bestellung hinzufügen**.

<u>Erwartete Ergebnisse</u>:

Eine entsprechende Fehlermeldung wird angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Eine Ausnahme tritt auf.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in unserer Entwicklerdokumentation.
