---
title: "MDVA-41236: Es ist nicht möglich, bestehende geplante Updates für das Produkt zu erstellen oder zu bearbeiten."
description: Der Patch MDVA-41236 behebt das Problem, dass Benutzer nicht in der Lage sind, neue geplante Updates für das Produkt zu erstellen oder zu bearbeiten, wenn das "Enddatum"zuvor entfernt wurde. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.5 installiert ist. Die Patch-ID lautet MDVA-41236. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: 00d6c0af-f248-49f6-aaa2-3ae3c0294832
feature: Products, Staging
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# MDVA-41236: Es können keine neuen geplanten Updates für das Produkt erstellt oder bearbeitet werden

Der Patch MDVA-41236 behebt das Problem, dass Benutzer nicht in der Lage sind, neue geplante Updates für das Produkt zu erstellen oder zu bearbeiten, wenn das &quot;Enddatum&quot;zuvor entfernt wurde. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.5 ist installiert. Die Patch-ID lautet MDVA-41236. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.3 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Benutzer können keine neuen Zeitpläne erstellen oder vorhandene Zeitpläne für Produkte bearbeiten, wenn das Enddatum zuvor entfernt wurde.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein Produkt mit dem Status , der auf *disable*.
1. Fügen Sie eine geplante Aktualisierung hinzu, um dieses Produkt zu aktivieren.
   * Fügen Sie zukünftige Start- und Enddaten hinzu.
1. Bearbeiten Sie die geplante Aktualisierung, indem Sie die **Enddatum**.
1. Bearbeiten Sie den Zeitplan erneut und versuchen Sie, eine **Enddatum**. Ein Fehler tritt auf.
1. Aktualisieren Sie die Seite und navigieren Sie erneut zu **Geplante Aktualisierung bearbeiten**.
1. Klicks **Aus Aktualisierung entfernen** > **Aktualisieren löschen**.
1. Jetzt sollte das geplante Update nicht über der Seite zur Produktbearbeitung angezeigt werden.
1. Versuchen Sie, eine neue geplante Aktualisierung zu erstellen, die sich mit der vorherigen Dauer überschneidet.

<u>Erwartete Ergebnisse</u>:

* In Schritt 4 ist kein Fehler aufgetreten. Der Administrator kann die geplante Aktualisierung ohne Fehler aktualisieren, da der Zeitplan noch nicht aktiv ist.
* Der Administrator kann die vorherige Aktualisierung löschen und eine neue erstellen.

<u>Tatsächliche Ergebnisse</u>:

Benutzer erhalten die folgende Fehlermeldung:

*error: Zukünftige Aktualisierung ist bereits in diesem Zeitraum vorhanden. Legen Sie einen anderen Bereich fest und versuchen Sie es erneut.*


## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) Abschnitt.
