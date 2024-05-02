---
title: "MDVA-31307: Out of memory on specific categories"
description: Der Patch MDVA-31307 behebt das Problem, dass `Magento\_Csp/Model/BlockCache` viel Speicher verbraucht und enorme zwischengespeicherte Zeichenfolgen generiert, was Probleme für bestimmte Seiten mit vielen dynamisch Whitelisting-Skripten und -Stilen verursacht. Der bereitgestellte Patch optimiert diesen Prozess. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 installiert ist. Die Patch-ID lautet MDVA-31307. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben ist.
exl-id: 15d82f5b-bd43-4a0a-b756-d109dac6d2cd
feature: Cache, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-31307: Nicht genügend Speicher für bestimmte Kategorien

Der Patch MDVA-31307 behebt das Problem, bei dem `Magento\_Csp/Model/BlockCache` verbraucht viel Arbeitsspeicher und erzeugt enorme zwischengespeicherte Zeichenfolgen, was Probleme für bestimmte Seiten mit vielen dynamisch Whitelisting-Skripten und -Stilen verursacht. Der bereitgestellte Patch optimiert diesen Prozess. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 ist installiert. Die Patch-ID lautet MDVA-31307. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben ist.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce auf Cloud-Infrastruktur 2.4.0

**Kompatibel mit Adobe Commerce-Versionen:** Adobe Commerce vor Ort und Adobe Commerce auf Cloud-Infrastruktur 2.4.0 - 2.4.1 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Behebt das Problem, bei dem *Nicht genügend Arbeitsspeicher* Fehler bei bestimmten Kategorien aufgrund von Problemen mit der dynamischen CSP-Whitelisting für zwischengespeicherte Blöcke.

<u>Zu reproduzierende Schritte:</u>

1. Kleinere Profilfixierungen generieren (`bin/magento setup:performance:generate-fixtures`).
1. Öffnen Sie alle Kategorieseiten auf unterschiedlichen Registerkarten.

<u>Ergebnis:</u>

*[Datum und Uhrzeit] PHP Schwerwiegender Fehler: Zulässige Speichergröße von 1073741824 Byte ausgeschöpft (versucht, 90112 Byte zuzuweisen) in Unbekannt in Zeile 0
[Datum und Uhrzeit] PHP Schwerwiegender Fehler: Zulässige Speichergröße von 1073741824 Byte ausgeschöpft (versucht, 33554440 Byte zuzuweisen) in /app/`<project-id>`/vendor/magento/module-csp/Model/Collector/DynamicCollector.php in Zeile 31*

<u>Erwartetes Ergebnis:</u>

Alle Seiten wurden korrekt geöffnet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) Abschnitt.
