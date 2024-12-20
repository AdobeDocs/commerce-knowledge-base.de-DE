---
title: 'ACSD-59378: Auf Store-Ebene [!DNL URL] schreibt fälschlicherweise während des Imports aktualisiert'
description: Wenden Sie den Patch ACSD-59378 an, um das Adobe Commerce-Problem zu beheben, bei dem Store-Level [!DNL URL] Rewrites beim Import falsch aktualisiert werden.
feature: Data Import/Export
role: Admin, Developer
exl-id: 4ba567e3-323d-4068-90cc-50aacd45d397
source-git-commit: 06f751e43ef825c0eb29cb9b42eb41f07c308625
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-59378: [!DNL URL] auf Store-Ebene schreibt beim Import falsch aktualisiert

Der Patch ACSD-59378 behebt das Problem, dass die Neuschreibungen auf der Store-Ebene [!DNL URL] beim Import falsch aktualisiert werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 installiert ist. Die Patch-ID ist ACSD-59378. Bitte beachten Sie, dass dieses Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p5

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5x (alle Versionen von 2.4.5)

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Neuschreibungen auf Speicherebene [!DNL URL] werden beim Import falsch aktualisiert.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein Produkt mit &quot;`url_key = key_default`&quot;im Bereich &quot;**Alle Store-Ansichten**&quot;.
1. Legen Sie `url_key = key_store` im Bereich **Standardspeicheransicht** fest.
1. Exportieren Sie das Produkt.
1. Importieren Sie eine [!DNL CSV] -Datei für dieses Produkt mit den folgenden Daten:
   * Die Spalte `store_view_code` ist auf *leer* eingestellt, sodass sie für den Bereich **Alle Store-Ansichten** gilt.
   * `url_key` ist auf den Standardschlüssel *`key_default`* gesetzt.

<u>Erwartete Ergebnisse</u>:

[!DNL URL] -Neuschreibungen werden nur für Store-Ansichten neu generiert, bei denen `url_key` nicht überschrieben wird (wobei die standardmäßige `url_key` gilt).

<u>Tatsächliche Ergebnisse</u>:

`key_store` [!DNL URL] Neuschreibungen werden gelöscht, aber die [!DNL URL] Neuschreibungen auf der Ebene **Standard-Store-Ansicht** für das Produkt sind weiterhin auf *`key_store`* eingestellt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
