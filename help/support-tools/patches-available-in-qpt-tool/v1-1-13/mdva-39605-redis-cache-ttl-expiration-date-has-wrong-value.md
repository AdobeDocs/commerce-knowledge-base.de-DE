---
title: 'MDVA-39605: Redis cache TTL (Ablaufdatum) hat falschen Wert'
description: Der MDVA-39605-Patch behebt das Problem, bei dem die Redis-Cache-TTL (Ablaufdatum) einen falschen Wert hat. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-39605. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: 7283838b-702d-4ddc-aa03-829dbf5aa91f
feature: Cache, Console, Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 0%

---

# MDVA-39605: Redis cache TTL (Ablaufdatum) hat falschen Wert

Der MDVA-39605-Patch behebt das Problem, bei dem die Redis-Cache-TTL (Ablaufdatum) einen falschen Wert hat. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-39605. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die TTL des Redis-Cache (Ablaufdatum) hat einen falschen Wert.

<u>Zu reproduzierende Schritte</u>:

Um die Fehlerbehebung zu testen, leeren Sie den Cache und öffnen Sie ein konfigurierbares Produkt auf der Storefront. Öffnen Sie dann ein Terminal (Konsole) und führen Sie die folgenden Schritte aus:

1. Führen Sie den Befehl aus: `redis-cli`.
1. Führen Sie `KEYS "*PRICE"` aus (im Ergebnis sollte nur ein Schlüssel enthalten sein, z. B. `zc:ti:e54_PRICE`). Kopieren Sie den Schlüssel.
1. Führen Sie `SMEMBERS` aus, gefolgt vom Schlüssel aus dem vorherigen Schritt (z. B. `SMEMBERS zc:ti:e54_PRICE`). Kopieren Sie einen beliebigen Schlüssel aus dem Ergebnis (z. B. e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421).
1. Führen Sie `KEYS "*<key>"` mit dem Schlüsselnamen aus dem vorherigen Schritt aus, um den vollständigen Schlüsselnamen zu erhalten (z. B. `KEYS "*e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421"`). Das Ergebnis sollte nur einen Schlüssel enthalten (z. B. `zc:k:e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421`). Wie Sie vielleicht feststellen, ist der vollständige Schlüsselname einfach der Schlüsselname mit dem Präfix &quot;`zc:k:`&quot;. Kopieren Sie nun den vollständigen Schlüsselnamen.
1. Führen Sie `HGETALL` aus, gefolgt vom vollständigen Schlüsselnamen aus Schritt 4, um den Wert zu überprüfen. Der Wert sollte serialisierte Daten verknüpfter Produkte eines zugehörigen konfigurierbaren Produkts enthalten.
1. Führen Sie `TTL` und dann den vollständigen Schlüsselnamen aus Schritt 4 aus, um zu überprüfen, ob der Schlüssel abläuft. Das Ergebnis sollte sich von **-1** und **-2** unterscheiden und ungefähr 2592000 (30 Tage) betragen. Die im Code festgelegte Gültigkeit beträgt zwar ein Jahr, die in Adobe Commerce verwendete Redis-Bibliothek hat jedoch eine feste maximale Ablaufgrenze von 2592000 Sekunden.

<u>Erwartete Ergebnisse</u>:

Das Ablauflimit beträgt 2592000s.

<u>Tatsächliche Ergebnisse</u>:

Das Ablauflimit ist auf **-1** oder **-2** festgelegt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) verfügbar sind, in unserer Entwicklerdokumentation.
