---
title: "ACSD-46674: benutzerdefinierte Optionen des Bildtyps, die in E-Mails von Kunden als HTML angezeigt werden"
description: Wenden Sie den Patch ACSD-46674 an, um das Adobe Commerce-Problem zu beheben, bei dem benutzerdefinierte Optionen des Bildtyps in E-Mails von Kunden als HTML angezeigt wurden.
exl-id: b4941dd0-bb3a-4805-9631-1d256a92f461
feature: Communications, Personalization
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-46674: benutzerdefinierte Optionen des Bildtyps, die in E-Mails von Kunden als HTML angezeigt werden

Der Patch ACSD-46674 behebt das Problem, dass die benutzerdefinierten Optionen eines Bildtyps in E-Mails von Kunden als HTML angezeigt werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21 installiert ist. Die Patch-ID ist ACSD-46674. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Benutzerdefinierte Optionen eines Bildtyps werden in E-Mails von Kunden als HTML angezeigt.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein Produkt mit einer benutzerdefinierten Option.
   * Optionstyp: *Datei*
   * Kompatible Dateierweiterungen: *png, jpg, gif*
   * Erforderlich: *Ja*
1. Platzieren Sie eine Bestellung für dieses Produkt mit einem Bild, das als benutzerdefinierte Option hochgeladen wurde.
1. Erstellen Sie eine Rechnung für die in Schritt 2 erstellte Bestellung.
1. Erstellen Sie ein Kreditmemo.
1. Prüfen Sie alle Bestätigungs-E-Mails.

<u>Erwartete Ergebnisse</u>:

In den Bestätigungs-E-Mails wird das hochgeladene Bild angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Die Bestätigungs-E-Mails enthalten einfachen HTML-Code anstelle des benutzerdefinierten Produktoptionsbilds.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tools] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in [!DNL QPT] verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
