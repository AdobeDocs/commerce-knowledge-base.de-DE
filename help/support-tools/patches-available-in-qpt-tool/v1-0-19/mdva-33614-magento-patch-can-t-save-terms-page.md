---
title: "MDVA-33614 Patch: Kann keine Seite mit Nutzungsbedingungen speichern"
description: 'Der Patch MDVA-33614 behebt das Problem, bei dem es nicht möglich ist, Änderungen auf der Seite "Begriffe"zu speichern, da der Seitenaufbau den folgenden Fehler ausgibt: *Beim Initiieren von Page Builder ist ein Fehler aufgetreten. Wenden Sie sich an Ihren technischen Support-Ansprechpartner*. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 installiert ist. Die Patch-ID lautet MDVA-33614. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde."'
exl-id: d9b287bb-eab4-4c33-b725-ae0074962447
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# MDVA-33614 Patch: Seite mit Nutzungsbedingungen kann nicht gespeichert werden

Der Patch MDVA-33614 behebt das Problem, bei dem es nicht möglich ist, Änderungen an der Seite &quot;Begriffe&quot;zu speichern, da der Seitenaufbau den folgenden Fehler ausgibt: *Beim Initiieren von Page Builder ist ein Fehler aufgetreten. Wenden Sie sich an Ihren technischen Support-Ansprechpartner*. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 installiert ist. Die Patch-ID lautet MDVA-33614. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce in der Cloud-Infrastruktur 2.4.1

**Kompatibel mit Adobe Commerce-Versionen:** Adobe Commerce On-Premise und Adobe Commerce in Cloud-Infrastruktur 2.4.1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Es ist nicht möglich, Änderungen an der Seite &quot;Begriffe&quot;zu speichern, da der Seitenaufbau einen Fehler ausgibt.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie in Commerce Admin zu **INHALT** > Elemente > **Seiten**.
1. Wählen Sie die Seite Begriffe aus.
1. Klicken Sie auf **Bearbeiten**.
1. Nehmen Sie eine Bearbeitung vor und klicken Sie auf **Speichern**.

<u>Erwartetes Ergebnis</u>:

Die Seite wird ohne Fehler gespeichert.

<u>Tatsächliches Ergebnis</u>:

Der folgende Fehler wird angezeigt: *Beim Initiieren von Page Builder ist ein Fehler aufgetreten. Wenden Sie sich an Ihren technischen Support-Ansprechpartner*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie im Abschnitt [In QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) verfügbare Patches.
