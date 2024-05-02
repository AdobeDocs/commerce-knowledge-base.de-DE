---
title: '"MDVA-31006: Fehler "Paypal Duplicate Orders 10415"'
description: Der Patch MDVA-31006 behebt das Problem, dass bei der Verwendung der PayPal Express Checkout-Zahlung doppelte Bestellungen mit einem 10415-Fehler erstellt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 installiert ist. Das Problem wurde in Adobe Commerce 2.4.2 behoben.
exl-id: ff471fd3-f580-4149-83bc-67f6fce8e28d
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---

# MDVA-31006: Fehler Paypal Duplicate Orders 10415

Der Patch MDVA-31006 behebt das Problem, dass bei der Verwendung der PayPal Express Checkout-Zahlung doppelte Bestellungen mit einem 10415-Fehler erstellt werden. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 installiert ist. Das Problem wurde in Adobe Commerce 2.4.2 behoben.

## Betroffene Produkte und Versionen

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.2 - 2.4.0

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Benutzer wird nicht an die Adobe Commerce-Auftragserfolgsseite gesendet, sodass er die leere Seite aktualisiert und die zweite Bestellung aufgegeben wird, was zu doppelten Bestellungen führt.

<u>Voraussetzungen</u>:

* Adobe Commerce ist installiert.
* PayPal Express Checkout Zahlung ist konfiguriert.
* Melden Sie sich beim Commerce-Administrator an. Navigieren Sie zu **Stores** > **Konfiguration** > **Vertrieb** > **Zahlungsmethoden** > Auswählen **Paypal Express Checkout** > **Konfigurieren** > **Erweiterte Einstellungen** > **Schritt zur Überprüfung der Bestellung überspringen** > *Nein*.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich als Benutzer an.
1. Element auswählen und auf **Zum Warenkorb hinzufügen**.
1. Klicken Sie auf den Warenkorb und klicken Sie auf **Zur Kasse gehen**.
1. Fahren Sie mit dem PayPal Express-Fenster fort und zahlen Sie eine Zahlung.
1. Sie werden zur Adobe Commerce-Bestellüberprüfungsseite weitergeleitet.
1. Drücken Sie die **Bestellung platzieren** Schaltfläche.
1. Emulieren Sie den Systemfehler aufgrund von Problemen mit der Serverinfrastruktur. Dem Benutzer wird eine leere Seite angezeigt.
1. Aktualisieren Sie die Seite.

<u>Erwartete Ergebnisse</u>:

* Der Kunde wird zur Seite &quot;Auftragsüberprüfung&quot;umgeleitet und erhält eine Fehlermeldung &quot;*Ein erfolgreicher Zahlungsvorgang wurde bereits abgeschlossen. Überprüfen Sie bitte, ob die Bestellung aufgegeben wurde.*&quot;
* In der Datei payment.log, die sich unter `/var/log/payment.log`, gibt es einen Fehler 10415, aber nur eine Bestellung wurde erstellt.

<u>Tatsächliche Ergebnisse</u>:

* Da der Kunde nicht an die Adobe Commerce-Auftragserfolgsseite gesendet wird, wird die leere Seite aktualisiert und eine zweite Bestellung aufgegeben, sodass zwei duplizierte Bestellungen erstellt werden.
* In der Datei payment.log, die sich unter `/var/log/payment.log`, gibt es einen Fehler 10415.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
