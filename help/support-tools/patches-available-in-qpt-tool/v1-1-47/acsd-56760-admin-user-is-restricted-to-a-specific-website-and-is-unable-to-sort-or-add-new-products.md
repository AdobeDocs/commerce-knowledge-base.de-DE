---
title: "ACSD-56760: Admin-Benutzer ist auf eine bestimmte Website beschränkt und kann keine neuen Produkte sortieren oder hinzufügen."
description: Wenden Sie den Patch ACSD-56760 an, um das Adobe Commerce-Problem zu beheben, bei dem der Admin-Benutzer, der auf eine bestimmte Website beschränkt ist und keine neuen Produkte innerhalb einer Kategorie sortieren oder hinzufügen kann, falls der Webstore über eine eigene Stammkategorie verfügt.
role: Admin
exl-id: fc1898ce-dcd7-4c0b-bef0-445219e8455f
source-git-commit: a8e1b3b5b9de41c62bf819ef68ac9f89626483a1
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# ACSD-56760: Der Administrator ist auf eine bestimmte Website beschränkt und kann keine neuen Produkte sortieren oder hinzufügen

Der Patch ACSD-56760 behebt das Problem, dass der Admin-Benutzer, der auf eine bestimmte Website beschränkt ist und keine neuen Produkte innerhalb einer Kategorie sortieren oder hinzufügen kann, falls der Webstore über eine eigene Stammkategorie verfügt. Dieser Patch ist verfügbar, wenn die Variable [!DNL Quality Patches Tool (QPT)] 1.1.47 ist installiert. Die Patch-ID ist ACSD-56760. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6 - p4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Administrator-Benutzer, der auf eine bestimmte Website beschränkt ist und keine neuen Produkte innerhalb einer Kategorie sortieren oder hinzufügen kann, falls der Webstore über eine eigene Stammkategorie verfügt.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen *2* Websites.
1. Erstellen Sie eine **[!UICONTROL restricted admin user]** nur mit Zugriff auf *1* Website.
1. Als **[!UICONTROL restricted admin user]** und versuchen Sie, die Produktpositionen in einer Kategorie zu ändern.

*1. Fall*:

* *2* Stores.
* *2* Stammkategorien, jede Website, die dem eigenen Kategoriestamm zugewiesen ist.

*2. Fall*:

* *2* Stores.
* Nur *1* Die Stammkategorie wird beiden Websites zugewiesen.

<u>Erwartete Ergebnisse</u>:

* *1. Fall*: Der eingeschränkte Administrator sollte Produkte innerhalb der verfügbaren Kategorie sortieren können.
* *2. Fall*: Der eingeschränkte Administrator kann keine Produkte innerhalb der verfügbaren Kategorie sortieren, da sich dies auch auf den eingeschränkten Speicher auswirkt.

<u>Tatsächliche Ergebnisse</u>:

* *1. Fall*: Der eingeschränkte Administrator kann keine Produkte innerhalb der verfügbaren Kategorie sortieren.
* *2. Fall*: Der eingeschränkte Administrator kann Produkte innerhalb der verfügbaren Kategorie sortieren, was sich auf die eingeschränkten Stores auswirkt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
