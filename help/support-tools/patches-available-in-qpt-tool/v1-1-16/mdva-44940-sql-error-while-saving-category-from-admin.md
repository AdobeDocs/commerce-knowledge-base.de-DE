---
title: "MDVA-44940: SQL-Fehler beim Speichern der Kategorie von Administratoren"
description: Der Patch MDVA-44940 behebt das Problem, dass beim Speichern einer Kategorie vom Administrator ein SQL-Fehler auftritt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 installiert ist. Die Patch-ID lautet MDVA-44940. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.
exl-id: cae6f231-3b91-441f-af56-824db0fa2d32
feature: Admin Workspace, Categories, Sales Channels
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# MDVA-44940: SQL-Fehler beim Speichern der Kategorie unter Admin

Der Patch MDVA-44940 behebt das Problem, dass beim Speichern einer Kategorie vom Administrator ein SQL-Fehler auftritt. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 installiert ist. Die Patch-ID lautet MDVA-44940. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Beim Speichern einer Kategorie vom Administrator tritt ein SQL-Fehler auf.

<u>Zu reproduzierende Schritte</u>:

1. Beispieldaten installieren.
1. Erstellen Sie eine zweite Website mit einer Store-Gruppe, die der Standardkategorie zugeordnet ist.

   * Erstellen Sie eine Store-Ansicht, die der neuen Store-Gruppe zugewiesen ist.

1. Erstellen Sie ein Lager und eine zusätzliche Quelle, die diesem Lager zugewiesen ist, sowie einen Vertriebskanal, der der zweiten Website zugewiesen ist.
1. Erstellen Sie ein Testprodukt, das der zweiten Website zugewiesen ist.
1. Navigieren Sie zu **Admin** > **Katalog** > **Kategorien** auswählen **Anwendungsbereich** = **Zweite Website** und gehen Sie zu **Produkte der Kategorie** > **Automatische Sortierung** > Nicht vorrätige Produkte nach unten verschieben und auf **Speichern**.

<u>Erwartete Ergebnisse</u>:

Die Kategorie wird gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Der folgende Fehler tritt auf: *Beim Speichern der Kategorie ist etwas schiefgelaufen*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
