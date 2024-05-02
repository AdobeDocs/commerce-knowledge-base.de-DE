---
title: "MDVA-30112: Unstimmigkeiten bei Zahlenreservierungen"
description: Der Patch MDVA-30112 behebt das Problem, bei dem eine unerwartet große Anzahl von [Reservierungsinkonsistenzen](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#what-causes-reservation-inconsistencies) in der Tabelle "inventory_reservation"vorhanden ist. Inkonsistenzen bei Reservierungen umfassen nicht registrierte offene Bestellungen und komplette Bestellungen, die nicht registriert sind. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.2 behoben wurde.
exl-id: db74fb61-dfeb-4e99-8513-d36fd68d2267
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---

# MDVA-30112: Unstimmigkeiten bei Zahlenreservierungen

Der Patch MDVA-30112 löst das Problem, dass Sie eine unerwartet große Anzahl von [Inkonsistenzfehler](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#what-causes-reservation-inconsistencies) im `inventory_reservation` Tabelle. Inkonsistenzen bei Reservierungen umfassen nicht registrierte offene Bestellungen und komplette Bestellungen, die nicht registriert sind. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 ist installiert. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.2 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce in Cloud-Infrastruktur 2.3.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce lokal und Adobe Commerce auf Cloud-Infrastruktur 2.3.4 - 2.3.5-p2, 2.4.0 - 2.4.1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die [Bounch-Größe](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#list-inconsistencies-command) -Wert ist der Wert für die Anzahl der Bestellungen, die gleichzeitig geladen werden sollen. Wenn mehr Bestellungen als dieser Wert vorhanden sind, betrachtet Adobe Commerce die Bestellungen mit dem Status &quot;Ausstehend&quot;als Inkonsistenzen.

>[!NOTE]
>
>Es gibt einen Patch MDVA-33281, der drei weitere Inventarinkonsistenzprobleme behebt. Dies beinhaltet einen PHP Fatal-Fehler beim Ausführen. `bin/magento inventory:reservation:list-inconsistencies` in der CLI. Ein weiteres Problem, das behoben wird, sind doppelte Daten in der Inkonsistenzliste. Außerdem das Problem, bei dem eine Reservierung erstellt wird, bevor eine Bestellung aufgegeben wurde (vorherige Realisierung basierend auf der Reservierung nach der Bestellung). Die Lösung finden Sie unter [MDVA-33281: Unstimmigkeitsprobleme bei Beständen](/help/support-tools/patches-available-in-qpt-tool/v1-0-14/mdva-33281-magento-patch-inventory-inconsistency-issues.md) in unserer Wissensdatenbank.

<u>Voraussetzungen</u>:

Sie führen den folgenden Befehl in der CLI aus, um Reservierungsinkonsistenzen in der `inventory_reservation` table:

```
magento inventory:reservation:list-inconsistencies
```

Sie sehen eine unerwartet große Anzahl von Reservierungsinkonsistenzen und/oder der Befehl wird nie abgeschlossen.

<u>Zu reproduzierende Schritte</u>:

1. Führen Sie den folgenden Befehl in der CLI aus, um die Inkonsistenzen zu beheben:

   ```
   bin/magento inventory:reservation:list-inconsistencies -r | bin/magento inventory:reservation:create-compensations
   ```

1. Drei Bestellungen geben:
   * Weisen Sie jedem ein Produkt zu.
   * Verwenden Sie die Zahlungsmethode Check/Money Order , sodass der Bestellstatus &quot;ausstehend&quot;lautet.
1. Es werden drei Datensätze mit -1 Menge im `inventory_reservation` Tabelle. Führen Sie den folgenden Befehl in der CLI aus, um Inkonsistenzen anzuzeigen:

   ```
   bin/magento inventory:reservation:list-inconsistencies
   ```

   Dadurch werden keine Ergebnisse zurückgegeben, was korrekt ist.

1. Führen Sie den folgenden Befehl in der CLI aus:

   ```
   Execute bin/magento inventory:reservation:list-inconsistencies      --bunch-size 1
   ```

   Sie sehen, dass die Statusbestellungen &quot;ausstehend&quot;als Inkonsistenzen angezeigt werden.

1. Führen Sie den folgenden Befehl in der CLI aus:

   ```
   bin/magento inventory:reservation:list-inconsistencies      -r --bunch-size 1 | bin/magento inventory:reservation:create-compensations
   ```

<u>Erwartete Ergebnisse</u>:

Adobe Commerce sollte Inkonsistenzen von &quot;ausstehenden&quot;Statustexten nicht beheben. Die Unstimmigkeiten bei den Lagerbeständen sollten für Bestellungen mit dem Status &quot;vollständig&quot;, &quot;geschlossen&quot;und &quot;storniert&quot;behoben werden.

<u>Tatsächliche Ergebnisse</u>:

Wenn es Bestellungen gibt, die größer als der angegebene Wert für die Bounce-Größe sind, betrachtet Adobe Commerce Bestellungen mit dem Status &quot;Ausstehend&quot;als Inkonsistenzen und fügt mehrere Inkonsistenzen hinzu, wodurch Datensätze für dieselbe Bestellung aufgelöst werden.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
