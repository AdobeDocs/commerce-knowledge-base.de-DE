---
title: "MDVA-36424: An den Seitenaufbau angehängte Bilder verschwinden beim Speichern."
description: Der Patch MDVA-36424 behebt das Problem, dass die Bilder, die mit den Seitenaufbauelementen verknüpft sind, beim zweiten Speichern der Kategorie bei mehreren Websites verschwinden, wobei sich die Basis-URL der Standardwebsite von der Admin-URL unterscheidet. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 installiert ist. Die Patch-ID lautet MDVA-36424. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.
exl-id: ae15db2d-0d9f-48c1-87e4-61da1558a57c
feature: Categories, Page Builder
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# MDVA-36424: Mit dem Seitenaufbau verbundene Bilder verschwinden beim Speichern.

Der Patch MDVA-36424 behebt das Problem, dass die Bilder, die mit den Seitenaufbauelementen verknüpft sind, beim zweiten Speichern der Kategorie bei mehreren Websites verschwinden, wobei sich die Basis-URL der Standardwebsite von der Admin-URL unterscheidet. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 installiert ist. Die Patch-ID lautet MDVA-36424. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce in Cloud-Infrastruktur 2.3.6

**Kompatibel mit Magento-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.5 - 2.4.1-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Mit Seitenaufbauelementen verknüpfte Medienbilder werden nicht gespeichert, wenn sich die Backend-Basis-URL von der Basis-URL des Storefront unterscheidet.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine zweite Website - website2.
1. Legen Sie für website2 eine andere Basis-URL fest (die Basis-URL, die in admin verwendet wird, sollte sich von der zweiten Website unterscheiden).
1. Legen Sie die zweite Website als Standardwebsite fest (**Stores** > *Einstellungen* > **Alle Stores** > Wählen Sie die zweite Website aus > setzen Sie sie als *Standard*).
1. Navigieren Sie zur Kategorieseite im Backend und navigieren Sie zu einer Ansicht zur Kategoriebearbeitung.
1. Navigieren Sie zu **Inhalt** > *Beschreibung*.
1. Fügen Sie dem Inhalt eine Spalte hinzu und legen Sie mithilfe der Mediengalerie ein Hintergrundbild fest.
1. Speichern Sie die Kategorie.
1. Navigieren Sie zu **Inhalt** > *Beschreibung* erneut angezeigt. Das gespeicherte Bild wird dann korrekt angezeigt.
1. Speichern Sie die Kategorie erneut.
1. Navigieren Sie zu **Inhalt** > *Beschreibung*.

<u>Erwartete Ergebnisse</u>:

Das Bild wird beim Speichern der Kategorie nicht entfernt.

<u>Tatsächliche Ergebnisse</u>:

Das Bild wird nach dem zweiten Speichern der Kategorie entfernt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
