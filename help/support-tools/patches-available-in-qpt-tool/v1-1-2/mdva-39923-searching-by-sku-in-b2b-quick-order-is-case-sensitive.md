---
title: 'MDVA-39923: Bei der Suche nach SKU in der B2B-Schnellbestellungsfunktion wird zwischen Groß- und Kleinschreibung unterschieden'
description: Der Patch MDVA-39923 behebt das Problem, dass Kunden einen Fehler erhalten, wenn sie die Bestellung nach SKU in der B2B-Schnellbestellungsfunktion mit einer anderen Groß-/Kleinschreibung als der durchsuchen, mit der der Name gespeichert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-39923. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
exl-id: 52e435df-28a7-49be-a257-7e5801601d57
feature: B2B, Catalog Management, Orders, Search
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# MDVA-39923: Bei der Suche nach SKU in der B2B-Schnellbestellungsfunktion wird zwischen Groß- und Kleinschreibung unterschieden

Der Patch MDVA-39923 behebt das Problem, dass Kunden einen Fehler erhalten, wenn sie die Bestellung nach SKU in der B2B-Schnellbestellungsfunktion mit einer anderen Groß-/Kleinschreibung als der durchsuchen, mit der der Name gespeichert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-39923. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Bei der Suche nach SKU in der B2B-Schnellbestellungsfunktion wird zwischen Groß- und Kleinschreibung unterschieden und ein Fehler angezeigt, wenn eine andere Groß-/Kleinschreibung als die verwendet wird, mit der die SKU gespeichert wird.

<u>Voraussetzungen</u>:

B2B-Module werden installiert.

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich bei Admin an und gehen Sie zu **Stores** > **Konfiguration** > **B2B**.
1. Aktivieren Sie **Freigegebener Katalog** und **Schnellbestellung**.
1. Erstellen eines Produkts mit SKU in Großbuchstaben, z. B. TEST20-1234
1. Zuweisen eines erstellten Produkts zum **freigegebenen Katalog**.
1. Melden Sie sich als Kunde an und klicken Sie auf **Schnellbestellung**.
1. Geben Sie die SKU in Kleinbuchstaben ein, z. B. test20-1234.

<u>Erwartete Ergebnisse</u>:

Das Produkt sollte unabhängig vom verwendeten Fall gefunden werden.

<u>Tatsächliche Ergebnisse</u>:

Die folgende Fehlermeldung wird empfangen: *1 Produkt(e) erfordern Ihre Aufmerksamkeit*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) in unserer Entwicklerdokumentation.
