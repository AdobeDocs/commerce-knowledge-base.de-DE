---
title: "ACSD-45424: Falsche Reservierungsentschädigung nach teilweiser Erstattung"
description: Der Patch ACSD-45424 behebt das Problem, dass nach einer teilweisen Rückerstattung eine falsche Reservierungsentschädigung entsteht. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 installiert ist. Die Patch-ID lautet ACSD-45424. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.
exl-id: 0676cfda-a28e-4a66-a75b-8a3fc5e22566
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# ACSD-45424: Falsche Reservierungsentschädigung nach teilweiser Rückerstattung

Der Patch ACSD-45424 behebt das Problem, dass nach einer teilweisen Rückerstattung eine falsche Reservierungsentschädigung entsteht. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 installiert ist. Die Patch-ID lautet ACSD-45424. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Nach einer teilweisen Rückerstattung wird eine falsche Reservierungsentschädigung erstellt.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie die Versandmethode für den In-Store-Versand.
1. Erstellen Sie drei Inventarquellen und stellen Sie sicher, dass der Erfassungsort in jedem (Quelle1, Quelle2, Quelle3) aktiv ist.
1. Erstellen Sie ein neues Lager und weisen Sie dem neuen Lager die drei Quellen zu.
   * Dieser Bestand sollte der Haupt-Website zugewiesen werden.
1. Erstellen Sie ein einfaches Produkt, P3, und weisen Sie ihm alle Quellen zu.
1. Fügen Sie die folgenden Mengen für die Quellen des einfachen Produkts hinzu und aktivieren Sie Backorder:
   * Standardquelle - 100
   * source1 - 0
   * source2 - 10
   * source3 - 0
1. Fügen Sie das einfache Produkt vom Frontend zum Warenkorb hinzu und fahren Sie mit dem Versandformular fort.
1. Wählen Sie &quot;source1&quot;als Versandort aus.
1. Führen Sie die Bestellung aus und führen Sie die folgende Abfrage in der Datenbank aus:

   ```sql
   SELECT * FROM inventory_reservation WHERE sku = 'P3';
   ```

   Sie erhalten den Bestelldatensatz im `inventory_reservation` Tabelle. Die Menge ist 10, was richtig ist.
1. Invotieren Sie diese Bestellung vom Backend aus.
1. Erstellen Sie nun ein Kreditmemo für nur ein Produkt. Wählen Sie NICHT die *Zurück auf Lager* aktivieren.
1. Führen Sie dieselbe Abfrage aus Schritt 8 aus.

<u>Erwartete Ergebnisse</u>:

Wenn Sie die *Zurück auf Lager* während der Erstellung des Kreditmemo die `inventory_reservation` -Tabelle keinen Datensatz enthält, der dem Kreditmemo entspricht.

<u>Tatsächliche Ergebnisse</u>:

Auch wenn Sie die *Zurück auf Lager* während der Erstellung des Credit-Memos wird ein Datensatz zu `inventory_reservation` Tabelle mit `creditmemo_created` Ereignistyp. Außerdem wurde der Datensatz mit dem Credit Memo im `inventory_reservation` -Tabelle weist eine Menge von 10 auf, obwohl Sie das Kreditmemo für nur eine Menge erstellt haben.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
