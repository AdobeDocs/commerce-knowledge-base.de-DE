---
title: Speicherort der Adobe Commerce-Admin-URL angegeben
description: Dieser Artikel enthält einen Patch für das Adobe Commerce-Sicherheitsproblem, bei dem der URL-Speicherort des Admin-Bedienfelds offen gelegt werden kann. Die Kenntnis der URL-Position könnte die Automatisierung von Angriffen erleichtern.
exl-id: fe147ad5-6019-46c1-b48c-6b957b6e1582
feature: Admin Workspace
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '343'
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

* Laden Sie [PRODSECBUG-2432\_EE\_2.1.17\_composer.patch](assets/PRODSECBUG-2432_EE_2.1.17_composer.patch.zip) - für die Versionen 2.1.13-2.1.17, Adobe Commerce, Magento Open Source herunter.
* Laden Sie [PRODSECBUG-2432\_EE\_2.2.8\_composer.patch](assets/PRODSECBUG-2432_EE_2.2.8_composer.patch.zip) - für die Versionen 2.2.0-2.2.8 alle Editionen herunter.
* Laden Sie [PRODSECBUG-2432\_EE\_2.3.1\_composer.patch](assets/PRODSECBUG-2432_EE_2.3.1_composer.patch.zip) - für die Versionen 2.3.0-2.3.1 alle Editionen herunter.

Wenn Sie keinen Patch für Ihr Produkt/Ihre Version sehen, aktualisieren Sie auf die neueste Sicherheitsversion und wenden Sie dann den Patch an.

Adobe empfiehlt dringend, das Pflaster so schnell wie möglich anzuwenden, auch wenn Sie keine Symptome eines Angriffs hatten.

## Anwenden des Pflasters

Anweisungen finden Sie unter [Anwenden eines von Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) bereitgestellten Composer-Patches.

## Sonstige Sicherheitsempfehlungen

Adobe empfiehlt Händlern außerdem dringend, Tools bereitzustellen, um ihr Admin Panel zu schützen, einschließlich Zweifaktorauthentifizierung, VPN, IP-Zulassungsauflistung und mehr. Detaillierte Informationen finden Sie in den folgenden Blogs und Dokumentationen:

* [5 Sofortige Maßnahmen gegenüber Protect gegen Brute-Force-Angriffe](https://magento.com/security/best-practices/5-immediate-actions-protect-against-brute-force-attacks)
* [Protect Ihr Magento-Installationskennwort für die Warnung &quot;Neues Update&quot;](https://magento.com/security/best-practices/protect-your-magento-installation-password-guessing-new-update)
* [Best Practices für die Sicherheit](https://magento.com/security/best-practices/security-best-practices)
* Hinzufügen und Konfigurieren der Zweifaktorauthentifizierung in Adobe Commerce für [2.4.x](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication)
