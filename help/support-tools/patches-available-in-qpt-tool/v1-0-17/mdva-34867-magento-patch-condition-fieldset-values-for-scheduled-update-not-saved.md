---
title: "MDVA-34867: Feldsatzwerte für Bedingungen für geplante Aktualisierung nicht gespeichert"
description: Der Patch MDVA-34867 behebt das Problem, dass der Wert für die Bedingung im neuen Zeitplan-Update beim Bearbeiten einer Katalogpreisregel nicht gespeichert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.3 behoben wurde.
exl-id: bf514ccc-bebd-4ed2-868f-28b02b1e253e
feature: Catalog Management, Categories
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# MDVA-34867: Feldsatzwerte für Bedingungen für geplante Aktualisierung nicht gespeichert

Der Patch MDVA-34867 behebt das Problem, dass der Wert für die Bedingung im neuen Zeitplan-Update beim Bearbeiten einer Katalogpreisregel nicht gespeichert wird. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 ist installiert. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.4.0-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce über Cloud-Infrastruktur und Adobe Commerce vor Ort 2.3.0 - 2.4.2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Wert für die Bedingung im neuen Zeitplan-Update wird beim Bearbeiten einer Katalogpreisregel nicht gespeichert.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich bei Admin an.
1. Erstellen Sie eine **Katalogregel** mit **Bedingung** = &quot;*Kategorie 1*&quot;.
1. Planen Sie ein Update mit einem zukünftigen Startdatum (Beispiel: morgen) und legen Sie **Bedingung** = &quot;*Kategorie ist 2, 3* und speichern Sie die Aktualisierung.
1. Klicken Sie auf **Anzeigen/Bearbeiten** für die oben erstellte Aktualisierung und überprüfen Sie die Bedingungsfelder.

<u>Erwartete Ergebnisse</u>:

Die **Katalogregel**  **Bedingung** = &quot;*Kategorie ist 2, 3*&quot;, wie erwartet.

<u>Tatsächliche Ergebnisse</u>:

Die **Katalogregel**  **Bedingung** = &quot;*Kategorie 1*&quot;, was bedeutet, dass die Aktualisierung nicht gespeichert wurde.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) Abschnitt.
