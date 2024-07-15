---
title: "MDVA-43726: Katalogpreisregel wird nach partieller Neuindizierung nicht angewendet"
description: Der Patch MDVA-43726 behebt das Problem, dass die Katalogpreisregel, die auf einer Attributübereinstimmung auf Store-Ebene basiert, nach einer partiellen Neuindizierung nicht angewendet werden kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-43726. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: 70e7e1d2-e601-4fed-9274-a1a619de29e1
feature: Catalog Management, Categories, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# MDVA-43726: Katalogpreisregel wird nach partieller Neuindizierung nicht angewendet

Der Patch MDVA-43726 behebt das Problem, dass die Katalogpreisregel, die auf einer Attributübereinstimmung auf Store-Ebene basiert, nach einer partiellen Neuindizierung nicht angewendet werden kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-43726. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.3 - 2.4.2-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Katalogpreisregel, die auf der Attributübereinstimmung auf Store-Ebene basiert, wird nach einer partiellen Neuindizierung nicht angewendet.

<u>Zu reproduzierende Schritte</u>:

1. Legen Sie den Indexermodus fest, um planmäßig ausgeführt zu werden.
1. Erstellen Sie zwei konfigurierbare Produktattribute. Beispiel: Farbe (visuelles Muster) und Größe (Textmuster).
1. Erstellen Sie ein konfigurierbares Produkt mit beiden Attributen, die Sie in Schritt 2 erstellt haben.
1. Erstellen Sie nach dem Erstellen der Produkte ein Attribut vom Typ **Ja/Nein** und machen Sie es in den Regelbedingungen sichtbar.
1. Fügen Sie dieses Attribut zum standardmäßigen Attributsatz hinzu.
1. Erstellen Sie eine Katalogpreisregel, die angewendet werden soll, wenn dieses Attribut auf **Ja** festgelegt ist.
1. Öffnen Sie eines der einfachen Produkte, die sich auf das konfigurierbare Produkt beziehen.
1. Ändern Sie den Umfang, in dem die Ansicht gespeichert werden soll, und aktualisieren Sie den Attributwert auf **Ja**.
1. Führen Sie die `CRON` aus und überprüfen Sie den Preis auf der Vorderseite.
1. Führen Sie eine vollständige Neuindizierung durch. Nochmals, überprüfen Sie den Preis auf der Vorderseite.
1. Aktualisieren Sie die konfigurierbare Produktkategorie.
1. Führen Sie die `CRON` aus und überprüfen Sie den Preis erneut auf der Vorderseite.

<u>Erwartete Ergebnisse</u>:

Die Katalogregel wird korrekt ohne vollständige Neuindizierung mit inkrementellen Indizes angewendet.

<u>Tatsächliche Ergebnisse</u>:

Die Katalogregel gilt nicht ohne vollständige Neuindizierung.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
