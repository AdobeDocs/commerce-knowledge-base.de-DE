---
title: 'ACSD-56760: Admin-Benutzende sind auf eine bestimmte Website beschränkt und können keine Produkte sortieren oder hinzufügen'
description: Wenden Sie den Patch ACSD-56760 an, um das Adobe Commerce-Problem zu beheben, bei dem der Admin-Benutzer, der auf eine bestimmte Website beschränkt ist und keine neuen Produkte innerhalb einer Kategorie sortieren oder hinzufügen kann, falls der Webstore eine eigene Stammkategorie hat.
role: Admin
exl-id: fc1898ce-dcd7-4c0b-bef0-445219e8455f
source-git-commit: a8e1b3b5b9de41c62bf819ef68ac9f89626483a1
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# ACSD-56760: Admin-Benutzende sind auf eine bestimmte Website beschränkt und können keine Produkte sortieren oder hinzufügen

Mit dem Patch ACSD-56760 wird das Problem behoben, dass der Admin-Benutzer, der auf eine bestimmte Website beschränkt ist und keine neuen Produkte innerhalb einer Kategorie sortieren oder hinzufügen kann, falls der Webstore eine eigene Stammkategorie hat. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.47 installiert ist. Die Patch-ID ist ACSD-56760. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Admin-Benutzer, der auf eine bestimmte Website beschränkt ist und keine neuen Produkte innerhalb einer Kategorie sortieren oder hinzufügen kann, falls der Webstore eine eigene Stammkategorie hat.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie *2*-Websites.
1. Erstellen Sie eine **[!UICONTROL restricted admin user]**, die nur Zugriff auf die *1*-Website hat.
1. Melden Sie sich als **[!UICONTROL restricted admin user]** an und versuchen Sie, die Produktpositionen in einer Kategorie zu ändern.

*Fall 1*:

* *2* Stores.
* *2* Stammkategorien, wobei jede Website ihrem eigenen Kategoriestamm zugewiesen ist.

*Fall 2*:

* *2* Stores.
* Beide Websites haben nur eine *1*-Stammkategorie.

<u>Erwartete Ergebnisse</u>:

* *Fall 1*: Der Admin mit Zugriffsbeschränkung sollte in der Lage sein, Produkte innerhalb der verfügbaren Kategorie zu sortieren.
* *Fall 2*: Der Admin mit Zugriffsbeschränkung kann Produkte nicht innerhalb der verfügbaren Kategorie sortieren, da dies auch den eingeschränkten Store betrifft.

<u>Tatsächliche Ergebnisse</u>:

* *Fall 1*: Der Administrator mit Zugriffsbeschränkung kann Produkte nicht innerhalb der verfügbaren Kategorie sortieren.
* *Fall 2*: Der eingeschränkte Administrator kann Produkte innerhalb der verfügbaren Kategorie sortieren, was sich auf die eingeschränkten Stores auswirkt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
