---
title: "MDVA-32759 Patch: shared catalogs delete tier price"
description: Der Patch MDVA-32759 behebt das Problem, dass freigegebene Kataloge vorhandene Tier-Preise löschen.
exl-id: c6192d2f-cd25-483e-ba69-01ca62996faf
feature: B2B, Catalog Management
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# Patch MDVA-32759: Geteilte Kataloge löschen Ebenenpreise

Der Patch MDVA-32759 behebt das Problem, dass freigegebene Kataloge vorhandene Tier-Preise löschen.

Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce-Version 2.4.3 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.3.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce über Cloud-Infrastruktur und Adobe Commerce vor Ort 2.3.0 - 2.4.2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Voraussetzungen</u>:

Installieren Sie Adobe Commerce mit B2B mit **B2B-Funktionen** aktiviert.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zu **Stores > Konfiguration > B2B-Funktionen > Unternehmen aktivieren** und **Freigegebener Katalog**.
1. Ausführen `bin/magento cron:run`.
1. Erstellen Sie ein einfaches Produkt, klicken Sie auf **Erweiterte Preise** und fügen Sie **Katalog- und Tier-Preis** und speichern Sie sie.
1. Navigieren Sie zu **Katalog > Freigegebener Katalog > Preise und Struktur festlegen**, klicken Sie auf **Konfigurieren** und deaktivieren Sie in diesem Dropdown-Menü die Auswahl aller Optionen und speichern Sie.
1. Ausführen `bin/magento cron:run`.
1. Öffnen Sie das oben erstellte Produkt und überprüfen Sie die erweiterten Preise.

<u>Erwartete Ergebnisse</u>:

Die Tierpreise sollten nicht wie erwartet aus den Produkten entfernt werden, nachdem alle Produkte aus dem öffentlichen gemeinsamen Katalog entfernt wurden.

<u>Tatsächliche Ergebnisse</u>:

Die Tierpreise werden entfernt, nachdem alle Produkte aus dem öffentlichen freigegebenen Katalog entfernt wurden.


## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
