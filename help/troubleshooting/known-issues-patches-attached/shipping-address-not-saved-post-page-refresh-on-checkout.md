---
title: Versandadresse nicht gespeichert Post-Page-Aktualisierung beim Checkout
description: Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce 2.2.3-Problem, bei dem das bereits ausgefüllte Versandadressenformular des Kunden nach dem Aktualisieren der Browserseite beim Checkout erneut leer war. Das Problem trat auf, wenn der beständige Warenkorb aktiviert war.
exl-id: b757e4af-7b1a-41bc-8460-9a6858c7aa5e
feature: Checkout, Orders, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# Versandadresse nicht gespeichert Post-Page-Aktualisierung beim Checkout

Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce 2.2.3-Problem, bei dem das bereits ausgefüllte Versandadressenformular des Kunden nach dem Aktualisieren der Browserseite beim Checkout erneut leer war. Das Problem trat auf, wenn der beständige Warenkorb aktiviert war.

## Problem

Kunden gehen zum Checkout und füllen alle Formulare einschließlich der Lieferadresse aus. Sie gelangen zum Abschnitt &quot;Überprüfung und Zahlungen&quot;und laden die Seite neu. Das Formular ist leer, und die Versandadresse muss erneut eingegeben werden. Beständige Warenkorbfunktionen sind aktiviert.

<u>Zu reproduzierende Schritte</u> :

**Voraussetzungen**: Die persistente Warenkorbfunktion ist aktiviert. Überprüfen Sie, ob es in Admin unter &quot;**Stores** > **Konfiguration** > **Kunden**&quot;oder &quot;**Stores**&quot;> &quot;**Konfiguration**&quot;> &quot;**Vertrieb,**&quot;je nach Adobe Commerce-Version aktiviert ist.

1. Gehen Sie zur Storefront.
1. Fügen Sie Produkte zum Warenkorb hinzu.
1. Fahren Sie fort, um als Gast auszuchecken.
1. Füllen Sie Ihre Lieferadresse aus, wählen Sie Versandoptionen und sichern Sie weiterhin die Zahlung.
1. Gehen Sie zum Abschnitt &quot;Überprüfung und Zahlungen&quot;des Checkouts.
1. Überprüfen Sie, ob die Lieferadresse im Abschnitt &quot;Versand an&quot;angezeigt wird.
1. Aktualisieren Sie die Seite.

<u>Erwartetes Ergebnis</u>:

Sie können mit dem Checkout fortfahren und alle Daten werden gespeichert.

<u>Tatsächliches Ergebnis</u>:

Die Lieferadresse ist leer, Sie müssen sie neu eingeben.

## Patch

Der Patch ist an diesen Artikel angehängt. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link:

[MDVA-9718\_EE\_2.2.3\_COMPOSER\_v1.patch herunterladen](assets/MDVA-9718_EE_2.2.3_COMPOSER_v1.patch.zip)

### Kompatible Adobe Commerce-Versionen

**Der Patch wurde erstellt für:**

* Adobe Commerce 2.2.3

**Der Patch ist auch mit den folgenden Adobe Commerce-Versionen und -Editionen kompatibel (löst das Problem jedoch möglicherweise nicht):**

* Adobe Commerce auf Cloud-Infrastruktur 2.1.13 - 2.1.18
* Adobe Commerce auf Cloud-Infrastruktur 2.2.0 - 2.2.5
* Adobe Commerce On-Premise 2.0.X
* Adobe Commerce vor Ort 2.1.X
* Adobe Commerce vor Ort 2.2.0 - 2.2.2 und 2.2.4 - 2.2.5

## Anwenden des Pflasters

Anweisungen finden Sie unter [Anwenden eines von Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) bereitgestellten Composer-Patches in unserer Support-Wissensdatenbank.

## Attached Files
