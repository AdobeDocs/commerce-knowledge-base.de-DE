---
title: "ACSD-48784: Preise für Kundensegmente wurden zwischen Kundengruppen falsch zwischengespeichert."
description: Wenden Sie den Patch ACSD-48784 an, um das Adobe Commerce-Problem zu beheben, bei dem Kundensegmentpreise zwischen Kundengruppen falsch zwischengespeichert werden.
exl-id: 6be11fd0-5c93-4ac7-8664-7e2a289c9e38
feature: Admin Workspace, Cache, Customer Service, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-48784: Die Preise für Kundensegmente wurden zwischen Kundengruppen falsch zwischengespeichert.

Der Patch ACSD-48784 behebt das Problem, dass die Preise für Kundensegmente zwischen Kundengruppen falsch zwischengespeichert werden. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28 ist installiert. Die Patch-ID lautet ACSD-48784. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Kundensegmentpreise werden zwischen den Kundengruppen falsch zwischengespeichert.

<u>Voraussetzungen</u>:

Konfigurieren [!DNL Varnish] oder [!DNL Fastly].

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie das vollständige Seiten-Caching in Ihrem Store.
1. Melden Sie sich bei der Site als Benutzer mit Sonderpreisen für Kundengruppen an.
1. Gehen Sie zu einer Produktseite für ein Produkt mit Sonderpreisen für Kundengruppen. Beobachten Sie die *Sonderpreis*.
1. Öffnen Sie in einem separaten Browser dieselbe Produktseite wie ein Gastbenutzer, ohne sich anzumelden. Beobachten Sie den regulären Preis.
1. Zugriff auf die Verwaltungsoberfläche von Adobe Commerce und Löschen der Adobe Commerce und [!DNL Fastly] Cache für diesen Store.
1. Entfernen Sie im angemeldeten Browser die `X-Magento-Vary` Cookie.
1. Laden Sie dieselbe Produktseite im angemeldeten Browser mehrmals neu, bis die Zwischenspeicherung vollständig geleert ist.
1. Laden Sie die Produktseite im nicht angemeldeten Browser neu, um jetzt die Preisgestaltung für Kundengruppen anzuzeigen.

<u>Erwartete Ergebnisse</u>:

Auf der Produktseite wird der richtige Preis für bestimmte Kundengruppen angezeigt.

<u>Tatsächliche Ergebnisse</u>:

* Gastbenutzer sehen den speziellen Preis für angemeldete Benutzer.
* Der Mini-Warenkorb zeigt den richtigen Preis an, sobald das Produkt hinzugefügt wurde.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
