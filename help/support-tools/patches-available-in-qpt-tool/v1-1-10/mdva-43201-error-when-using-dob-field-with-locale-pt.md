---
title: "MDVA-43201: Fehler bei Verwendung des DOB-Felds mit dem Gebietsschema PT"
description: Der Patch MDVA-43201 behebt das Problem, dass bei der Verwendung des DOB-Kundenattributs im Formular zur Kundenregistrierung für das portugiesische Gebietsschema ein Fehler auftritt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-43201. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
exl-id: 02979378-adc1-4a1a-93bf-a35ad50e6b80
feature: B2B, Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-43201: Fehler bei Verwendung des DOB-Felds mit dem Gebietsschema PT

Der Patch MDVA-43201 behebt das Problem, dass bei der Verwendung des DOB-Kundenattributs im Formular zur Kundenregistrierung für das portugiesische Gebietsschema ein Fehler auftritt. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-43201. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn das DOB-Kundenattribut dem Formular zur Kundenregistrierung für das portugiesische Gebietsschema hinzugefügt wird, gibt das Formular den Fehler zurück. *Argument 1, das an iterator_to_array() übergeben wird, muss Schnittstelle travesable implementieren, null, angegeben*.

<u>Voraussetzungen</u>:

B2B-Module sind installiert.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zu Admin > **Stores** > **Konfiguration** > **Allgemein** > **Gebietsschemaoptionen**, Gebietsschema auf **Portugiesisch (Portugal)** und klicken **Speichern**.
1. Neuindizieren und leeren Sie den Cache.
1. Navigieren Sie zu **Stores** > **Attribut** > **Kunde**.
1. Öffnen Sie das DOB-Kundenattribut und legen Sie **In Storefront anzeigen** nach **Ja**.
1. Alle auswählen unter **Formular zur Verwendung in**.
1. Speichern Sie das Attribut.
1. Rufen Sie im Frontend die Seite Neues Konto erstellen auf.

<u>Erwartete Ergebnisse</u>:

Das Formular zur Kundenregistrierung für den portugiesischen Store gibt keinen Fehler beim Hinzufügen des DOB-Attributs.

<u>Tatsächliche Ergebnisse</u>:

Das Formular zur Kundenregistrierung für den portugiesischen Store gibt beim Hinzufügen des DOB-Attributs einen Fehler aus.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
