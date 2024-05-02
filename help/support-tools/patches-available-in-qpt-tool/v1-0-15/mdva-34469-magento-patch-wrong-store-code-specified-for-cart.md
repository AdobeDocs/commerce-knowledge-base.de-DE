---
title: "MDVA-34469: Falscher Store-Code für Warenkorb"
description: 'Der Patch MDVA-34469 behebt das Problem, bei dem Benutzer die Fehlermeldung erhalten: *Falscher Store-Code, der für den Warenkorb angegeben ist, wenn ein Produkt zum Warenkorb hinzugefügt wird, nachdem Store-Ansichten gewechselt wurden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 installiert ist. Die Patch-ID lautet MDVA-34469. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde."'
exl-id: 35d4f120-7fcf-4996-8b23-aca99cfc18ac
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# MDVA-34469: Falscher Store-Code für Warenkorb angegeben

Der Patch MDVA-34469 behebt das Problem, bei dem Benutzer die Fehlermeldung erhalten: *Falscher Store-Code für Warenkorb angegeben* beim Hinzufügen eines Produkts zum Warenkorb nach dem Wechsel der Store-Ansichten. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 installiert ist. Die Patch-ID lautet MDVA-34469. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce in Cloud-Infrastruktur 2.4.1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce über Cloud-Infrastruktur und Adobe Commerce vor Ort 2.4.1 - 2.4.1 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Benutzer sieht einen Warenkorbabfragefehler, *&quot;Falscher Store-Code für Warenkorb angegeben&quot;*, wenn versucht wird, die Store-Ansichten zu wechseln.

<u>Voraussetzungen</u>:

* Adobe Commerce 2.4.0.
* Eine einzelne Website mit einem einzelnen Store und zwei Store-Ansichten ist konfiguriert.
* Ein Kundenkonto wird erstellt.

<u>Zu reproduzierende Schritte</u>:

1. Das Adobe Commerce-Backend ist so konfiguriert, dass es zwei Store-Ansichten hat (mit Store-Codes: Standard, Sekunde).
1. Der Benutzer erstellt einen Warenkorb mit dem standardmäßigen Store-Code.
1. Der Benutzer versucht, diesen Warenkorb mit dem zweiten Store-Code im `Store` Anfrage-Header.

<u>Erwartete Ergebnisse</u>:

Der Warenkorb wird angezeigt, weil der Store wechselt (der neue Code wird im `Store` Anfrage-Header) verknüpft den Warenkorb mit dem angeforderten Store.

<u>Tatsächliche Ergebnisse</u>:

Die Warenkorbabfrage gibt einen Fehler zurück und der Warenkorb wird nicht angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) Abschnitt.
