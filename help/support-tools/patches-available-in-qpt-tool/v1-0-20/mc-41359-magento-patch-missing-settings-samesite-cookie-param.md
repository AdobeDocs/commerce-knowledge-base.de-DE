---
title: 'MC-41359 Commerce-Patch: fehlende Einstellungen SameSite-Cookie-Parameter'
description: Der Commerce-Patch MC-41359 behebt das Problem mit fehlenden SameSite-Cookie-Parametern. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 installiert ist. Die Patch-ID ist MC-41359. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben sein soll.
exl-id: b48faa3f-0d9a-4d65-9abb-1573c6240635
feature: Observability
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# MC-41359 Commerce-Patch: fehlende Einstellungen SameSite-Cookie-Parameter

Der Commerce-Patch MC-41359 behebt das Problem mit fehlenden SameSite-Cookie-Parametern. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 installiert ist. Die Patch-ID ist MC-41359. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce in der Cloud-Infrastruktur 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:** Adobe Commerce lokal und Adobe Commerce in der Cloud-Infrastruktur 2.3.6-p1, 2.4.2, 2.4.2-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Fehlende Einstellungen des SameSite-Cookie-Parameters.

<u>Zu reproduzierende Schritte:</u>

Voraussetzungen:

* Öffnen Sie Chrome und navigieren Sie zu chrome://flags/
* Aktivieren Sie standardmäßig **SameSite-Cookies** und **Cookies ohne SameSite müssen sicher sein**.
* Öffnen Sie den Chrome-Inspektor.

<u>Szenario 1:</u>

1. Aktivieren Sie PayPal.
1. Geh zur Schaufensterfront.
1. Fügen Sie dem Warenkorb ein Produkt hinzu.
1. Gehen Sie zum Checkout.

<u>Szenario 2:</u>

Wenn Sie New Relic [aktiviert haben](https://docs.magento.com/user-guide/reports/new-relic-reporting.html), wird die Warnung auf einer beliebigen Frontend-Seite angezeigt.

<u>Tatsächliches Ergebnis:</u>

Warnmeldung in der Browser-Konsole: *Ein Cookie, das mit einer Site-übergreifenden Ressource verknüpft ist, wurde ohne SameSite-Attribut gesetzt.*

<u>Erwartetes Ergebnis:</u>

&quot;lax&quot;sollte nicht zur Cookie-Domäne hinzugefügt werden. Das gleiche Site-Attribut sollte mit dem Standardwert vorhanden sein.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätssicherungswerkzeugs](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md), ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie unter [im QPT-Tool verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
