---
title: '"MDVA-37897: Falsche Umleitung beim Hinzufügen von Produkten aus "Kürzlich angesehen"'
description: Der Patch MDVA-37897 löst das Problem der falschen Umleitung, wenn Benutzer versuchen, Produkte mit Optionen aus dem Widget "Kürzlich angesehen"hinzuzufügen. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1 installiert ist. Die Patch-ID lautet MDVA-37897. Bitte beachten Sie, dass das Problem in Adobe Commerce-Version 2.4.4 behoben werden soll.
exl-id: f0a86e02-b357-4d2d-8386-e9cc045bcf06
feature: Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# MDVA-37897: Falsche Umleitung beim Hinzufügen von Produkten aus &quot;Kürzlich angesehen&quot;

Der Patch MDVA-37897 löst das Problem der falschen Umleitung, wenn Benutzer versuchen, Produkte mit Optionen aus dem Widget &quot;Kürzlich angesehen&quot;hinzuzufügen. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1 installiert ist. Die Patch-ID lautet MDVA-37897. Bitte beachten Sie, dass das Problem in Adobe Commerce-Version 2.4.4 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce in unserer Cloud-Infrastruktur 2.4.1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.2-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn ein Benutzer versucht, ein Produkt aus dem Abschnitt &quot;Zuletzt angezeigt&quot;hinzuzufügen, für das Optionen ausgewählt werden müssen, wird der Benutzer zur Produktlistenseite und nicht zur Produktdetailseite weitergeleitet.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein einfaches Produkt mit anpassbaren Optionen (Typ: Optionsfeld).
1. Konfigurieren Sie das Widget &quot;Kürzlich angezeigt&quot;so, dass Produkte angezeigt werden.
1. Besuchen Sie Produkte mit anpassbaren Optionen, damit sie im Widget &quot;Kürzlich angesehen&quot;angezeigt werden.
1. Klicken Sie auf **Zum Warenkorb hinzufügen** für eines der Produkte im Widget &quot;Kürzlich angezeigt&quot;.

<u>Erwartete Ergebnisse</u>:

Sie werden zur Produktdetailseite weitergeleitet, um die Optionen auszuwählen.

<u>Tatsächliche Ergebnisse</u>:

Sie werden zur Produktlistenseite weitergeleitet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungstyp die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce On-Premise: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce in unserer Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zu Qualitäts-Patches für Adobe Commerce finden Sie unter:

* [Qualitätspatches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Überprüfen Sie mithilfe des Qualitätssicherungswerkzeugs](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md), ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) verfügbare Patches.
