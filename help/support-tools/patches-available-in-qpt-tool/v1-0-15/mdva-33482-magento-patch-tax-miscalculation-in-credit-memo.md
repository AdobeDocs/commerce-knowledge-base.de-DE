---
title: "MDVA-33482 Patch: Tax miscalculations in Credit Memo"
description: Der Patch MDVA-33482 behebt das Problem, dass die Steuer in Kreditmemos falsch berechnet wird.
exl-id: 80740e6f-2b6c-4770-9a1a-58ba68a1b28f
feature: Orders, Returns, Taxes
role: Admin
source-git-commit: 0ffa6d63f7046048f7e8f0e9fab1ee1869c98e93
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# MDVA-33482 Patch: Fehlberechnung von Steuern im Kreditmemo

Der Patch MDVA-33482 behebt das Problem, dass die Steuer in Kreditmemos falsch berechnet wird, wenn keine Anpassungsgebühr oder Anpassungserstattung angewendet wird.

Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce-Version 2.4.3 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce auf Cloud-Infrastruktur 2.4.0

**Kompatibel mit Adobe Commerce-Versionen:** Adobe Commerce über Cloud-Infrastruktur und Adobe Commerce vor Ort 2.3.5 - 2.4.2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Konfigurieren **Steuern**.
1. Erstellen Sie mit einer beliebigen Online-Zahlungsmethode eine Bestellung mit zwei Produkten im Backend (Beispiel: [!DNL PayPal Payment Pro]). Stellen Sie sicher, dass alle Produkte steuerpflichtig sind.
1. Erstellen Sie zwei Rechnungen für die Bestellung.
1. Erstellen Sie ein Kreditmemo für eine der Rechnungen. Beachten Sie, dass die Lösung nicht anwendbar ist, wenn Sie planen, eine Anpassungsgebühr oder einen Anpassungsrückerstattungsbetrag anzuwenden.
1. Überprüfen Sie die Gesamtwerte der Credit-Memos.

<u>Erwartete Ergebnisse</u>:

Nur ein teilweise in Rechnung gestellter Steuerbetrag wird wie erwartet im Kreditmemo ausgewiesen.

<u>Tatsächliche Ergebnisse</u>:

Der volle Steuerbetrag wird im Kreditmemo angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Adobe Commerce-Produkt die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie im Abschnitt [Im QPT-Tool verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) Abschnitt.
