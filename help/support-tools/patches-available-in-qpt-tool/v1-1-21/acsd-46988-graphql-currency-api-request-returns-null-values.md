---
title: 'ACSD-46988: GraphQL-Währungs-API-Anfrage gibt Nullwerte zurück.'
description: Der Patch ACSD-46988 behebt das Problem, bei dem die GraphQL-Währungs-API-Anfrage Nullwerte für eine benutzerdefinierte Währung zurückgibt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21 installiert ist. Die Patch-ID lautet ACSD-46988. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.
exl-id: 8da0ab99-8db9-4222-9400-6df1520267f0
feature: REST, GraphQL
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-46988: GraphQL-Währungs-API-Anfrage gibt Nullwerte zurück

Der Patch ACSD-46988 behebt das Problem, bei dem die GraphQL-Währungs-API-Anfrage Nullwerte für eine benutzerdefinierte Währung zurückgibt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21 installiert ist. Die Patch-ID lautet ACSD-46988. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die GraphQL-Währungs-API-Anfrage gibt Nullwerte für eine benutzerdefinierte Währung zurück.

<u>Zu reproduzierende Schritte</u>:

1. Konfigurieren Sie die benutzerdefinierte Währung im Admin. Wechseln Sie zu **System** > **Konfiguration** > **Allgemein** > **Währungseinstellungen**.
1. Senden Sie eine GraphQL-Anfrage mit der folgenden Payload:

<pre>
<code class="language-graphql">
{
    currency {
        base_currency_code
        base_currency_symbol
        default_display_currency_code
        default_display_currency_symbol
        available_currency_codes
        exchange_rates {
            currency_to
            rate
        }
    }
}
</code>
</pre>

<u>Erwartete Ergebnisse</u>:

Die Anfrage gibt Währungswerte anstelle von Nullwerten zurück.

<u>Tatsächliche Ergebnisse</u>:

Die Anfrage gibt mehrere Nullwerte zurück.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Tools für Qualitätsmuster > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im Handbuch zum Werkzeug für Qualitätsmuster.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Zusätzliche Schritte, die nach der Patch-Installation erforderlich sind

Für On-Premise-Nutzer:

* Ausführen: `composer require symfony/intl:"~5.4.11"`

Für Cloud-Benutzer:

* Ausführen: `composer require symfony/intl:"~5.4.11"`
* Push `composer.json` - und `composer.lock` -Dateien zusammen mit der Patch-Datei in das Git-Repository.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im Handbuch zum Werkzeug für Qualitätsmuster .
