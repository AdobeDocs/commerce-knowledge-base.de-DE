---
title: 'MDVA-44188: E-Mails werden nicht an IDs gesendet, die ".-"'
description: Der Patch MDVA-44188 behebt das Problem, dass E-Mails nicht an die E-Mail-IDs gesendet werden, die ""enthalten.-". Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-44188. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: 2abd300a-6cf3-4973-9b36-1bba7b578378
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# MDVA-44188: E-Mails werden nicht an IDs gesendet, die &quot;.- &quot;

Der Patch MDVA-44188 behebt das Problem, dass E-Mails nicht an die E-Mail-IDs gesendet werden, die `.-` enthalten. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-44188. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

E-Mails können nicht an E-Mail-IDs gesendet werden, die im Benutzernamen `.-` enthalten.

<u>Zu reproduzierende Schritte</u>:

1. Registrieren Sie einen Kunden mit einer E-Mail-Adresse, die `.-` enthält. Beispiel: `.-foo@example.com`.
1. Bestellung aufgeben.

<u>Erwartete Ergebnisse</u>:

Benutzer mit der E-Mail-ID, die `.-` enthält, erhalten wie gewohnt E-Mails.

<u>Tatsächliche Ergebnisse</u>:

E-Mail wird nicht an die E-Mail-ID gesendet, die `.-` enthält. Der folgende Fehler wird in den Fehlerprotokollen angezeigt: *Die E-Mail-Adresse konnte der Mailingwarteschlange nicht hinzugefügt werden*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
