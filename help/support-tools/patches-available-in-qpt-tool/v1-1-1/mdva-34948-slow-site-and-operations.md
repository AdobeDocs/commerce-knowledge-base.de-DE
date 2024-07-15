---
title: "MDVA-34948: Verlangsamung der Website"
description: Der MDVA-34948 Adobe Commerce Patch behebt das Problem der Verlangsamung der Website. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1 installiert ist. Die Patch-ID lautet MDVA-34948. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.1 behoben wurde.
exl-id: ba5417b3-a71c-4f1b-877b-4e7206f86660
feature: Observability, Configuration
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# MDVA-34948: Verlangsamung der Website


## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce auf unserer Cloud-Infrastruktur 2.4.0-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce vor Ort und Adobe Commerce auf unserer Cloud-Infrastruktur 2.3.6-2.3.6-p1, 2.4.0-2.4.0-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Website wird langsam, was den Betrieb behindert.

<u>Zu reproduzierende Schritte</u>:

1. Führen Sie `show processlist` in MySQL aus.
1. Überprüfen Sie, ob mehrere Abfragen vorliegen, z. B.:

```sql
   SELECT GET_LOCK(SYSTEM_CONFIG', '10');
```

<u>Erwartete Ergebnisse</u>:

`GET_LOCK` sollte sofort ausgeführt werden.

<u>Tatsächliche Ergebnisse</u>:

Mehrere `GET_LOCK` -Abfragen werden für jeweils bis zu 10 Sekunden blockiert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) verfügbare Patches.
