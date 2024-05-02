---
title: '"ACSD-56193: [!DNL Fastly] Cache wird für die Aktualisierung des Inhalts-Staging nicht gelöscht.'
description: Wenden Sie den Patch ACSD-56193 an, um das Adobe Commerce-Problem zu beheben, bei dem das [!DNL Fastly] Der Cache wird für die Aktualisierung des Inhalts-Staging nicht gelöscht.
feature: Cache, GraphQL, Staging
role: Admin, Developer
exl-id: d4bbfafa-2d24-44cf-a08b-f7dd9111a65b
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-56193: [!DNL Fastly] Cache für die Aktualisierung des Inhalts-Staging nicht gelöscht

Der Patch ACSD-56193 behebt das Problem, bei dem der [!DNL Fastly] Der Cache wird für die Aktualisierung des Inhalts-Staging nicht gelöscht. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 ist installiert. Die Patch-ID ist ACSD-56193. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die [!DNL Fastly/Varnish] Cache für die Aktualisierung des Inhalts-Staging nicht gelöscht

<u>Zu reproduzierende Schritte</u>:

1. Installieren und Konfigurieren [!DNL Varnish] zwischenspeichern.
1. Erstellen Sie einen statischen Block mit einer geplanten Aktualisierung.
1. Erstellen Sie eine Kategorie, die den statischen Block einbettet.
1. Rufen Sie den Inhalt der Kategorie mithilfe der folgenden GraphQL-Abfrage ab:

   ```GraphQL
      query GetCategories($id: String!) {
         categoryList(filters: { category_uid: { eq: $id } }) 
       {
           meta_title
           meta_keywords
           meta_description
           description
           path
           cms_block {
             content
             identifier
             title
             __typename
           }
           __typename
       }
     }
     {"id":"Mwo="}
   ```

1. Führen Sie diese Abfrage mehrmals aus und stellen Sie sicher, dass die Antwort im [!DNL Varnish].
1. Führen Sie den Cron aus, um die geplante Änderung anzuwenden.
1. Führen Sie die oben genannte GraphQL-Abfrage erneut aus.
1. Erstellen Sie einen neuen Zeitplan für denselben statischen Baustein.
1. Wiederholen Sie die Schritte 5 bis 9.

<u>Erwartete Ergebnisse</u>:

Der aktualisierte Inhalt wird nach Ausführung der geplanten Aktualisierungen zurückgegeben.

<u>Tatsächliche Ergebnisse</u>:

Der veraltete Inhalt wird nach Ausführung der geplanten Aktualisierungen zurückgegeben.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
