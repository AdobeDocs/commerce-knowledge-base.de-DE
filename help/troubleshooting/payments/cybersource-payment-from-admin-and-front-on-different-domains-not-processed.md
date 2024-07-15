---
title: Zahlung über Cyberquellen von Admin und Front auf verschiedenen Domänen nicht verarbeitet
description: Dieser Artikel enthält einen Patch für die bekannte Adobe Commerce 2.3.0-Einschränkung, die sich darauf bezieht, keine Cybersource-Zahlungen sowohl aus der Storefront als auch aus dem Commerce-Administrator zu verarbeiten, wenn sie sich auf unterschiedlichen Domänen befinden.
exl-id: 948d5907-70bd-4890-bc8a-23e04b116018
feature: Admin Workspace, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---

# Zahlung über Cyberquellen von Admin und Front auf verschiedenen Domänen nicht verarbeitet

Dieser Artikel enthält einen Patch für die bekannte Adobe Commerce 2.3.0-Einschränkung, die sich darauf bezieht, keine Cybersource-Zahlungen sowohl aus der Storefront als auch aus dem Commerce-Administrator zu verarbeiten, wenn sie sich auf unterschiedlichen Domänen befinden.

>[!NOTE]
>
>Die zentrale Adobe Commerce Cybersource-Zahlungsintegration ist seit 2.3.3 veraltet und wird in 2.4.0 vollständig entfernt. Verwenden Sie stattdessen die offizielle Erweiterung [vom Marketplace aus.](https://marketplace.magento.com/cybersource-global-payment-management.html)

## Problem

Die vorherige Implementierung der Cybersource-Integration ermöglichte nur die Verarbeitung von Zahlungen aus einer Domain. Wenn sich Ihre Adobe Commerce-Storefront daher in einer anderen Domäne als der Commerce-Administrator befindet, erhalten Sie beim Versuch, eine Bestellung mit Cybersource im Admin zu platzieren, den folgenden Fehler: &quot; *Von X-Frame-Optionen verweigertes Laden: https://%your\_domain%/cybersource/SilentOrder/TokenResponse/ erlaubt kein ursprungsübergreifendes Framing.* ..&quot;

<u>Zu reproduzierende Schritte</u>:

1. Richten Sie Admin für eine andere Subdomäne ein.
1. Konfigurieren Sie Cybersource für den Speicher unter &quot;**Stores**&quot;> &quot;Einstellungen&quot;> &quot;**Konfiguration**&quot;> &quot;**Verkauf**&quot;> &quot;**Zahlungsmethoden**&quot;> &quot;**CyberSource**&quot;.
1. Wechseln Sie zu **Verkauf** > **Bestellungen**.
1. Erstellen Sie eine neue Bestellung.
1. Erstellen Sie einen neuen Kunden.
1. Geben Sie Kundendetails ein.
1. Geben Sie Bestelldetails (Produkte, Versandmethode) ein.
1. Wählen Sie Cybersource als Zahlungsmethode aus.
1. Bestellung absenden.

<u>Erwartetes Ergebnis</u>: Die Reihenfolge wird ohne Probleme platziert.

<u>Tatsächliches Ergebnis</u>: Auf der Seite &quot;Bestellung&quot;wird ein Ladesymbol angezeigt, die Reihenfolge wird jedoch nie platziert. Der Fehler wird in der Konsole angezeigt.

## Lösung

Der angehängte Patch verbessert die Integration mit Cybersource. Nachdem Sie den Patch angewendet haben, müssen Sie ein weiteres Profil mit Cybersource zur Verarbeitung von Zahlungen in der Admin-Konsole erstellen und die erforderlichen Anmeldeinformationen in der Cybersource-Konfiguration im Commerce-Admin unter **Stores** > Einstellungen > **Konfiguration** > **Verkauf** > **Zahlungsmethoden** > **CyberSource** hinzufügen.

>[!NOTE]
>
>Die Verbesserung ist in Adobe Commerce-On-Premise- und Cloud-Infrastruktur 2.2.9 und 2.3.1 enthalten.

## Patch

Es gibt mehrere Patches, die an diesen Artikel angehängt sind, verschiedene Patches für verschiedene Versionen. Um einen Patch herunterzuladen, scrollen Sie nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link:

* [MDVA-5914\_EE\_2.1.9\_COMPOSER\_v3.patch herunterladen](assets/MDVA-5914_EE_2.1.9_COMPOSER_v3.patch.zip)
* [MDVA-8609\_EE\_2.2.2\_COMPOSER\_v2.patch herunterladen](assets/MDVA-8609_EE_2.2.2_COMPOSER_v2.patch.zip)
* [MDVA-12964\_EE\_2.2.5\_COMPOSER\_v1.patch herunterladen](assets/MDVA-12964_EE_2.2.5_COMPOSER_v1.patch.zip)
* [MDVA-16643\_EE\_2.3.0\_COMPOSER\_v1.patch herunterladen](assets/MDVA-16643_EE_2.3.0_COMPOSER_v1.patch.zip)

## Kompatible Adobe Commerce-Versionen

Die Patches wurden für eine bestimmte Version erstellt, die im Patch-Dateinamen vermerkt ist. Beispielsweise wurde MDVA-5914\_EE\_2.1.9\_COMPOSER\_v3.patch für Adobe Commerce 2.1.9 erstellt und ist der beste Patch für diese Version.

Die Patches sind auch mit den folgenden Versionen kompatibel:

* Adobe Commerce lokal 2.1.3-2.1.17; Adobe Commerce auf Cloud-Infrastruktur 2.1.5-2.12 (MDVA-5914\_EE\_2.1.9\_COMPOSER\_v3.patch)
* Adobe Commerce lokal 2.2.0-2.2.3; Adobe Commerce auf Cloud-Infrastruktur 2.2.0-2.2.3 (MDVA-8609\_EE\_2.2.2\_COMPOSER\_v2.patch)
* Adobe Commerce lokal 2.2.4-2.2.7; Adobe Commerce auf Cloud-Infrastruktur 2.2.4-2.2.7 (MDVA-12964\_EE\_2.2.5\_COMPOSER\_v1.patch)
* Adobe Commerce lokal 2.2.8, 2.3.0; Adobe Commerce auf Cloud-Infrastruktur 2.3.0 (MDVA-16643\_EE\_2.3.0\_COMPOSER\_v1.patch)

## Anwenden eines Pflasters

Anweisungen finden Sie unter [Anwenden eines von Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) bereitgestellten Composer-Patches in unserer Support-Wissensdatenbank.

## Attached Files
