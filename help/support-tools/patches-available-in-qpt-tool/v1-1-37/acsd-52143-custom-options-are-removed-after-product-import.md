---
title: 'ACSD-52143: Benutzerdefinierte Optionen werden nach dem Produktimport entfernt'
description: Wenden Sie den Patch ACSD-52143 an, um das Adobe Commerce-Problem zu beheben, bei dem die Anpassungsoptionen nach dem Produktimport entfernt werden.
feature: Data Import/Export
role: Admin, Developer
exl-id: 7dde1efe-37a3-443f-9ce1-82cf1b3d9da7
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-52143: Benutzerdefinierte Optionen werden nach dem Produktimport entfernt

Der Patch ACSD-52143 behebt das Problem, dass die benutzerdefinierten Optionen nach dem Produktimport entfernt werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.37 installiert ist. Die Patch-ID ist ACSD-52143. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6 - p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die benutzerdefinierten Optionen werden nach dem Produktimport entfernt.

<u>Zu reproduzierende Schritte</u>:

1. Wechseln Sie zu &quot;**[!UICONTROL Store]**&quot;> &quot;**[!UICONTROL All Stores]**&quot;und richten Sie eine Instanz mit mehreren Stores ein (eine Website mit zwei Store-Ansichten).
1. Gehen Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]** und erstellen Sie zwei Produkte mit [!UICONTROL Customizable Options].
1. Fügen Sie jedem Produkt den Wert [!UICONTROL Customizable Option] hinzu.
1. Wechseln Sie zur zweiten Store-Ansicht und ändern Sie den Produktnamen für jedes Produkt.
1. Gehen Sie zu **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]** und exportieren Sie die beiden von Ihnen erstellten Produkte.
1. Laden Sie die CSV-Datei herunter.
1. Gehen Sie zu **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]** und importieren Sie die Datei erneut.
1. Überprüfen Sie beide Produkte.

<u>Erwartete Ergebnisse</u>:

Die benutzerdefinierten Optionen werden nach dem Produktimport nicht entfernt.

<u>Tatsächliche Ergebnisse</u>:

Die Zolloptionen werden nach der Einfuhr des Erzeugnisses entfernt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
