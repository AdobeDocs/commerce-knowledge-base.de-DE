---
title: "MDVA-39043: Admin-Benutzer erhalten Fehler beim Hinzufügen von Widgets zur CMS-Seite."
description: Der Patch MDVA-39043 behebt das Problem, dass Admin-Benutzer mit eingeschränktem Zugriff beim Hinzufügen des Widgets "Produkte"zur CMS-Seite einen Fehler erhalten. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-39043. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
exl-id: 63057351-e972-4575-9bf0-e818f590b40a
feature: Admin Workspace, CMS, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# MDVA-39043: Admin-Benutzer erhalten Fehler beim Hinzufügen von Widgets zur CMS-Seite

Der Patch MDVA-39043 behebt das Problem, dass Admin-Benutzer mit eingeschränktem Zugriff beim Hinzufügen des Widgets &quot;Produkte&quot;zur CMS-Seite einen Fehler erhalten. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-39043. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4 - 2.4.3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Admin-Benutzer mit eingeschränktem Zugriff erhalten beim Hinzufügen des Widgets &quot;Produkte&quot;zur CMS-Seite einen Fehler.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich beim Backend mit dem Administrator an, der nur Zugriff auf die Bearbeitung von Inhalten hat.
1. Wechseln Sie zu **Inhalt** > **Seiten**.
1. Öffnen Sie alle zu bearbeitenden Seiten.
1. Bearbeiten Sie den Inhalt mit **Seitenaufbau**.
1. Fügen Sie das Widget **Produkt** aus dem Abschnitt **Inhalt hinzufügen** hinzu.
1. Klicken Sie im Widget **Produkt** auf **Konfigurieren** .

<u>Erwartete Ergebnisse</u>:

Es wird kein Fehler angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Die folgende Fehlermeldung wird empfangen:

`*A technical problem with the server created an error. Try again to continue what you were doing. If the problem persists, try again later.*`

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
