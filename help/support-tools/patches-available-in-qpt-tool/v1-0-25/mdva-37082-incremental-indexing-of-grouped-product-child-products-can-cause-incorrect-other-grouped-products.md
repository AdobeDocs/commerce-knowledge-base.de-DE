---
title: "MDVA-37082: Falscher partieller Index des Bestandsstatus für gruppierte Erzeugnisse"
description: Der MDVA-37082 Magento Patch behebt das Problem, wenn der partielle Index des Aktienstatus für gruppierte Produkte für benutzerdefinierte Bestände falsch ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25 installiert ist. Die Patch-ID lautet MDVA-37082. Bitte beachten Sie, dass das Problem in Magento 2.4.4 behoben sein soll.
exl-id: 1c0abc99-bd24-4848-87a3-227a63655cb7
feature: Cache, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---

# MDVA-37082: Falscher partieller Index des Aktienstatus für gruppierte Produkte

Der MDVA-37082 Magento Patch behebt das Problem, wenn der partielle Index des Aktienstatus für gruppierte Produkte für benutzerdefinierte Bestände falsch ist. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25 ist installiert. Die Patch-ID lautet MDVA-37082. Bitte beachten Sie, dass das Problem in Magento 2.4.4 behoben sein soll.


## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
Adobe Commerce auf Cloud-Infrastruktur 2.3.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**
Adobe Commerce On-Premise und Adobe Commerce über Cloud-Infrastruktur 2.3.0-2.4.2-p1
>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die inkrementelle Indizierung von gruppierten Produkt-untergeordneten Produkten kann dazu führen, dass falsche andere gruppierte Produkte falsch indiziert werden, wenn untergeordnete Elemente freigegeben werden.

<u>Zu reproduzierende Schritte</u>:

* Erstellen Sie ein neues Lager und eine neue Quelle für die Haupt-Website.
* Erstellen Sie 3 einfache Produkte mit den Werten 10,15 und 0.
* Erstellen Sie 2 Produkte, die gruppiert sind, und ordnen Sie das erste einfache Produkt mit 10 zu einem und zwei anderen einfachen Produkten zum anderen.
* Vergewissern Sie sich, dass beide gruppierten Produkte von der Frontend aus auf Lager verfügbar sind.
* Weisen Sie das einfache Produkt mit 0 den Up-Sell-Produkten des ersten gruppierten Produkts zu.
* Reinigen Sie den Cache für die gesamte Seite und überprüfen Sie das zweite gruppierte Produkt vom Frontend.
* Führen Sie eine vollständige Neuindizierung aus.
* Überprüfen Sie das zweite gruppierte Produkt vom Frontend.
* Speichern Sie das erste gruppierte Produkt.
* Reinigen Sie den Cache für ganze Seiten und überprüfen Sie das zweite gruppierte Produkt vom Frontend.

<u>Erwartete Ergebnisse</u>:

Das gruppierte Produkt ist nach dem Speichern eines anderen gruppierten Produkts mit Up-Sell nicht mehr vorrätig. Das Problem wird nach einer vollständigen Neuindizierung behoben.

<u>Tatsächliche Ergebnisse</u>:

Das zweite gruppierte Produkt wird nicht mehr vorrätig, wenn Sie das erste gruppierte Produkt speichern.

## Wenden Sie den Patch an

Um einzelne Patches anzuwenden, verwenden Sie je nach Adobe Commerce-Bereitstellungsmethode die folgenden Links zur Entwicklerdokumentation:

* Adobe Commerce vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Überprüfen Sie mithilfe des Tools &quot;Quality Patches&quot;, ob der Patch für Ihr Magento-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Weitere Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie im Abschnitt [Im QPT-Tool verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) Abschnitt.
