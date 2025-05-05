---
title: 'MDVA-34948: Verlangsamung der Website'
description: Der MDVA-34948 Adobe Commerce Patch behebt das Problem der Verlangsamung der Website. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1 installiert ist. Die Patch-ID lautet MDVA-34948. Beachten Sie, dass das Problem in Adobe Commerce Version 2.4.1 behoben wurde.
exl-id: ba5417b3-a71c-4f1b-877b-4e7206f86660
feature: Observability, Configuration
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# MDVA-34948: Verlangsamung der Website


## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce auf unserer Cloud-Infrastruktur 2.4.0-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce On-Premises und Adobe Commerce in unserer Cloud-Infrastruktur 2.3.6-2.3.6-p1, 2.4.0-2.4.0-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Website wird langsam, was den Betrieb behindert.

<u>Schritte zur Reproduktion</u>:

1. `show processlist` in MySQL ausführen.
1. Überprüfen, ob mehrere Abfragen vorhanden sind, z. B.:

```sql
   SELECT GET_LOCK(SYSTEM_CONFIG', '10');
```

<u>Erwartete Ergebnisse</u>:

`GET_LOCK` sollte sofort ausgeführt werden.

<u>Tatsächliche Ergebnisse</u>:

Mehrere `GET_LOCK`-Abfragen bleiben jeweils bis zu 10 Sekunden lang hängen.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [Patches in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
