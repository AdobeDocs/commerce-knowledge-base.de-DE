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

Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.14 ist installiert. Bitte beachten Sie, dass das Problem in Adobe Commerce-Version 2.4.3 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.3.2 mit B2B-Version 1.2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce über Cloud-Infrastruktur und Adobe Commerce vor Ort 2.3.0 - 2.3.5-p2, 2.4.0, 2.4.1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Voraussetzungen</u>:

Installieren Sie eine neue Adobe Commerce-Instanz mit B2B.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zu **SPEICHER > Konfiguration > ALLGEMEIN > B2B-Funktionen** und aktivieren **Firma** und **B2B-Angebot**.
1. Erstellen Sie zwei weitere Websites mit **Stores** und **stoviews** (Insgesamt sollten Sie über drei Websites verfügen: *base*, *website2*, *website3*).
1. Erstellen Sie ein einfaches Produkt und weisen Sie es nur *website3*.
1. Navigieren Sie zu **STORES > Alle Stores** und *website3* as **default**.
1. Gehen Sie zum Frontend und erstellen Sie ein neues Unternehmen auf *website3*.
1. Fügen Sie das zuvor erstellte Produkt zum Warenkorb hinzu und erstellen Sie ein neues handelbares Angebot.
1. Navigieren Sie zu **STORES > Alle Stores** und legen Sie &quot;*base*&quot;Website zurück als **default**.
1. Navigieren Sie zu **SALES > Anführungszeichen > Offenes, zuvor erstelltes Zitat** und versuchen Sie, ihm dasselbe Produkt hinzuzufügen.

<u>Erwartete Ergebnisse</u>:

Der Admin-Benutzer kann dem Angebot wie erwartet dasselbe Produkt hinzufügen.

<u>Tatsächliche Ergebnisse</u>:

Der Admin-Benutzer kann dem Zitat nicht dasselbe Produkt hinzufügen. Diese Fehlermeldung wird angezeigt:

```php
This product is assigned to another website.
```

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
