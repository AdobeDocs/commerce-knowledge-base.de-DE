---
title: 'ACSD-46703: Drag-and-Drop der Produktanpassung funktioniert nicht'
description: Dieser Artikel bietet eine Lösung für den Fall, dass die anpassbaren Optionen zum Ziehen und Ablegen des Produkts nicht wie erwartet funktionieren.
exl-id: 49b29495-d225-4f34-ac76-b7294a86aea6
feature: Products
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# ACSD-46703: Drag-and-Drop der Produktanpassung funktioniert nicht

Der Patch ACSD-46703 behebt das Problem, dass die anpassbaren Optionen des Produkts (Drag-and-Drop) nicht wie erwartet funktionieren. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20 installiert ist. Die Patch-ID ist ACSD-46703. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des [Quality Patches Tool] auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Benutzende können die anpassbaren Optionen nicht von einer Seite auf eine andere ziehen.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein einfaches Produkt.
1. Fügen Sie dem einfachen Produkt anpassbare Optionen hinzu und stellen Sie sicher, dass Sie über 20 Optionen hinzufügen, was zu einer Paginierung führt.
1. Versuchen Sie, eine anpassbare Option (Drag-and-Drop) innerhalb derselben Seite zu verschieben.
1. Versuchen Sie jetzt, eine anpassbare Option von Seite zwei auf Seite eins zu verschieben.

<u>Erwartete Ergebnisse</u>:

* Sie können die anpassbaren Optionen per Drag-and-Drop von einer Seite auf eine andere ziehen.
* Sie können die Werte mithilfe der Drag-and-Drop-Funktion sortieren, auch für mehrere Seiten.

<u>Tatsächliche Ergebnisse</u>:

Sie können mit der Drag-and-Drop-Funktion keinen Wert auf eine andere Seite verschieben.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Quality Patches Tools > Usage](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im Handbuch Quality Patches Tool.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html?lang=de) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im Handbuch Quality Patches Tool.
