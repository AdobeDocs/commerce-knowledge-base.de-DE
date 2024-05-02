---
title: "MDVA-42657: Kategorien können in den Kundensegmentbedingungen nicht ausgewählt werden"
description: Der Patch MDVA-42657 behebt das Problem, dass der Admin-Benutzer keine Kategorien in den Kundensegmentbedingungen auswählen kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-42657. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: 9c810dcd-b39b-4456-a362-5452ada4dc53
feature: Categories, Console, Customer Service
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# MDVA-42657: Kategorien können in den Kundensegmentbedingungen nicht ausgewählt werden

Der Patch MDVA-42657 behebt das Problem, dass der Admin-Benutzer keine Kategorien in den Kundensegmentbedingungen auswählen kann. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 ist installiert. Die Patch-ID lautet MDVA-42657. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Admin-Benutzer kann in den Kundensegmentbedingungen keine Kategorien auswählen.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zu **Kunden** > **Segmente**.
1. Erstellen Sie ein neues Segment.
1. Gehen Sie zum neu erstellten Segment und klicken Sie auf **Bedingungen** in der linken Seitennavigation.
1. Klicken Sie auf das grüne Pluszeichen.
1. Wählen Sie Produktverlauf unter Produkte aus.
1. Ändern Sie &quot;Angesehen&quot;in &quot;ordered&quot;.
1. Ändern Sie &quot;ALL&quot;in &quot;ANY&quot;.
1. Klicken Sie auf das verschachtelte grüne Pluszeichen und wählen Sie Kategorie aus.
1. Klicken Sie auf **...** und klicken Sie dann auf das Auswahlsymbol (links neben dem Häkchen).
1. Öffnen Sie die Entwicklerkonsole des Browsers.
1. Aktivieren Sie die Kontrollkästchen für eine oder mehrere Kategorien und beachten Sie den JavaScript-Fehler, der in der Konsole ausgegeben wird.
1. Klicken Sie auf **Speichern** Schaltfläche.
1. Navigieren Sie zurück zur Bedingung und prüfen Sie, ob die ausgewählten Kategorien gespeichert wurden.

<u>Erwartete Ergebnisse</u>:

Die ausgewählten Kategorien werden beim Anzeigen/Bearbeiten der Segmentbedingungen gespeichert und ausgewählt.

<u>Tatsächliche Ergebnisse</u>:

Die ausgewählten Kategorien fehlen und wurden nicht ordnungsgemäß gespeichert. Sie erhalten den folgenden Fehler in der Konsole:

```
category-checkbox-tree.js:249 Uncaught TypeError: Cannot set properties of undefined (setting 'value')
    at Ext.tree.TreePanel.Enhanced.<anonymous> (category-checkbox-tree.js:249)
    at Ext.util.Event.fire (ext-tree.js:29)
```

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
