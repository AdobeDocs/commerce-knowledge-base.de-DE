---
title: "MDVA-32694 Patch: Problem beim Hinzufügen eines Produkts zu einem Zitat"
description: Der Patch MDVA-32694 behebt das Problem, dass es nicht möglich ist, ein gültiges Produkt in Admin zu einem verhandelbaren Angebot hinzuzufügen, das auf der nicht standardmäßigen Website erstellt wurde.
exl-id: 964abbbd-c8b1-4645-a393-7283f52e94ff
feature: Products, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# MDVA-32694 Patch: Problem beim Hinzufügen eines Produkts zu einem Zitat

Der Patch MDVA-32694 behebt das Problem, dass es nicht möglich ist, ein gültiges Produkt in Admin zu einem verhandelbaren Angebot hinzuzufügen, das auf der nicht standardmäßigen Website erstellt wurde.

Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.14 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce-Version 2.4.3 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.3.2 mit B2B-Version 1.2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce über Cloud-Infrastruktur und Adobe Commerce vor Ort 2.3.0 - 2.3.5-p2, 2.4.0, 2.4.1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Voraussetzungen</u>:

Installieren Sie eine neue Adobe Commerce-Instanz mit B2B.

<u>Zu reproduzierende Schritte</u>:

1. Wechseln Sie zu **STORES > Konfiguration > ALLGEMEIN > B2B-Funktionen** und aktivieren Sie **Firma** und **B2B-Angebot**.
1. Erstellen Sie zwei weitere Websites mit **stores** und **stoviews** (insgesamt sollten Sie über drei Websites verfügen: *base*, *website2*, *website3*).
1. Erstellen Sie ein einfaches Produkt und weisen Sie es nur *website3* zu.
1. Wechseln Sie zu **STORES > Alle Stores** und legen Sie *website3* auf **default** fest.
1. Gehen Sie zum Frontend und erstellen Sie ein neues Unternehmen auf *Website3*.
1. Fügen Sie das zuvor erstellte Produkt zum Warenkorb hinzu und erstellen Sie ein neues handelbares Angebot.
1. Wechseln Sie zu **STORES > Alle Stores** und stellen Sie die Website &quot;*base*&quot;wieder auf **default** ein.
1. Gehen Sie zu **VERKAUF > Angebote > Offenes, zuvor erstelltes Anführungszeichen** und versuchen Sie, dasselbe Produkt hinzuzufügen.

<u>Erwartete Ergebnisse</u>:

Der Admin-Benutzer kann dem Angebot wie erwartet dasselbe Produkt hinzufügen.

<u>Tatsächliche Ergebnisse</u>:

Der Admin-Benutzer kann dem Zitat nicht dasselbe Produkt hinzufügen. Diese Fehlermeldung wird angezeigt:

```php
This product is assigned to another website.
```

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie in der [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
