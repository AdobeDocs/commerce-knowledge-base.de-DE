---
title: "MDVA-34680: Kundenkonto im Kundennetz nicht korrekt gefiltert"
description: Der Patch MDVA-34680 behebt das Problem, dass das Kundenkonto, das nach 00:00 UTC erstellt wurde, im Kundenraster nicht korrekt gefiltert wurde. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26 installiert ist. Die Patch-ID lautet MDVA-34680. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben sein soll.
exl-id: 2e506d7a-8cde-41eb-84b2-1a5ff8015428
feature: Customer Service
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# MDVA-34680: Kundenkonto im Kundennetz nicht korrekt gefiltert

Der Patch MDVA-34680 behebt das Problem, dass das Kundenkonto, das nach 00:00 UTC erstellt wurde, im Kundenraster nicht korrekt gefiltert wurde. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26 ist installiert. Die Patch-ID lautet MDVA-34680. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.4.1 und 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce lokal und Adobe Commerce auf Cloud-Infrastruktur 2.3.6-2.3.7 und 2.4.1-2.4.2-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn ein Kundenkonto nach 00:00 UTC erstellt wird und Sie versuchen, Konten nach diesem Datum zu filtern, wird dieser Kunde nicht zurückgegeben.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zu **Stores** > **Konfiguration** > **Allgemein** und legen Sie die Zeitzone auf &quot;Eastern Standard&quot;fest [Vereinigte Staaten/New York].
1. Erstellen Sie nach 00:00 UTC ein neues Kundenkonto.
1. Navigieren Sie zu **Kunden** > **Alle Kunden** und die Konten nach dem heutigen Datum filtern.

<u>Erwartete Ergebnisse</u>:

Die Kundenkontofilter zeigen das neue Konto an, das heute nach 00:00 UTC erstellt wurde.

<u>Tatsächliche Ergebnisse</u>:

In den Kundenkontofiltern wird das heute erstellte neue Konto nicht angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) Abschnitt.
