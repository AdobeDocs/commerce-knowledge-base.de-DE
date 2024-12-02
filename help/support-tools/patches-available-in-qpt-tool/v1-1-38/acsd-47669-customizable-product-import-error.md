---
title: 'ACSD-47669: Interner Server-Fehler beim Importieren von Produkten mit anpassbaren Optionen'
description: Wenden Sie den Patch ACSD-47669 an, um das Adobe Commerce-Problem zu beheben, bei dem beim Importieren von Produkten mit anpassbaren Optionen ein interner Serverfehler auftritt.
feature: Products
role: Admin, Developer
exl-id: 14afbd71-075a-4264-8da2-dbbd93f472a1
source-git-commit: 66e56b9ba31fd2c5d3f8a330f09d8e94df77b17d
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-47669: Interner Server-Fehler beim Importieren von Produkten mit anpassbaren Optionen

Der Patch ACSD-47669 behebt das Problem, bei dem während des Produktimports mit anpassbaren Optionen ein interner Server-Fehler auftritt. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.38 installiert ist. Die Patch-ID ist ACSD-47669. Bitte beachten Sie, dass das Problem bereits in Adobe Commerce 2.4.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.5-p4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Beim Importieren von Produkten mit anpassbaren Optionen tritt ein interner Server-Fehler auf.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine zusätzliche Store-Ansicht. Stellen Sie sicher, dass Sie über 2 Store-Ansichten verfügen, z. B. en, UK.
1. Erstellen Sie zwei einfache Produkte, z. B. prod1 und prod2.
1. Bereiten Sie eine CSV-Datei vor, die benutzerdefinierte Optionen für beide Produkte in jeder Store-Ansicht und für den Bereich **Alle Store-Ansicht** hinzufügt. Importieren Sie diese CSV-Datei.
1. Bereiten Sie eine weitere CSV-Datei vor, die zwei Datensätze enthält. Der erste Datensatz sollte darin bestehen, die benutzerdefinierten Optionen von &quot;prod1&quot;speziell für den Umfang der britischen Store-Ansicht zu aktualisieren, und der zweite Datensatz sollte darin bestehen, die benutzerdefinierten Optionen von &quot;prod2&quot;für den Bereich **Alle Store-Ansicht** zu aktualisieren. Importieren Sie diese zweite CSV-Datei.

<u>Erwartete Ergebnisse</u>:

Sie sollten in der Lage sein, die Optionen ohne Fehler anzupassen.

<u>Tatsächliche Ergebnisse</u>:

Ein Fehler wegen Verletzung der Integritätseinschränkung tritt auf.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
