---
title: "ACSD-48204: Katalogpreisregel, die basierend auf dem Attribut *Ja/Nein* erstellt wurde, berücksichtigt den ausgewählten Umfang nicht."
description: Wenden Sie den Patch ACSD-48204 an, um das Adobe Commerce-Problem zu beheben, bei dem die auf dem Attribut *Ja/Nein* erstellte Katalogpreisregel den ausgewählten Umfang nicht berücksichtigt.
exl-id: 9b0b4d62-c4c5-40d7-a279-52f59ee7ac42
feature: Admin Workspace, Attributes, Catalog Management, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# ACSD-48204: Katalogpreisregel erstellt basierend auf *Ja/Nein* Attribut berücksichtigt nicht den ausgewählten Umfang

Der Patch ACSD-48204 behebt das Problem, bei dem die Katalogpreisregel basierend auf *Ja/Nein* -Attribut berücksichtigt nicht den ausgewählten Bereich. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28 ist installiert. Die Patch-ID lautet ACSD-48204. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.2-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Katalogpreisregel, die basierend auf *Ja/Nein* -Attribut berücksichtigt nicht den ausgewählten Bereich.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie zwei Websites (Standard und W2).
1. Erstellen Sie das Produktattribut von *Ja/Nein* Typ.
   * Satz [!UICONTROL Default value] = [!UICONTROL No]
   * [!UICONTROL Scope] = [!UICONTROL Website]
   * [!UICONTROL Use for Promo Rule Conditions] = [!UICONTROL Yes]
1. Erstellen Sie ein konfigurierbares Produkt basierend auf einem beliebigen Attribut mit zwei Varianten (V1 und V2).
   * Fügen Sie die *Ja/Nein* Attribut zum Attributsatz mit konfigurierbaren Varianten
   * Setzen Sie für eine der Varianten (V1) den Wert auf *[!UICONTROL Yes]* auf der nicht standardmäßigen Website (W2)
1. Erstellen Sie eine Katalogregel:
   * Auf beide Websites angewendet
   * Bedingung: *Ja/Nein* Attributwert ist *[!UICONTROL Yes]*
   * Rabatt = 50 %
1. Öffnen Sie das konfigurierbare Produkt auf der nicht standardmäßigen Website (W2).
1. Vergewissern Sie sich, dass auf die V1-Variante der 50 %-Rabatt angewendet wird.
1. Öffnen Sie die V1-Variante im Adobe Commerce Admin.
   * Zur Standardwebsite wechseln
   * Nehmen Sie keine Änderungen vor und speichern Sie das Produkt
1. Aktualisieren Sie die konfigurierbare Produkt-Storefront-Seite.

<u>Erwartete Ergebnisse</u>:

Für die V1-Variante wird weiterhin der 50-%-Rabatt angewendet, da keine Änderungen vorgenommen wurden.

<u>Tatsächliche Ergebnisse</u>:

Der Rabatt verschwindet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
