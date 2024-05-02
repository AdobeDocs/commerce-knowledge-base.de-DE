---
title: "MDVA-38728: Durch Ändern der Produktsichtbarkeit wird URL-Neufassung für die Haupt-Website erstellt"
description: Der Patch MDVA-38728 behebt das Problem, bei dem durch die Änderung der Produktsichtbarkeit der zweiten Website ein URL-Neuschreiben für die Haupt-Website erstellt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-38728. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: ad1d5f82-294d-485d-acd3-28c3cd0fbf56
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# MDVA-38728: Durch Ändern der Produktsichtbarkeit wird eine URL-Neufassung für die Haupt-Website erstellt.

Der Patch MDVA-38728 behebt das Problem, bei dem durch die Änderung der Produktsichtbarkeit der zweiten Website ein URL-Neuschreiben für die Haupt-Website erstellt wird. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-38728. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.2 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn Sie die Produktsichtbarkeit der zweiten Website ändern, wird eine URL-Umschreibung für die Haupt-Website erstellt.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine zusätzliche Website, einen Store und eine Storeinstanz.
1. Erstellen Sie ein einfaches Produkt.
1. Festlegen der Sichtbarkeit auf **Individuell nicht sichtbar**.
1. Weisen Sie das Produkt nur der zweiten Website zu.
1. Füllen Sie alle anderen erforderlichen Felder aus.
1. Speichern Sie das Produkt.
1. MySQL-Warteschlangen starten:

   ```mysql
   bin/magento queue:consumers:start product_action_attribute.update &
   bin/magento queue:consumers:start product_action_attribute.website.update &
   ```

1. Navigieren Sie zur Produktliste.
1. Wählen Sie das erstellte Produkt aus und aktualisieren Sie das Sichtbarkeitsattribut mithilfe des gebündelten Updates für Katalog und Suche.
1. Überprüfen Sie die URL-Neufassung.

<u>Erwartete Ergebnisse</u>:

Die Neufassung wird für die zweite Website erstellt, der das Produkt zugewiesen ist.

<u>Tatsächliche Ergebnisse</u>:

Die Neufassung wird für die Haupt-Website erstellt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
