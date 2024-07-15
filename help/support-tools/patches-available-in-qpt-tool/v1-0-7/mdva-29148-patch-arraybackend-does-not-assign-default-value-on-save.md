---
title: "MDVA-29148: ArrayBackend weist beim Speichern keinen Standardwert zu."
description: Der Patch MDVA-29148 behebt das Problem, dass "\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend"beim Speichern den Standardwert nicht zuweist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.
exl-id: 7b2f5c18-0e7a-485b-a07e-700e435697fd
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-29148: ArrayBackend weist beim Speichern keinen Standardwert zu

Der Patch MDVA-29148 behebt das Problem, dass `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` beim Speichern den Standardwert nicht zuweist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.3.3-p1.

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) >=2.3.0 &lt;2.4.2.

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn ein Produkt über ein Importskript oder die REST-API erstellt wird, wird Attributen, die das Backend-Modell `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` verwenden und einen Standardwert haben, kein Standardwert zugewiesen.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein neues globales Attribut, das das Backend-Modell `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` und einen nicht leeren Standardwert verwendet.
1. Verwenden Sie die REST-API, um ein neues Produkt zu erstellen.
1. Rufen Sie dieses neue Produkt aus der REST-API ab und bestätigen Sie, dass das -Attribut in den benutzerdefinierten Attributen des Produkts nicht vorhanden ist.

<u>Erwartete Ergebnisse</u>:

Der Standardwert des benutzerdefinierten Attributs wurde im Produktattribut gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Der Standardwert des benutzerdefinierten Attributs wurde nicht im Produktattribut gespeichert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
