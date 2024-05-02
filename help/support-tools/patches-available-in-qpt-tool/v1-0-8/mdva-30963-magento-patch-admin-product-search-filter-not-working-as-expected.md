---
title: "MDVA-30963: Admin-Produktsuchfilter funktioniert nicht erwartungsgemäß"
description: Der Patch MDVA-30963 löst das Problem, dass der Commerce-Administrator und der Produktsuchfilter nicht wie erwartet funktionieren. Werte, die in einem Bereich der Store-Ansicht überschrieben werden, werden auch beim Filtern nach dem Bereich "Alle Store-Ansicht"berücksichtigt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.
exl-id: bde2836e-8954-48e5-b411-08c951ec8620
feature: Admin Workspace, Products, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 0%

---

# MDVA-30963: Admin-Produktsuchfilter funktionieren nicht erwartungsgemäß

Der Patch MDVA-30963 löst das Problem, dass der Commerce-Administrator und der Produktsuchfilter nicht wie erwartet funktionieren. Werte, die in einem Bereich der Store-Ansicht überschrieben werden, werden auch beim Filtern nach berücksichtigt **Alle Store-Ansichten** Umfang der Store-Ansicht. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 ist installiert. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce auf Cloud-Infrastruktur 2.4.0

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.2 - 2.4.1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Satz **Stores** > **Konfiguration** > **Katalog** > **Katalog** > **Preis** > **Katalogpreisumfang** = *Webseite*.
1. Erstellen Sie zwei Websites mit zwei verschiedenen Währungen (die Standardwebsite ist beispielsweise ein indischer Store \[Rupee ₹\], die zweite den US Store \[Dollar $\]).
1. Legen Sie Folgendes fest: **Basiswährung**, **Standardanzeigewährung**, und **Zulässige Währungen**:
   * **Standardkonfiguration** = *US-Dollar (Standard)*
   * **Hauptwebsite** = *Indien, Rupie*
   * **WebsiteUS** = **Use Default** = *US-Dollar*
1. Satz **Stores** > **Wechselkurse** = *1:1*.
1. Erstellen Sie ein einfaches Testprodukt, das beiden Websites zugewiesen wird, mit den folgenden Preisen:
   * **Standardpreis** = **US-Website-Preis** = *123 USD*
   * **Haupt-Website-Preis** = *321 Rupie*
1. Erstellen Sie einen Sub-Admin-Benutzer, der nur Zugriff auf den US-Store hat.
1. Gehen Sie zur US-Storefront und legen Sie ein Produkt in den Warenkorb (Beispiel: *123 USD-Preis*).
1. Melden Sie sich mit dem soeben erstellten Unter-Admin bei Admin an (Beispiel: *Nur US-Administrator*).
1. Navigieren Sie zu **Berichte** > **Produkte im Warenkorb**.

<u>Erwartete Ergebnisse</u>:

Beim Filtern innerhalb der **Alle Store-Ansichten** Umfang der Store-Ansicht, sollte die Produktfilterung den in diesem bestimmten Bereich festgelegten Wert erhalten.

<u>Tatsächliche Ergebnisse</u>:

Werte, die im Bereich einer Store-Ansicht überschrieben werden, werden auch beim Filtern nach dem Bereich &quot;Alle Store-Ansicht&quot;berücksichtigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
