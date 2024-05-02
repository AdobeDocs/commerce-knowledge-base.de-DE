---
title: "ACSD-45849: Videometadaten gehen nach der Staging-Aktualisierung verloren"
description: Der Patch ACSD-45849 behebt das Problem, dass die Video-Metadaten nach dem Anwenden eines Staging-Updates verloren gehen. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 installiert ist. Die Patch-ID lautet ACSD-45849. Beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben wurde.
exl-id: 071a535d-f96c-4731-a17c-0b7bf8a87372
feature: Staging, Page Content
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# ACSD-45849: Videometadaten gehen nach der Staging-Aktualisierung verloren

Der Patch ACSD-45849 behebt das Problem, dass die Video-Metadaten nach dem Anwenden eines Staging-Updates verloren gehen. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 installiert ist. Die Patch-ID lautet ACSD-45849. Beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.3-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Video-Metadaten gehen verloren, nachdem eine Staging-Aktualisierung angewendet wurde.

<u>Zu reproduzierende Schritte</u>:

1. Einrichten des YouTube-API-Schlüssels in **Admin** > **Stores** > **Konfiguration** > **Katalog** > **Produktvideo**.
1. Erstellen Sie ein Produkt mit einem YouTube-Video. Beachten Sie, dass die URL, der Titel und die Beschreibung ausgefüllt sind.
1. Erstellen Sie eine neue geplante Aktualisierung für das Produkt mit beliebigen Parametern, ohne die *Bilder und Videos* Abschnitt.
1. Klicken Sie auf **Anzeigen/Bearbeiten** unter Geplante Änderungen.
1. Navigieren Sie zu **Bilder und Videos** und klicken Sie auf das Video.

<u>Erwartete Ergebnisse</u>:

Die URL, der Titel und die Beschreibung enthalten die entsprechenden Daten.

<u>Tatsächliche Ergebnisse</u>:

Die Felder URL, Titel und Beschreibung sind leer.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
