---
title: Offenlegter Speicherort der Adobe Commerce-Admin-URL
description: Dieser Artikel enthält einen Patch für das Adobe Commerce-Sicherheitsproblem, in dem der URL-Speicherort des Admin-Bedienfelds offen gelegt werden kann. Die Kenntnis des URL-Speicherorts kann die Automatisierung von Angriffen vereinfachen.
exl-id: fe147ad5-6019-46c1-b48c-6b957b6e1582
feature: Admin Workspace
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# Offenlegter Speicherort der Adobe Commerce-Admin-URL

Dieser Artikel enthält einen Patch für das Adobe Commerce-Sicherheitsproblem, in dem der URL-Speicherort des Admin-Bedienfelds offen gelegt werden kann. Die Kenntnis des URL-Speicherorts kann die Automatisierung von Angriffen vereinfachen.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.x.x
* Adobe Commerce On-Premises 2.X.X
* Magento Open Source 2.x.x

## Problem

In Magento Open Source und Adobe Commerce wurde ein Problem erkannt, das verwendet werden kann, um den URL-Speicherort des Admin-Bedienfelds anzugeben. Es gibt derzeit zwar keinen Grund zu der Annahme, dass dieses Problem direkt zu einem Kompromiss führen würde, aber die Kenntnis des URL-Speicherorts könnte die Automatisierung von Angriffen erleichtern.

## Lösung

Um das Problem zu beheben, wenden Sie bitte den Patch an, der diesem Artikel beigefügt ist. Um ihn herunterzuladen, klicken Sie auf den folgenden Link:

* Laden Sie [PRODSECBUG-2432\_EE\_2.1.17\_composer.patch](assets/PRODSECBUG-2432_EE_2.1.17_composer.patch.zip) herunter - für Version 2.1.13-2.1.17, Adobe Commerce, Magento Open Source
* Download [PRODSECBUG-2432\_EE\_2.2.8\_composer.patch](assets/PRODSECBUG-2432_EE_2.2.8_composer.patch.zip) - für Versionen 2.2.0-2.2.8, alle Editionen
* Download [PRODSECBUG-2432\_EE\_2.3.1\_composer.patch](assets/PRODSECBUG-2432_EE_2.3.1_composer.patch.zip) - für Versionen 2.3.0-2.3.1, alle Editionen

Wenn kein Patch für Ihr Produkt/Ihre Version angezeigt wird, aktualisieren Sie auf die neueste Sicherheitsversion, und wenden Sie dann den Patch an.

Adobe empfiehlt dringend, das Pflaster so bald wie möglich aufzukleben, auch wenn bei Ihnen keine Symptome eines Anfalls aufgetreten sind.

## Anbringen des Pflasters

Anweisungen [ Sie unter „Anwenden eines von Adobe Commerce bereitgestellten Composer](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)Patches .

## Weitere Sicherheitsempfehlungen

Adobe empfiehlt außerdem dringend, dass Händler Tools bereitstellen, um ihr Admin-Panel zu schützen, einschließlich Zwei-Faktor-Authentifizierung, VPN, IP-Zulassungsauflistung und mehr. Detaillierte Informationen finden Sie in den folgenden Blogs und in der Dokumentation:

* [5 Sofortige Maßnahmen für Protect gegen Brute-Force-Angriffe](https://magento.com/security/best-practices/5-immediate-actions-protect-against-brute-force-attacks)
* [Protect Ihr Magento-Installationskennwort Raten Sie auf ein neues Update](https://magento.com/security/best-practices/protect-your-magento-installation-password-guessing-new-update)
* [Best Practices für die Sicherheit](https://magento.com/security/best-practices/security-best-practices)
* Hinzufügen und Konfigurieren der Zwei-Faktor-Authentifizierung in Adobe Commerce für [2.4.x](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication)
