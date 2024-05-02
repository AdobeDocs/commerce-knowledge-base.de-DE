---
title: "ACSD-46192: Problem mit dem Endpunkt async/bulk/V1/configuring-products/bySku/options"
description: Der Patch ACSD-46192 behebt das Problem mit dem Endpunkt "async/bulk/V1/configuring-products/bySku/options". Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.19 installiert ist. Die Patch-ID ist ACSD-46192. Beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben wurde.
exl-id: fed49708-868a-48ec-8dbc-638d75506a40
feature: Configuration, Products
role: Admin
source-git-commit: 6c04285321879dae82fe3c5aa04f165fdba42bbd
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-46192: Problem mit dem Endpunkt async/bulk/V1/configuring-products/bySku/options

Der Patch ACSD-46192 behebt das Problem mit dem `async/bulk/V1/configurable-products/bySku/options` -Endpunkt. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) Version 1.1.19 ist installiert. Die Patch-ID ist ACSD-46192. Beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.6 - 2.4.4-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 und 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn eine POST-Anfrage an `async/bulk/V1/configurable-products/bySku/`.

<u>Zu reproduzierende Schritte</u>:

1. Senden einer POST-Anfrage an `async/bulk/V1/configurable-products/bySku/`.

```JSON
[{
  "sku": "MS-Champ",
  "option": {
    "attribute_id": "141",
    "label": "Size",
    "position": 0,
    "is_use_default": true,
    "values": [
      {
        "value_index": 9
      }
    ]
  }
}]
```

<u>Erwartete Ergebnisse</u>:

Es gibt keinen Fehler. Sie erhalten die folgende Antwort:

```JSON
{
  "bulk_uuid": "e5a94361-e16e-432b-a000-c1351a0d01b3",
  "request_items": [
    {
      "id": 0,
      "data_hash": "3e7369ffc0a1602c1f25601a2e11b130f65fd01e68b5091ad746d0cac5b7f35d",
      "status": "accepted"
    }
  ],
  "errors": false
}
```

<u>Tatsächliche Ergebnisse</u>:

Der folgende Fehler tritt auf:

```PHP
TypeError: Argument 3 passed to Magento\Framework\Webapi\ServiceInputProcessor::process() must be of the type array, string given, called in /var/www/html/vendor/magento/module-webapi-async/Controller/Rest/Asynchronous/InputParamsResolver.php on line 154 and defined in /var/www/html/vendor/magento/framework/Webapi/ServiceInputProcessor.php:172
```

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
