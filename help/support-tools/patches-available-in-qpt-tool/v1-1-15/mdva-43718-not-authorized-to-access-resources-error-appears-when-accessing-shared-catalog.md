---
title: "MDVA-43718: 'Consumer is not authorized to access resources' error wird beim Zugriff auf freigegebenen Katalog angezeigt."
description: Der Patch MDVA-43718 behebt das Problem, bei dem der Benutzer den Fehler *nicht berechtigt ist, auf %resources zuzugreifen.* wird angezeigt, wenn von einer benutzerdefinierten Integration aus auf einen freigegebenen Katalog zugegriffen wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 installiert ist. Die Patch-ID lautet MDVA-43718. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: fa783ed4-906e-4ee6-b82a-cfe6db5ae89e
feature: Catalog Management
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-43718: &quot;Der Verbraucher ist nicht berechtigt, auf Ressourcen zuzugreifen&quot;wird beim Zugriff auf freigegebene Kataloge der Fehler angezeigt

Der Patch MDVA-43718 behebt das Problem, bei dem der Fehler *consumer nicht berechtigt ist, auf %resources zuzugreifen.* wird beim Zugriff auf einen freigegebenen Katalog von einer benutzerdefinierten Integration angezeigt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 installiert ist. Die Patch-ID lautet MDVA-43718. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Beim Zugriff auf einen freigegebenen Katalog aus einer benutzerdefinierten Integration wird der folgende Fehler angezeigt: *Der Verbraucher ist nicht berechtigt, auf %resources* zuzugreifen.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine neue Integration über Admin > **System** > **Integration** > **Integration hinzufügen**.
1. Fügen Sie Zugriff für die folgenden Ressourcen hinzu und aktivieren Sie die Integration:

   * Magento_SharedCatalog::list
   * Magento_SharedCatalog::manage
   * Magento_Catalog:catalog

1. Integrationszugriff verwenden: `rest/default/V1/sharedCatalog/1`

<u>Erwartete Ergebnisse</u>:

Details zum freigegebenen Katalog werden zurückgegeben.

<u>Tatsächliche Ergebnisse</u>:

Der folgende Fehler wird zurückgegeben:

```JSON
"message": "The consumer isn't authorized to access %resources.",
"resources": "Magento_SharedCatalog::sharedCatalog"
```

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
