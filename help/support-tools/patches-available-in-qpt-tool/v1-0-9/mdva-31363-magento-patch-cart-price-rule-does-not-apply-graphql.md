---
title: "MDVA-31363 Patch: Warenkorbpreisregel gilt nicht (GraphQL)"
description: Der Patch MDVA-31363 behebt das Problem, dass die Preisregel für den Warenkorb mit Coupon nicht über GraphQL gilt, wenn die Aktion "Fester Rabatt für ganzen Warenkorb"verwendet wird. Dieser Patch ist verfügbar, wenn das Quality Patches Tool (QPT) 1.0.9 installiert ist. Das Problem soll in Adobe Commerce-Version 2.4.2 behoben werden.
exl-id: f64fbbb1-b5fd-4624-bcdd-d1e6c1f9acfe
feature: GraphQL, Orders, Price Rules, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# Patch MDVA-31363: Preisregel für Warenkorb gilt nicht (GraphQL)

>[!WARNING]
>
>Ein neuer Patch namens MDVA-33975 behebt Probleme bei der GraphQL-Preisberechnung. MDVA-31363 wird abgeschrieben und es wird empfohlen, den Patch MDVA-33975 anzuwenden. Informationen zum Zugriff auf diesen Patch finden Sie unter [Patch MDVA-33975: GraphQL-Preisberechnungen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/mdva-33975-magento-patch-graphql-price-calculations.html).

Der Patch MDVA-31363 behebt das Problem, dass die Preisregel für den Warenkorb mit Coupon nicht über GraphQL gilt, wenn die Aktion &quot;Fester Rabatt für ganzen Warenkorb&quot;verwendet wird. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 ist installiert. Das Problem soll in Adobe Commerce-Version 2.4.2 behoben werden.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.4.0

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce über Cloud-Infrastruktur und Adobe Commerce vor Ort 2.3.2 - 2.4.1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Neuberechnung der Anführungssummen vor der Abgabe einer Antwort zu Anführungspreisen führt dazu, dass angewandte Regeln verloren gehen.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein einfaches Produkt.
1. Erstellen Sie eine Regel zum Warenkorbpreis mit einem festen Rabatt für den gesamten Warenkorb.
1. Erstellen Sie mit GraphQL einen neuen Warenkorb.
1. Speichern Sie die card\_id aus der Antwort und fügen Sie das Produkt aus Schritt 1 mithilfe von GraphQL zum Warenkorb hinzu.
1. Aktivieren Sie die Preisregel für den Warenkorb, indem Sie den Gutscheincode mithilfe von GraphQL zum Warenkorb hinzufügen.
1. Überprüfen Sie den Preis als Antwort.

<u>Erwartete Ergebnisse</u>:

Der Rabatt wird angewendet.

<u>Tatsächliche Ergebnisse</u>:

Der Rabatt wird nicht gewährt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
