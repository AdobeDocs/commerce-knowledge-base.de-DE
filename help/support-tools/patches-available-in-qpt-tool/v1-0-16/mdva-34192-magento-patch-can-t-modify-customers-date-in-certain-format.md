---
title: "MDVA-34192 Patch: Kann das Kundendatum nicht in einem bestimmten Format ändern"
description: Der Patch MDVA-34192 behebt das Problem, dass es nicht möglich ist, das Geburtsdatum des Kunden im TT/MM/JJJJ-Format zu ändern/anzugeben. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben sein soll.
exl-id: 8aa36970-b2bf-43f8-ba8f-bfc144f8d4ab
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# MDVA-34192 Patch: kann das Kundendatum nicht in einem bestimmten Format ändern

Der Patch MDVA-34192 behebt das Problem, dass es nicht möglich ist, das Geburtsdatum des Kunden im TT/MM/JJJJ-Format zu ändern/anzugeben. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce auf Cloud-Infrastruktur 2.3.5-p1

**Kompatibel mit Adobe Commerce-Versionen:** 2.3.4-2.3.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Patch löst mehrere Probleme. Im Folgenden finden Sie die Beschreibung und die Schritte zum Reproduzieren für eine davon.

Der Produkt-Rasterfilter funktioniert nicht ordnungsgemäß, wenn wir mit dem benutzerdefinierten Datumsattribut filtern und das Gebietsschema des Admin-Benutzers en\_GB lautet.

<u>Zu reproduzierende Schritte:</u>:

1. Erstellen eines Administratorbenutzers, dessen **Gebietsschema der Benutzeroberfläche** auf *Englisch (UK)*.
1. Erstellen Sie ein Datumsattribut mit der folgenden Konfiguration:
   * **Katalogeingabetyp für Store Owner**: *Datum*
   * **Verwenden in Filteroptionen**: *Ja*
   * **Zu Spaltenoptionen hinzufügen**: *Ja*
1. Weisen Sie das Attribut einem Attributsatz zu.
1. Wählen Sie auf der Seite zur Produktbearbeitung ein Datum für das neue Attribut mit der Datumsauswahl aus und speichern Sie es.
1. Versuchen Sie, das Produktraster mit dem neuen Datumsattribut zu filtern.

<u>Erwartetes Ergebnis:</u>:

Der Produktfilter funktioniert für ein benutzerdefiniertes Datumsattribut ordnungsgemäß, wenn das Gebietsschema des Admin-Benutzers en\_GB ist.

<u>Ergebnis:</u>:

Der Produktfilter für ein benutzerdefiniertes Datumsattribut funktioniert nicht ordnungsgemäß, wenn das Gebietsschema des Admin-Benutzers en\_GB ist.

## Wenden Sie den Patch an

Verwenden Sie je nach Adobe Commerce-Produkt die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie im Abschnitt [Im QPT-Tool verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) Abschnitt.
