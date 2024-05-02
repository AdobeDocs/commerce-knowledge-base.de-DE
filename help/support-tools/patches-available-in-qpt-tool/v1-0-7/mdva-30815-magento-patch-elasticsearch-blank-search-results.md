---
title: "MDVA-30815: Elasticsearch blank Search results"
description: Der Patch MDVA-30815 behebt das Problem, dass Elasticsearch eine leere Seite anzeigt, wenn die Begrenzungsoptionen der Suchergebnisse geändert werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.3.5 behoben wurde.
exl-id: dbe41a43-e248-407e-8cf9-319ad5843935
feature: Search, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# MDVA-30815: Elasticsearch für leere Suchergebnisse

Der Patch MDVA-30815 behebt das Problem, dass Elasticsearch eine leere Seite anzeigt, wenn die Begrenzungsoptionen der Suchergebnisse geändert werden. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 ist installiert. Beachten Sie, dass das Problem in Adobe Commerce 2.3.5 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce auf Cloud-Infrastruktur 2.3.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.2 - 2.3.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn Sie Elasticsearch verwenden und die Begrenzungsoptionen der Suchergebnisse ändern, zeigt Adobe Commerce eine leere Seite an.

<u>Voraussetzungen</u>:

Elasticsearch ist **enabled**. Navigieren Sie zu **SPEICHER** > **Einstellungen** > **Konfiguration** > **Katalog** > **Katalogsuche**.

<u>Zu reproduzierende Schritte</u>:

1. Rufen Sie Ihre Site auf.
1. Suchen Sie im Hauptsuchfeld nach einem Produkt.
1. Nachdem die Suchergebnisseiten angezeigt wurden, klicken Sie auf die letzte Seite der Suchergebnisseiten.
1. Auswählen **xx pro Seite anzeigen** aus der Begrenzeroption. Stellen Sie sicher, dass dies eine andere Begrenzung für die Suchergebnisnummer ist als derzeit konfiguriert.

<u>Erwartete Ergebnisse</u>:

Auf der Seite wird die konfigurierte Anzahl der Produktergebnisse angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Es wird eine leere Seite angezeigt. Dieser Fehler wird auch im `var/report` : *\`&quot;0&quot;:&quot;SQLSTATE\[42000\]: Syntaxfehler oder Zugriffsverletzung: 1064 Sie haben einen Fehler in Ihrer SQL-Syntax. Überprüfen Sie das Handbuch, das Ihrer MySQL-Serverversion entspricht, auf die richtige Syntax, um &quot;nähere&quot;zu verwenden.*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
