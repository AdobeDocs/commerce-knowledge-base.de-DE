---
title: 'ACSD-48771: Der WYSIWYG-Editor rendert Inhalte anders'
description: Wenden Sie den Patch ACSD-48771 an, um das Adobe Commerce-Problem zu beheben, bei dem der WYSIWYG-Editor Inhalte anders rendert.
exl-id: 6a856fa3-6099-4237-8d1c-e3735b8ca012
feature: Cache, Page Content
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# ACSD-48771: Der WYSIWYG-Editor rendert Inhalte anders

Der Patch ACSD-48771 behebt das Problem, dass der WYSIWYG-Editor Inhalte anders rendert. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 installiert ist. Die Patch-ID ist ACSD-48771. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der WYSIWYG-Editor rendert Inhalte anders.

<u>Schritte zur Reproduktion</u>:

1. Wechseln Sie zum Adobe Commerce-Administrator, erstellen Sie eine neue Seite mit einer Zeile mit drei Spalten und speichern Sie die Seite.
1. Aktualisieren Sie Adobe Commerce auf eine der neuesten Versionen.
1. Stellen Sie [!DNL Chrome] Browser so ein, dass Cache und Geschwindigkeit auf &quot;*3G“*.
1. Wechseln Sie erneut zur Bearbeitungsseite und aktualisieren Sie sie, bis die Spalten zu Zeilen werden.
1. Speichern Sie die Seite, während die Spalten in Zeilen angezeigt werden.

<u>Erwartete Ergebnisse</u>:

Der Admin Page Builder sollte keine Spalten in Zeilen anzeigen.

<u>Tatsächliche Ergebnisse</u>:

Spalten werden in verschiedenen Zeilen angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
