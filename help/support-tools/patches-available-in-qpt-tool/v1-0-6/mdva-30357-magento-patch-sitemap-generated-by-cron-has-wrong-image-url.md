---
title: "MDVA-30357: von Cron generierte Sitemap hat falsche Bild-URL"
description: Der Patch MDVA-30357 behebt das Problem mit der falschen Bild-URL, die von einer durch Cron generierten Sitemap in der Commerce Admin erstellt wurde. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.
exl-id: c91f7ae0-0970-4918-9d1f-4ede6bfcb05f
feature: Marketing Tools
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 0%

---

# MDVA-30357: von Cron generierte Sitemap hat falsche Bild-URL

Der Patch MDVA-30357 behebt das Problem mit der falschen Bild-URL, die von einer durch Cron generierten Sitemap in der Commerce Admin erstellt wurde. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.

## Betroffene Produkte und Versionen

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.2 bis 2.4.0

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Von Cron in Adobe Commerce generierte Sitemaps enthalten den falschen Bild-URL-Pfad.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie in Commerce Admin eine neue Website-, Store- oder Store-Ansicht.
1. Fügen Sie jedem Store mindestens ein Produkt hinzu und fügen Sie jedem Produkt mindestens ein Bild hinzu.
1. Aktivieren **Sitemap-Erstellung nach Zeitplan** in **Admin** > **Stores** > **Konfiguration** > **KATALOG** > **XML-Sitemap** > **Generierungseinstellungen**.
1. Erstellen Sie eine Sitemap für einen der beiden Stores manuell in **Admin** > **Marketing** > **Site-Map** mit einem Sitemap-Namen wie &quot;*sitemap.xml*&quot;.
   * Benennen Sie die Datei in einen der folgenden Werte um:*manual\_sitemap.xml*&quot; oder kopieren Sie den Dateiinhalt in einen beliebigen Texteditor.
1. Erstellen derselben Sitemap durch Cron-Auftrag `sitemap_generate`.
1. Vergleich der manuell generierten Sitemap &quot;*manual\_sitemap.xml* und die von Cron generierte Sitemap *sitemap.xml*&quot;.

<u>Erwartete Ergebnisse</u>:

Die URL des zwischengespeicherten Sitemap-Bildpfads ist korrekt.

<u>Tatsächliche Ergebnisse</u>:

Die von Cron generierte Sitemap enthält die falsche BildpfadURL. Wenn Sie versuchen, das Bild über zu öffnen *sitemap.xml*&quot;, wird ein standardmäßiger Platzhalter angezeigt. Manuell generierte Sitemap-URLs sind von diesem Problem nicht betroffen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.

Weitere Informationen zu Sitemaps finden Sie in diesen Artikeln in unserer Entwicklerdokumentation:

* [Sitemap- und Suchmaschinen-Roboter hinzufügen](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html)
* [Cron konfigurieren und ausführen](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html)
* [Sichere cron.php für die Ausführung im Browser](https://devdocs.magento.com/guides/v2.4/config-guide/secy/secy-cron.html)
