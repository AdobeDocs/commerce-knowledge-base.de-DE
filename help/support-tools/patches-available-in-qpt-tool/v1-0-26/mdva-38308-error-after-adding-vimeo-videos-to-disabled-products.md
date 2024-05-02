---
title: "MDVA-38308: Fehler nach dem Hinzufügen von Vimeo-Videos zu deaktivierten Produkten"
description: "Der MDVA-38308-Qualitäts-Patch für Adobe Commerce löst das Problem, bei dem Benutzer die Fehlermeldung erhalten: *Hinweis: Undefinierter Index: Erweiterung in /lib/internal/Magento/Framework/File/Uploader.php in Zeile 806,* beim Hinzufügen von Vimeo-Videos zu deaktivierten Produkten. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26 installiert ist. Die Patch-ID lautet MDVA-38308. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben werden soll."
exl-id: ed5fb9ec-c465-4bb9-8a29-4d5e4bd4c867
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# MDVA-38308: Fehler nach dem Hinzufügen von Vimeo-Videos zu deaktivierten Produkten

Der Qualitäts-Patch MDVA-38308 für Adobe Commerce behebt das Problem, bei dem Benutzer die Fehlermeldung erhalten: *Hinweis: Undefinierter Index: Erweiterung in /lib/internal/Magento/Framework/File/Uploader.php in Zeile 806,* beim Hinzufügen von Vimeo-Videos zu deaktivierten Produkten Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26 ist installiert. Die Patch-ID lautet MDVA-38308. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
Adobe Commerce auf Cloud-Infrastruktur 2.4.1-p1, 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**
Adobe Commerce lokal und Adobe Commerce auf Cloud-Infrastruktur 2.3.5 - 2.3.6-p1, 2.4.0 - 2.4.1-p1, 2.4.2 - 2.4.2-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Beim Hinzufügen von Vimeo-Videos zu deaktivierten Produkten erhalten Sie die folgende Fehlermeldung:  *Hinweis: Undefinierter Index: Erweiterung in /lib/internal/Magento/Framework/File/Uploader.php in Zeile 806*

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein einfaches Produkt.
1. Deaktivieren Sie das erstellte Produkt.
1. Versuchen Sie, dem deaktivierten Produkt ein Vimeo-Video hinzuzufügen.

<u>Erwartete Ergebnisse</u>:

Das Video wird ohne Fehler hinzugefügt.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten den folgenden Fehler:
*Hinweis: Undefinierter Index: Erweiterung in /lib/internal/Magento/Framework/File/Uploader.php in Zeile 806*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html)

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster in unserer Wissensdatenbank finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

Weitere Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie im Abschnitt [Im QPT-Tool verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) in unserer Support-Wissensdatenbank.
