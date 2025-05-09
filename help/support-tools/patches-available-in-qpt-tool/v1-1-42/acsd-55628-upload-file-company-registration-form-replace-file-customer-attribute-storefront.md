---
title: 'ACSD-55628: Datei wird auf dem Unternehmensregistrierungsformular hochgeladen; Datei für Kundenattribut in Storefront wird ersetzt'
description: Wenden Sie den Patch ACSD-55628 an, um das Problem zu beheben, dass Adobe Commerce eine -Datei in das Unternehmensregistrierungsformular hochlädt und eine -Datei durch ein Kundenattribut in der Storefront ersetzt.
feature: Storefront, Attributes, B2B, Customers
role: Admin, Developer
exl-id: ca85b459-f72b-4663-85af-1f793935fe7e
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-55628: Datei wird auf dem Unternehmensregistrierungsformular hochgeladen; Datei für Kundenattribut in Storefront wird ersetzt

>[!NOTE]
>
>Dieser Patch ersetzt [ACSD-51240](/help/support-tools/patches-available-in-qpt-tool/v1-1-33/acsd-51240-uploaded-file-missing-while-registering-via-company-registration-form.md).

Mit dem Patch ACSD-55628 wird das Problem behoben, dass eine Datei auf das Unternehmensregistrierungsformular hochgeladen und eine Datei durch ein Kundenattribut in der Storefront ersetzt wurde. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 installiert ist. Die Patch-ID ist ACSD-55628. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p2 &lt; 2.4.5 und 2.4.5-p1 &lt; 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Datei für ein Kundenattribut in der Storefront kann nicht ersetzt werden.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein neues Kundenattribut mit den folgenden Werten:

   * *[!UICONTROL Input Type]*: *[!UICONTROL File (Attachment)]*
   * *[!UICONTROL Show on Storefront]*: *Ja*
   * *[!UICONTROL Forms to Use In]*: *Alle verfügbaren Optionen*

1. Melden Sie sich als Kunde an der Storefront an und öffnen Sie **[!UICONTROL My Account]** > **[!UICONTROL Account Information]**.
1. Ein neues Bild hochladen und speichern.
1. Aktualisieren Sie die Seite. Löschen Sie das alte Bild und laden Sie ein neues hoch. Speichern Sie die Änderungen.

<u>Erwartete Ergebnisse</u>:

Das neue Bild wird gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Das alte Bild wird weiterhin angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
