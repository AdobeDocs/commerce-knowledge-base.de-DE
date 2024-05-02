---
title: "MDVA-39605: Redis cache TTL (Ablaufdatum) hat falschen Wert"
description: Der MDVA-39605-Patch behebt das Problem, bei dem die Redis-Cache-TTL (Ablaufdatum) einen falschen Wert hat. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-39605. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: 7283838b-702d-4ddc-aa03-829dbf5aa91f
feature: Cache, Console, Services
role: Admin
source-git-commit: 667fcacd5b6cbf56a5fd919d0683ad6a0f979fca
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 0%

---

# MDVA-39605: Redis cache TTL (Ablaufdatum) hat falschen Wert

Der MDVA-39605-Patch behebt das Problem, bei dem die Redis-Cache-TTL (Ablaufdatum) einen falschen Wert hat. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-39605. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die TTL des Redis-Cache (Ablaufdatum) hat einen falschen Wert.

<u>Zu reproduzierende Schritte</u>:

Um die Fehlerbehebung zu testen, leeren Sie den Cache und öffnen Sie ein konfigurierbares Produkt auf der Storefront. Öffnen Sie dann ein Terminal (Konsole) und führen Sie die folgenden Schritte aus:

1. Führen Sie den Befehl aus: `redis-cli`.
1. Ausführen `KEYS "*PRICE"` (Im Ergebnis sollte beispielsweise nur ein Schlüssel enthalten sein. `zc:ti:e54_PRICE`). Kopieren Sie den Schlüssel.
1. Ausführen `SMEMBERS` gefolgt vom Schlüssel aus dem vorherigen Schritt (z. B. `SMEMBERS zc:ti:e54_PRICE`). Kopieren Sie einen beliebigen Schlüssel aus dem Ergebnis (z. B. e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421).
1. Ausführen `KEYS "*<key>"` mit dem Schlüsselnamen aus dem vorherigen Schritt, um den vollständigen Schlüsselnamen zu erhalten (z. B. `KEYS "*e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421"`). Das Ergebnis darf nur einen Schlüssel enthalten (z. B. `zc:k:e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421`). Wie Sie vielleicht feststellen, ist der vollständige Schlüsselname einfach der Schlüsselname mit dem Präfix &quot;`zc:k:`&quot;. Kopieren Sie nun den vollständigen Schlüsselnamen.
1. Ausführen `HGETALL` gefolgt vom vollständigen Schlüsselnamen aus Schritt 4, um den Wert zu überprüfen. Der Wert sollte serialisierte Daten verknüpfter Produkte eines zugehörigen konfigurierbaren Produkts enthalten.
1. Ausführen `TTL` gefolgt vom vollständigen Schlüsselnamen aus Schritt 4, um zu überprüfen, ob der Schlüssel abläuft. Das Ergebnis sollte sich von **-1** und **-2** und sollte ungefähr 2592000 (30 Tage) betragen. Die im Code festgelegte Gültigkeit beträgt zwar ein Jahr, die in Adobe Commerce verwendete Redis-Bibliothek hat jedoch eine feste maximale Ablaufgrenze von 2592000 Sekunden.

<u>Erwartete Ergebnisse</u>:

Das Ablauflimit beträgt 2592000s.

<u>Tatsächliche Ergebnisse</u>:

Das Ablauflimit ist auf **-1** oder **-2**.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
