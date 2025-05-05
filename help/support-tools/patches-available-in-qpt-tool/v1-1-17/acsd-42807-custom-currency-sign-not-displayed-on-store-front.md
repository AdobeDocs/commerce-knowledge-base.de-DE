---
title: 'ACSD-42807: Benutzerdefiniertes Währungszeichen wird nicht auf der Storefront angezeigt'
description: Der Patch ACSD-42807 behebt das Problem, dass das benutzerdefinierte Währungszeichen nicht auf der Storefront angezeigt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 installiert ist. Die Patch-ID ist ACSD-42807. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.
exl-id: 21bd17b4-d9d8-4c40-8f89-d6f7b930b475
feature: Storefront
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-42807: Benutzerdefiniertes Währungszeichen wird nicht auf der Storefront angezeigt

Der Patch ACSD-42807 behebt das Problem, dass das benutzerdefinierte Währungszeichen nicht auf der Storefront angezeigt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 installiert ist. Die Patch-ID ist ACSD-42807. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.4

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das benutzerdefinierte Währungszeichen wird nicht auf der Storefront angezeigt.

<u>Schritte zur Reproduktion</u>:

1. Wechseln Sie zu **Store** > **Einstellungen** > **Konfigurationen** > **Allgemein** > **Währungseinstellungen** und wählen Sie eine benutzerdefinierte Währung aus. Beispielsweise &quot;**Peso**.
1. Navigieren Sie zu **Store** > **Einstellungen** > **Konfigurationen** > **Allgemein** > **Gebietsschema-Optionen** und wählen Sie **Spanisch (Mexiko)**.
1. Wechseln Sie zu **Store** > **Währungssymbole** und konfigurieren Sie das Währungssymbol auf **MX$**.
1. Überprüfen Sie das Währungssymbol am Frontend.

<u>Erwartete Ergebnisse</u>:

Das standardmäßige Währungssymbol ist „MX$&quot;, wobei die Währung als „mexikanischer Peso“ und das Gebietsschema als „Spanisch (Mexiko)“ festgelegt ist.

<u>Tatsächliche Ergebnisse</u>:

Das standardmäßige Währungssymbol zeigt &quot;$&quot; an.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) in unserer Entwicklerdokumentation.
