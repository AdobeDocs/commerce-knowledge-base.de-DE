---
title: "MDVA-39305: Anmeldeproblem mit aktiviertem Google reCAPTCHA"
description: Der Patch MDVA-39305 behebt das Problem, dass registrierte Kunden sich nicht mit aktiviertem Google reCAPTCHA anmelden können. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1 installiert ist. Die Patch-ID lautet MDVA-39305. Bitte beachten Sie, dass das Problem in den Adobe Commerce-Versionen 2.4.4 und 2.4.7 behoben werden soll.
exl-id: 1e8e7dc7-f8f1-4432-90f4-dc73d85f353a
feature: Console
role: Admin
source-git-commit: d48abbf3ecc19a78ee1d86a12d9c32cba17d53e5
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# MDVA-39305: Anmeldeproblem mit aktiviertem Google reCAPTCHA

Der Patch MDVA-39305 behebt das Problem, dass registrierte Kunden sich nicht mit aktiviertem Google reCAPTCHA anmelden können. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1 installiert ist. Die Patch-ID lautet MDVA-39305. Bitte beachten Sie, dass das Problem in den Adobe Commerce-Versionen 2.4.4 und 2.4.7 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce auf Cloud-Infrastruktur 2.4.2-p1, 2.4.3-p3, 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1-p1 - 2.4.3-p3, 2.4.4-p1 - 2.4.4-p5, 2.4.5 - 2.4.6-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Registrierte Kunden können sich nicht mit der aktivierten Google reCAPTCHA anmelden.

<u>Zu reproduzierende Schritte</u>:

1. Wechseln Sie zu **Store** > **Konfiguration** > **Sicherheit** > **Google reCAPTCHA-Storefront** und aktivieren Sie **Google reCAPTCHA**.
1. Wechseln Sie zu **Frontend**.
1. Öffnen Sie die **Entwickler-Tool-Konsole** im Browser.

<u>Erwartete Ergebnisse</u>:

Keine CSP-Warnungen in der Konsole.

<u>Tatsächliche Ergebnisse</u>:

CSP-Warnungen in der Konsole.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
