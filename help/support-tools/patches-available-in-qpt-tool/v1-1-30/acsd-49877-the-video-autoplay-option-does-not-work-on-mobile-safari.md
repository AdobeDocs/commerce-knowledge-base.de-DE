---
title: '"ACSD-49877: Video-Autoplay funktioniert nicht auf Mobilgeräten [!DNL Safari]'''
description: Wenden Sie den Patch ACSD-49877 an, um das Adobe Commerce-Problem zu beheben, bei dem die Option zur automatischen Videowiedergabe auf einem Mobilgerät nicht funktioniert [!DNL Safari] wenn das Video direkt mit einer Remote-Videodatei verknüpft ist.
exl-id: 454f7cec-29b9-485b-93be-2a4f2eb77da7
feature: CMS
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-49877: Video-Autoplay funktioniert nicht auf Mobilgeräten [!DNL Safari]

ACSD-49877 behebt das Problem, bei dem die automatische Wiedergabe auf einem Mobilgerät [!DNL Safari] funktioniert nicht, wenn das Video direkt mit einer Remote-Videodatei verknüpft ist. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 installiert ist. Die Patch-ID lautet ACSD-49877. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die [!magento/quality-patches] auf die neueste Version zu aktualisieren und die Kompatibilität auf der [ zu überprüfen.[!DNL Quality Patches Tool]: Suchen Sie nach Patches]. Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die automatische Videowiedergabe funktioniert nicht auf einem Mobilgerät [!DNL Safari] wenn das Video direkt mit einer Remote-Videodatei und nicht mit einem Streaming-Dienst verknüpft ist.

<u>Voraussetzungen</u>:
[!DNL Page Builder] installiert sind.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine neue CMS-Seite und bearbeiten Sie die **[!UICONTROL Content Value]** mit [!DNL Page Builder].
1. Hinzufügen einer *Registerkarte* -Element zum Inhalt hinzufügen und eine *Videoelement* innerhalb der *Registerkarte*.
1. Klicken Sie nun auf die Zahnradschaltfläche, um die *Videoelement*.
1. Fügen Sie einen Link zu einer MP4-Videodatei zum [!UICONTROL Video URL] -Feld.
1. Markieren Sie die **[!UICONTROL Autoplay]** Feld als *Ja*.
1. Klicks **[!UICONTROL Save]**.
1. Öffnen Sie die kürzlich erstellte Seite auf [!DNL Safari] Verwendung einer iPhone.

<u>Erwartete Ergebnisse</u>

Die Option &quot;Autoplay&quot;funktioniert mit [!DNL Safari] Verwendung einer iPhone.

<u>Tatsächliche Ergebnisse</u>

Die Option &quot;Autoplay&quot;funktioniert nicht mit [!DNL Safari] Verwendung einer iPhone.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
