---
title: "MDVA-36718: Benutzerdefinierte Optionen bleiben nach API-Änderung erhalten"
description: Der Magento-Patch MDVA-36718 behebt das Problem, wenn die alten benutzerdefinierten Optionen nach dem Ändern über API beibehalten werden.
exl-id: e9755764-e563-4921-af75-a90e06237053
feature: REST
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# MDVA-36718: Benutzerdefinierte Optionen bleiben nach API-Änderung erhalten

Der Magento-Patch MDVA-36718 behebt das Problem, wenn die alten benutzerdefinierten Optionen nach dem Ändern über API beibehalten werden.

Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 installiert ist. Die Patch-ID lautet MDVA-36718. Bitte beachten Sie, dass das Problem in Magento Version 2.4.3 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce in Cloud-Infrastruktur 2.4.1

**Kompatibel mit Magento-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0-2.4.2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein einfaches Produkt.
1. Fügen Sie eine benutzerdefinierte Option vom Typ **Dropdown-Typ** hinzu.
1. Aktualisieren Sie die benutzerdefinierte Option über die API: Senden der `PUT` -Anfrage an `/V1/products/options/{optionId}`.

<u>Erwartete Ergebnisse</u>:

Die benutzerdefinierten Optionen werden wie erwartet aktualisiert.

<u>Tatsächliche Ergebnisse</u>:

Neue benutzerdefinierte Optionen werden hinzugefügt, die alten benutzerdefinierten Optionen bleiben jedoch erhalten.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie den Patch auf ein Magento-Problem mit dem Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank.

Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie im Abschnitt [Im QPT-Tool verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
