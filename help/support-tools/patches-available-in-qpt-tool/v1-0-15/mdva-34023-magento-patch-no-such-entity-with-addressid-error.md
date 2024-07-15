---
title: '"MDVA-34023 Patch: "No such entity with addressId" error"'
description: Der Patch MDVA-34023 behebt das Problem, dass "Keine Entität mit addressId"-Fehler zufällig im Webbrowser eines Kunden auftreten.
exl-id: bdf8f97d-856a-4dd7-bf21-941d1493496c
feature: Variables
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# MDVA-34023 Patch: &quot;No such entity with addressId&quot; error

Der Patch MDVA-34023 behebt das Problem, dass `No such entity with addressId`-Fehler zufällig im Webbrowser eines Kunden auftreten.

Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.15 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce-Version 2.4.3 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce in der Cloud-Infrastruktur 2.3.1

**Kompatibel mit Adobe Commerce-Versionen:** Adobe Commerce für Cloud-Infrastruktur und Adobe Commerce On-Premise 2.3.0 - 2.4.2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zu **Stores** > **Einstellungen** > **Konfiguration** > **Kunden-Registerkarte** > **Persistenter Warenkorb**.
1. Setzen Sie **Persistenz aktivieren** = *Ja*, legen Sie **Persistenz beim Abmelden löschen** = *Nein* fest.    ![persistent_shopping_cart_magento_2.4.1.png](/help/support-tools/patches-available-in-qpt-tool/assets/persistent_shopping_cart_magento_2.4.1.png)
1. Erstellen Sie einen neuen Kunden und definieren Sie die standardmäßigen Versand- und Rechnungsadressen.
1. Melden Sie sich ab.
1. Melden Sie sich mit dem aktivierten Kontrollkästchen **Angaben speichern** an.
1. Wechseln Sie zur Tabelle `customer_entity` DB und ändern Sie die Kennung `default_billing` und `default_shipping` in nicht vorhandene IDs.
1. Melden Sie sich ab.

<u>Erwartete Ergebnisse</u>:

Es werden keine Fehler angezeigt, wie erwartet.

<u>Tatsächliche Ergebnisse</u>:

Das Ausnahmeprotokoll wird generiert:

```php
Exception.log:
{"0":"No such entity with addressId = XXXXX","1":"#0 /vendor\/magento\/module-customer\/Model\/AddressRegistry.php(49): Magento\\Framework
Exception
NoSuchEntityException::singleField('addressId', 'XXXXX')
```

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie im Abschnitt [In QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) verfügbare Patches.
