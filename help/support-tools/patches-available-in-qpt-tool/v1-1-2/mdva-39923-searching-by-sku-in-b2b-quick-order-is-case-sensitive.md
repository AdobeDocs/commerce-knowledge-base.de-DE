---
title: "MDVA-39923: Bei der Suche nach SKU in der B2B-Schnellbestellfunktion wird zwischen Groß- und Kleinschreibung unterschieden"
description: Der Patch MDVA-39923 behebt das Problem, dass Kunden einen Fehler erhalten, wenn sie die Bestellung durch SKU in der B2B-Schnellbestellfunktion durchsuchen, wobei der Fall anders ist als der, mit dem der Name gespeichert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-39923. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
exl-id: 52e435df-28a7-49be-a257-7e5801601d57
feature: B2B, Catalog Management, Orders, Search
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# MDVA-39923: Bei der Suche nach SKU in der B2B-Schnellbestellfunktion wird zwischen Groß- und Kleinschreibung unterschieden

Der Patch MDVA-39923 behebt das Problem, dass Kunden einen Fehler erhalten, wenn sie die Bestellung durch SKU in der B2B-Schnellbestellfunktion durchsuchen, wobei der Fall anders ist als der, mit dem der Name gespeichert wird. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 ist installiert. Die Patch-ID lautet MDVA-39923. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Bei der Suche nach der SKU in der Funktion für die schnelle B2B-Bestellung wird zwischen Groß- und Kleinschreibung unterschieden und es wird ein Fehler angezeigt, wenn eine andere Groß-/Kleinschreibung verwendet wird als die, mit der die SKU gespeichert wird.

<u>Voraussetzungen</u>:

B2B-Module sind installiert.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich beim Administrator an und wechseln Sie zu **Stores** > **Konfiguration** > **B2B**.
1. Aktivieren **Freigegebener Katalog** und **Schnellbestellung**.
1. Erstellen Sie ein Produkt mit SKU in Großbuchstaben, z. B. TEST20-1234
1. Zuweisen eines erstellten Produkts zum **Freigegebener Katalog**.
1. Melden Sie sich als Kunde an und klicken Sie auf **Schnellbestellung**.
1. Geben Sie die SKU in Kleinbuchstaben ein, z. B. test20-1234.

<u>Erwartete Ergebnisse</u>:

Das Produkt sollte unabhängig vom verwendeten Fall gefunden werden.

<u>Tatsächliche Ergebnisse</u>:

Die folgende Fehlermeldung wird empfangen: *1 Produkt(e) erfordert(n) Ihre Aufmerksamkeit*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
