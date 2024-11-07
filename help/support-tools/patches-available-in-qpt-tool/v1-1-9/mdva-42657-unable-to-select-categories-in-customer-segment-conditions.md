---
title: "MDVA-42657: Kategorien können in den Kundensegmentbedingungen nicht ausgewählt werden"
description: Der Patch MDVA-42657 behebt das Problem, dass der Admin-Benutzer keine Kategorien in den Kundensegmentbedingungen auswählen kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-42657. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: 9c810dcd-b39b-4456-a362-5452ada4dc53
feature: Categories, Console, Customer Service
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# MDVA-42657: Kategorien können in den Kundensegmentbedingungen nicht ausgewählt werden

Der Patch MDVA-42657 behebt das Problem, dass der Admin-Benutzer keine Kategorien in den Kundensegmentbedingungen auswählen kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-42657. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Admin-Benutzer kann in den Kundensegmentbedingungen keine Kategorien auswählen.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zu **Kunden** > **Segmente**.
1. Erstellen Sie ein neues Segment.
1. Wechseln Sie zum neu erstellten Segment und klicken Sie im linken Navigationsbereich auf **Bedingungen** .
1. Klicken Sie auf das grüne Pluszeichen.
1. Wählen Sie Produktverlauf unter Produkte aus.
1. Ändern Sie &quot;Angesehen&quot;in &quot;ordered&quot;.
1. Ändern Sie &quot;ALL&quot;in &quot;ANY&quot;.
1. Klicken Sie auf das verschachtelte grüne Pluszeichen und wählen Sie Kategorie aus.
1. Klicken Sie auf das Symbol **..** und dann auf das Auswahlsymbol (links neben dem Häkchen).
1. Öffnen Sie die Entwicklerkonsole des Browsers.
1. Aktivieren Sie die Kontrollkästchen für eine oder mehrere Kategorien und beachten Sie den JavaScript-Fehler, der in der Konsole ausgegeben wird.
1. Klicken Sie auf die Schaltfläche **Speichern** .
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

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) verfügbar sind, in unserer Entwicklerdokumentation.
