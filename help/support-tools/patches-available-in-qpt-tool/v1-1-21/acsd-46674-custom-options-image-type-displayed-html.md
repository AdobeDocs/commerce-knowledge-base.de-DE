---
title: 'ACSD-46674: Benutzerdefinierte Optionen des Bildtyps, die als HTML in Kunden-E-Mails angezeigt werden'
description: Wenden Sie den Patch ACSD-46674 an, um das Problem in Adobe Commerce zu beheben, bei dem benutzerdefinierte Optionen des Bildtyps als HTML in Kunden-E-Mails angezeigt werden.
exl-id: b4941dd0-bb3a-4805-9631-1d256a92f461
feature: Communications, Personalization
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-46674: Benutzerdefinierte Optionen des Bildtyps, die als HTML in Kunden-E-Mails angezeigt werden

Mit dem Patch ACSD-46674 wird das Problem behoben, dass die benutzerdefinierten Optionen eines Bildtyps in Kunden-E-Mails als HTML angezeigt werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21 installiert ist. Die Patch-ID ist ACSD-46674. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Benutzerdefinierte Optionen eines Bildtyps werden in Kunden-E-Mails als HTML angezeigt.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein Produkt mit einer benutzerdefinierten Option.
   * Optionstyp: *Datei*
   * Kompatible Dateierweiterungen: *png, jpg, gif*
   * Erforderlich: *Ja*
1. Bestellen Sie dieses Produkt mit einem Bild, das als benutzerdefinierte Option hochgeladen wurde.
1. Erstellen Sie eine Rechnung für die in Schritt 2 erstellte Bestellung.
1. Erstellen Sie eine Gutschrift.
1. Überprüfen Sie alle Bestätigungs-E-Mails.

<u>Erwartete Ergebnisse</u>:

In den Bestätigungs-E-Mails wird das hochgeladene Bild angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Die Bestätigungs-E-Mails enthalten Nur-HTML-Code anstelle des benutzerdefinierten Optionsbildes des Produkts.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tools] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in [!DNL QPT] verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
