---
title: "MDVA-38393: Katalogregeln funktionieren für konfigurierbare Produkte nicht mehr, wenn ihr einfaches Produkt neu benannt ist."
description: Der Patch MDVA-38393 behebt das Problem, dass Katalogregeln für ein konfigurierbares Produkt nicht mehr funktionieren, wenn sein einfaches Produkt neu benannt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 installiert ist. Die Patch-ID lautet MDVA-38393. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
exl-id: a20856c4-8aff-427b-a404-7afe706be06f
feature: Catalog Management, Categories, Configuration, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# MDVA-38393: Katalogregeln funktionieren für konfigurierbare Produkte nicht mehr, wenn ihr einfaches Produkt neu benannt ist

Der Patch MDVA-38393 behebt das Problem, dass Katalogregeln für ein konfigurierbares Produkt nicht mehr funktionieren, wenn sein einfaches Produkt neu benannt wird. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 ist installiert. Die Patch-ID lautet MDVA-38393. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.3 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Katalogregeln funktionieren für ein konfigurierbares Produkt nicht mehr, wenn sein einfaches Produkt neu benannt wurde.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein konfigurierbares Produkt mit einem zugehörigen einfachen Produkt.
1. Erstellen Sie eine Kategorie.
1. Weisen Sie der neuen Kategorie nur das konfigurierbare Produkt zu.
1. Erstellen Sie neue Katalogregeln:
   * Bedingung = Kategorie enthält \&lt;new category=&quot;&quot; id=&quot;&quot;>
   * Aktion = 50 % Rabatt
   * Aktiv = Ja
1. Führen Sie eine Neuindizierung durch.
1. Überprüfen Sie das konfigurierbare Produkt auf der Vorderseite (der Rabatt sollte angewendet werden).
1. Überprüfen Sie die `catalogrule_product` -Tabelle (das einfache Produkt sollte einen Rabatt haben).
1. Wechseln Sie zum Administrator und ändern Sie den Namen des einfachen Produkts. Dadurch wird der `catalogrule_product_cl` Tabelle.
1. Führen Sie den Cron oder die `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1` Befehl.
1. Überprüfen Sie die `catalogrule_product` Tabelle.

<u>Erwartete Ergebnisse</u>:

Das konfigurierbare Produkt hat einen Rabatt.

<u>Tatsächliche Ergebnisse</u>:

* Die für einfache Produkte erstellten Discount-Datensätze fehlen im `catalogrule_product` Tabelle.
* Das konfigurierbare Produkt am Frontend hat den vollen Originalpreis.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
