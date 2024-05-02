---
title: "ACSD-51528: Verschiedenes Verhalten bei der Snake_Case-Formatierung"
description: Wenden Sie den Patch ACSD-51528 an, um das Adobe Commerce-Problem zu beheben, bei dem es unterschiedliche Verhaltensweisen bei der snake_case-Formatierung gibt.
exl-id: dd878321-8032-41f3-8dcd-acb0cc023b44
feature: Variables
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# ACSD-51528: Verschiedene Verhaltensweisen bei der Formatierung von Schlangen-Groß- und Kleinschreibung

Der Patch ACSD-51528 behebt unterschiedliche Verhaltensweisen bei der Formatierung von snake_case. Dieser Patch ist verfügbar, wenn die Variable [!DNL Quality Patches Tool (QPT)] 1.1.32 installiert ist. Die Patch-ID ist ACSD-51528. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das unterschiedliche Verhalten bei der Formatierung von snake_case.

<u>Zu reproduzierende Schritte</u>:

1. Testen Sie die `\Magento\Framework\Api\DataObjectHelper::populateWithArray` -Funktion mit einer Vielzahl verschiedener Eigenschaftsnamen.
1. Die Eigenschaften mit Namen wie *NewPName* in *new_p_name*, stattdessen werden sie in *new_pname*.
1. Außerdem bei Verwendung der *getNewPName* -Funktion im -Objekt, *null* zurückgegeben, da die *Abstraktes Modell* ändert den Aufruf von *new_p_name* Inkompatibilität beider Funktionen.

<u>Erwartete Ergebnisse</u>

Die **[!UICONTROL populateWithArray]** -Funktion sollte die Objekteigenschaften korrekt in snake_case umwandeln, damit sie mit der **[!DNL AbstractModel's]** `Getters` und `Setters`.

<u>Tatsächliche Ergebnisse</u>

Bei Verwendung von **[!UICONTROL populateWithArray]** -Funktion verwenden, führen alle Objekteigenschaften, die zwei oder mehr Großbuchstaben in einer Zeile im Namen enthalten, dazu, dass die Umwandlung snake_case im endgültigen Daten-Array falsch ist.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
