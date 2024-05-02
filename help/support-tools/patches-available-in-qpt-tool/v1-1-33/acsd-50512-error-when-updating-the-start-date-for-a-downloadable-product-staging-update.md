---
title: "ACSD-50512: Fehler beim Aktualisieren des Startdatums für ein herunterladbares Produkt-Staging-Update"
description: Wenden Sie den Patch ACSD-51892 an, um das Leistungsproblem von Adobe Commerce zu beheben, bei dem der Fehler *Der herunterladbare Link ist nicht mit dem Produkt verknüpft ist. Überprüfen Sie den Link und versuchen Sie es erneut*, tritt auf, wenn das Startdatum für ein herunterladbares Produkt-Staging-Update aktualisiert wird.
feature: Products, Staging
role: Admin
exl-id: 873357ef-49c3-48f8-a98e-41c48cb9ba8b
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# ACSD-50512: Fehler beim Aktualisieren des Startdatums für herunterladbare Produkt-Staging-Update

Der Patch ACSD-50512 behebt das Problem, bei dem der Fehler *Der herunterladbare Link steht nicht im Zusammenhang mit dem Produkt. Überprüfen Sie den Link und versuchen Sie es erneut* tritt auf, wenn das Startdatum für ein herunterladbares Produkt-Staging-Update aktualisiert wird. Dieser Patch ist verfügbar, wenn die Variable [!DNL Quality Patches Tool (QPT)] 1.1.33 installiert ist. Die Patch-ID ist ACSD-51502. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Fehler *Der herunterladbare Link steht nicht im Zusammenhang mit dem Produkt. Überprüfen Sie den Link und versuchen Sie es erneut* tritt auf, wenn das Startdatum für ein herunterladbares Produkt-Staging-Update aktualisiert wird.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein herunterladbares Produkt mit *herunterladbare Links* und *Beispiellinks*.
1. Erstellen Sie eine geplante Aktualisierung für dasselbe Produkt und speichern Sie das Produkt.
1. Bearbeiten Sie die vorkonfigurierte geplante Aktualisierung (ab Schritt 2) und ändern Sie das Startdatum.
1. Speichern Sie die geplante Aktualisierung.

<u>Erwartete Ergebnisse</u>:

Die Änderungen an der geplanten Aktualisierung werden erfolgreich gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten den Fehler: *Der herunterladbare Link steht nicht im Zusammenhang mit dem Produkt. Link überprüfen und erneut versuchen*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
