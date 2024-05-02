---
title: "MDVA-31343 Patch: Zeitplanaktualisierung entfernt Textklasse für Kategorie"
description: Der Patch MDVA-31343 behebt das Problem, dass die zugewiesene CSS-Klasse des Layout-Hauptteils für eine Kategorie während der geplanten Aktualisierung entfernt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 installiert ist. Das Problem soll in Adobe Commerce 2.4.2 behoben werden.
exl-id: 50dbff01-cb77-4cac-b90e-5c4b06f5e4e7
feature: Cache, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# Patch MDVA-31343: Durch eine regelmäßige Aktualisierung wird die Hauptteilklasse für die Kategorie entfernt

Der Patch MDVA-31343 behebt das Problem, dass die zugewiesene CSS-Klasse des Layout-Hauptteils für eine Kategorie während der geplanten Aktualisierung entfernt wird. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 ist installiert. Das Problem soll in Adobe Commerce 2.4.2 behoben werden.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.3.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce über Cloud-Infrastruktur und Adobe Commerce vor Ort 2.3.4 - 2.3.5-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Textklasse des Layouts wird nach geplanter Aktualisierung aus der Kategorie entfernt.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie in Commerce Admin eine Kategorie.
1. Satz **Layout** = *Kategorie — Vollbreite* im **Design** Abschnitt.
1. Speichern Sie die Kategorie.
1. Navigieren Sie zur Seite &quot;Kategoriefrontend&quot;. Beachten Sie in der Seitenquelle den

   ```css
   page-layout-category-full-width
   ```

   CSS-Klasse.
1. under **KATALOG** > **Kategorie** klicken **Neue Aktualisierung planen** im *Geplante Änderungen* für die neue Kategorie.
1. Warten Sie, bis das geplante Update gestartet ist, führen Sie Cron aus und leeren Sie den Cache.
1. Gehen Sie zur Kategorieseite im Frontend und überprüfen Sie die Seitenquelle.

<u>Erwartete Ergebnisse</u>:

Im Seitentext sehen Sie die

```css
page-layout-category-full-width
```

CSS-Klasse.

<u>Tatsächliche Ergebnisse</u>:

Im Seitentext sehen Sie die

```css
page-layout-2columns-left
```

CSS-Klasse, die standardmäßig für die Kategorieseite verwendet wird.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
