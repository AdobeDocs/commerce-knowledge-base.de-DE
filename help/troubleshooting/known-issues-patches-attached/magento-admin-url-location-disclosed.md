---
title: Speicherort der Adobe Commerce-Admin-URL angegeben
description: Dieser Artikel enthält einen Patch für das Adobe Commerce-Sicherheitsproblem, bei dem der URL-Speicherort des Admin-Bedienfelds offen gelegt werden kann. Die Kenntnis der URL-Position könnte die Automatisierung von Angriffen erleichtern.
exl-id: fe147ad5-6019-46c1-b48c-6b957b6e1582
feature: Admin Workspace
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# Speicherort der Adobe Commerce-Admin-URL angegeben

Dieser Artikel enthält einen Patch für das Adobe Commerce-Sicherheitsproblem, bei dem der URL-Speicherort des Admin-Bedienfelds offen gelegt werden kann. Die Kenntnis der URL-Position könnte die Automatisierung von Angriffen erleichtern.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.X.X
* Adobe Commerce On-Premise 2.X.X
* Magento Open Source 2.X.X

## Problem

In Magento Open Source und Adobe Commerce wurde ein Problem entdeckt, das zum Offenlegen des URL-Speicherorts des Admin-Bedienfelds verwendet werden kann. Obwohl es derzeit keinen Grund zu der Annahme gibt, dass dieses Problem direkt zu einem Kompromiss führen würde, könnte es durch das Wissen über den URL-Standort einfacher sein, Angriffe zu automatisieren.

## Lösung

Um das Problem zu beheben, wenden Sie bitte den an diesen Artikel angehängten Patch an. Um es herunterzuladen, klicken Sie auf den folgenden Link:

* Herunterladen [PRODSECBUG-2432\_EE\_2.1.17\_composer.patch](assets/PRODSECBUG-2432_EE_2.1.17_composer.patch.zip) - für die Versionen 2.1.13-2.1.17, Adobe Commerce, Magento Open Source
* Herunterladen [PRODSECBUG-2432\_EE\_2.2.8\_composer.patch](assets/PRODSECBUG-2432_EE_2.2.8_composer.patch.zip) - für die Versionen 2.2.0-2.2.8 alle Editionen
* Herunterladen [PRODSECBUG-2432\_EE\_2.3.1\_composer.patch](assets/PRODSECBUG-2432_EE_2.3.1_composer.patch.zip) - für die Versionen 2.3.0-2.3.1 alle Editionen

Wenn Sie keinen Patch für Ihr Produkt/Ihre Version sehen, aktualisieren Sie auf die neueste Sicherheitsversion und wenden Sie dann den Patch an.

Adobe empfiehlt dringend, das Pflaster so schnell wie möglich anzuwenden, auch wenn Sie keine Symptome eines Angriffs hatten.

## Anwenden des Pflasters

Siehe [Anwenden eines von Adobe Commerce bereitgestellten Komponentenpatches](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) für Anweisungen.

## Sonstige Sicherheitsempfehlungen

Adobe empfiehlt Händlern außerdem dringend, Tools bereitzustellen, um ihr Admin Panel zu schützen, einschließlich Zweifaktorauthentifizierung, VPN, IP-Zulassungsauflistung und mehr. Detaillierte Informationen finden Sie in den folgenden Blogs und Dokumentationen:

* [5 Sofortmaßnahmen gegen Protect gegen Brute-Force-Angriffe](https://magento.com/security/best-practices/5-immediate-actions-protect-against-brute-force-attacks)
* [Protect - Ihr Magento-Installationskennwort - Tipps für neue Updates](https://magento.com/security/best-practices/protect-your-magento-installation-password-guessing-new-update)
* [Best Practices für die Sicherheit](https://magento.com/security/best-practices/security-best-practices)
* Hinzufügen und Konfigurieren der Zwei-Faktor-Authentifizierung in Adobe Commerce für [2.3.x](https://docs.magento.com/user-guide/v2.3/stores/security-two-factor-authentication.html) und [2.4.x](https://docs.magento.com/user-guide/stores/security-two-factor-authentication.html)
