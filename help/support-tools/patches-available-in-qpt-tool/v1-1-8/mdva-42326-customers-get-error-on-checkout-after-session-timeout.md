---
title: "MDVA-42326: Kunden erhalten beim Checkout nach Sitzungs-Timeout einen Fehler."
description: Der Patch MDVA-42326 behebt das Problem, dass Kunden nach dem Sitzungs-Timeout beim Checkout einen Fehler beim Checkout erhalten, selbst wenn der beständige Warenkorb aktiviert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 installiert ist. Die Patch-ID lautet MDVA-42326. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
exl-id: bc9b71de-510d-4c4e-8b0d-9abf9a3e447f
feature: Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# MDVA-42326: Kunden erhalten beim Checkout nach Sitzungs-Timeout einen Fehler

Der Patch MDVA-42326 behebt das Problem, dass Kunden nach dem Sitzungs-Timeout beim Checkout einen Fehler beim Checkout erhalten, selbst wenn der beständige Warenkorb aktiviert ist. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 ist installiert. Die Patch-ID lautet MDVA-42326. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Kunden erhalten nach dem Sitzungs-Timeout beim Checkout einen Fehler, selbst wenn der beständige Warenkorb aktiviert ist.

<u>Voraussetzungen</u>:

1. Navigieren Sie zu **Konfiguration** > **Allgemein** > **Web** > **Standard-Cookie-Einstellungen** > **Cookie-Lebensdauer** und auf **120**.
1. Navigieren Sie zu **Konfiguration** > **Kunden** > **Kundenkonfiguration** > **Online-Kundenoptionen** und legen Sie beide Werte auf **2**.
1. Navigieren Sie zu **Konfiguration** > **Kunden** > **Persistenter Warenkorb** und auf **Aktivieren**.
1. Navigieren Sie zu **Konfiguration** > **Vertrieb** > **Zahlungsmethoden** und deaktivieren Sie alle Zahlungsmethoden außer **Überprüfen/Money Order** (sollte aktiviert sein).

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich als Kunde an und fügen Sie einige Produkte zum Warenkorb hinzu.
1. Überprüfen Sie den Warenkorb.
1. Warten Sie zwei Minuten (in Vorbedingung gesetzt); die Sitzung sollte mit einem Timeout beendet werden.
1. Klicks **Zum Checkout gehen** und aktualisieren Sie die Seite nicht.
1. Checkout als Gast, füllen Sie die Lieferadresse aus und wählen Sie eine Versandmethode.
1. Klicks **Nächste**.
1. Im **Überprüfung und Zahlungen** Seite, klicken **Bestellung platzieren**. Da nur eine Zahlungsmethode zulässig ist, sollte der Kunde die Bestellung aufgeben können, ohne die Zahlungsmethode auszuwählen.

<u>Erwartete Ergebnisse</u>:

Der Kunde sollte die Bestellung aufgeben können.

<u>Tatsächliche Ergebnisse</u>:

Der Kunde erhält den folgenden Fehler: *Validierung der Adresse fehlgeschlagen: E-Mail hat ein falsches Format.*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
