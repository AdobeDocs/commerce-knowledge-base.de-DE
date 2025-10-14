---
title: Cybersource-Zahlung von Admin und Front auf verschiedenen Domains nicht verarbeitet
description: Dieser Artikel enthält einen Patch für die bekannte Adobe Commerce 2.3.0-Einschränkung, die sich darauf bezieht, dass Cybersource-Zahlungen nicht sowohl von der Storefront als auch vom Commerce-Administrator verarbeitet werden können, wenn sie sich in verschiedenen Domains befinden.
exl-id: 948d5907-70bd-4890-bc8a-23e04b116018
feature: Admin Workspace, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---

# Cybersource-Zahlung von Admin und Front auf verschiedenen Domains nicht verarbeitet

Dieser Artikel enthält einen Patch für die bekannte Adobe Commerce 2.3.0-Einschränkung, die sich darauf bezieht, dass Cybersource-Zahlungen nicht sowohl von der Storefront als auch vom Commerce-Administrator verarbeitet werden können, wenn sie sich in verschiedenen Domains befinden.

>[!NOTE]
>
>Die zentrale Adobe Commerce Cybersource-Zahlungsintegration ist seit 2.3.3 veraltet und wird in 2.4.0 vollständig entfernt. Verwenden Sie stattdessen die [offizielle Erweiterung](https://marketplace.magento.com/cybersource-global-payment-management.html) vom Marketplace.

## Problem

Die vorherige Implementierung der Cybersource-Integration ermöglichte die Verarbeitung von Zahlungen aus nur einer Domain. Wenn sich Ihre Adobe Commerce-Storefront in einer anderen Domain als der Commerce-Admin befindet, erhalten Sie daher beim Versuch, eine Bestellung über Cybersource in Admin aufzugeben, die folgende Fehlermeldung: &quot;*Laden von X-Frame-Optionen verweigert: https://%your\_domain%/cybersource/SilentOrder/TokenResponse/ erlaubt kein ursprungsübergreifendes Framing.* ..“

<u>Schritte zur Reproduktion</u>:

1. Einrichten von Admin in einer anderen Subdomain.
1. Konfigurieren Sie Cybersource für den Store unter **Stores** > Einstellungen > **Konfiguration** > **Verkauf** > **Zahlungsmethoden** > **CyberSource**.
1. Navigieren Sie **Verkauf** > **Bestellungen**.
1. Neue Bestellung erstellen.
1. Neuen Kunden erstellen.
1. Geben Sie Kundendetails ein.
1. Geben Sie Auftragsdetails ein (Produkte, Versandart).
1. Wählen Sie als Zahlungsmethode Cybersource aus.
1. Bestellung übermitteln.

<u>Erwartetes Ergebnis</u>: Die Bestellung wird ohne Probleme aufgegeben.

<u>Tatsächliches Ergebnis</u>: Auf der Bestellseite wird ein Ladesymbol angezeigt, die Bestellung wird jedoch nie aufgegeben. Der Fehler wird in der Konsole angezeigt.

## Lösung

Der angehängte Patch bietet die Verbesserung für die Integration mit Cybersource. Nachdem Sie den Patch angewendet haben, müssen Sie mit Cybersource ein weiteres Profil für die Verarbeitung von Zahlungen in der Admin erstellen und die erforderlichen Anmeldeinformationen in der Cyberquellenkonfiguration in der Commerce Admin unter **Stores** > Settings > **Configuration** > **Sales** > **Payment Methods** > **CyberSource** hinzufügen.

>[!NOTE]
>
>Die Verbesserung ist in den lokalen und Cloud-Infrastrukturen 2.2.9 und 2.3.1 von Adobe Commerce enthalten.

## Fleck

Diesem Artikel sind mehrere Patches beigefügt, verschiedene Patches für verschiedene Versionen. Um einen Patch herunterzuladen, scrollen Sie nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder klicken Sie auf den folgenden Link:

* [MDVA-5914\_EE\_2.1.9\_COMPOSER\_v3.patch herunterladen](assets/MDVA-5914_EE_2.1.9_COMPOSER_v3.patch.zip)
* [MDVA-8609\_EE\_2.2.2\_COMPOSER\_v2.patch herunterladen](assets/MDVA-8609_EE_2.2.2_COMPOSER_v2.patch.zip)
* [MDVA-12964\_EE\_2.2.5\_COMPOSER\_v1.patch herunterladen](assets/MDVA-12964_EE_2.2.5_COMPOSER_v1.patch.zip)
* [MDVA-16643\_EE\_2.3.0\_COMPOSER\_v1.patch herunterladen](assets/MDVA-16643_EE_2.3.0_COMPOSER_v1.patch.zip)

## Kompatible Adobe Commerce-Versionen

Die Patches wurden für eine bestimmte Version erstellt, die im Patch-Dateinamen angegeben ist. Beispielsweise wurde MDVA-5914\_EE\_2.1.9\_COMPOSER\_v3.patch für Adobe Commerce 2.1.9 erstellt und ist der beste Patch, der für diese Version verwendet werden kann.

Die Patches sind auch mit den folgenden Versionen kompatibel:

* Adobe Commerce On-Premises 2.1.3-2.1.17; Adobe Commerce on Cloud Infrastructure 2.1.5-2.12 (MDVA-5914\_EE\_2.1.9\_COMPOSER\_v3.patch)
* Adobe Commerce On-Premises 2.2.0-2.2.3; Adobe Commerce on Cloud Infrastructure 2.2.0-2.2.3 (MDVA-8609\_EE\_2.2.2\_COMPOSER\_v2.patch)
* Adobe Commerce On-Premises 2.2.4-2.2.7; Adobe Commerce on Cloud Infrastructure 2.2.4-2.2.7 (MDVA-12964\_EE\_2.2.5\_COMPOSER\_v1.patch)
* Adobe Commerce On-Premises 2.2.8, 2.3.0; Adobe Commerce on Cloud Infrastructure 2.3.0 (MDVA-16643\_EE\_2.3.0\_COMPOSER\_v1.patch)

## Anwenden eines Pflasters

Anweisungen finden Sie unter [So wenden Sie einen von Adobe bereitgestellten Composer-Patch &#x200B;](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) unserer Support-Wissensdatenbank an.

## Angehängte Dateien
