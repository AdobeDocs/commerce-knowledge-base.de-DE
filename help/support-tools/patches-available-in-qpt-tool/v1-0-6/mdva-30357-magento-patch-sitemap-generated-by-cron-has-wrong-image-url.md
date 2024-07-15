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

Der Patch MDVA-30357 behebt das Problem mit der falschen Bild-URL, die von einer durch Cron generierten Sitemap in der Commerce Admin erstellt wurde. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.

## Betroffene Produkte und Versionen

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.2 bis 2.4.0

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Von Cron in Adobe Commerce generierte Sitemaps enthalten den falschen Bild-URL-Pfad.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie in Commerce Admin eine neue Website-, Store- oder Store-Ansicht.
1. Fügen Sie jedem Store mindestens ein Produkt hinzu und fügen Sie jedem Produkt mindestens ein Bild hinzu.
1. Aktivieren Sie die **Sitemap-Erstellung nach Zeitplan** in **Admin** > **Stores** > **Konfiguration** > **KATALOG** > **XML-Sitemap** > **Erstellungseinstellungen**.
1. Generieren Sie eine Sitemap für einen der beiden Stores manuell in &quot;**Admin** > **Marketing** > **Site Map**&quot;mithilfe eines Sitemap-Namens wie &quot;*sitemap.xml*&quot;.
   * Benennen Sie die Datei in einen Pfad wie &quot;*manual\_sitemap.xml*&quot;um oder kopieren Sie den Dateiinhalt in einen beliebigen Texteditor.
1. Erstellen Sie dieselbe Sitemap durch Cron-Auftrag `sitemap_generate`.
1. Vergleichen Sie die manuell generierte Sitemap &quot;*manual\_sitemap.xml*&quot;mit der Sitemap, die von cron &quot;*sitemap.xml*&quot; generiert wurde.

<u>Erwartete Ergebnisse</u>:

Die URL des zwischengespeicherten Sitemap-Bildpfads ist korrekt.

<u>Tatsächliche Ergebnisse</u>:

Die von Cron generierte Sitemap enthält die falsche BildpfadURL. Wenn Sie versuchen, das Bild aus &quot;*sitemap.xml*&quot;zu öffnen, wird ein standardmäßiger Platzhalter angezeigt. Manuell generierte Sitemap-URLs sind von diesem Problem nicht betroffen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.

Weitere Informationen zu Sitemaps finden Sie in diesen Artikeln in unserer Entwicklerdokumentation:

* [Hinzufügen von Sitemap- und Suchmaschinen-Robotern](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html)
* [cron konfigurieren und ausführen](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html)
* [Sichere cron.php für die Ausführung in einem Browser](https://devdocs.magento.com/guides/v2.4/config-guide/secy/secy-cron.html)
