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

Der Patch ACSD-46988 behebt das Problem, bei dem die GraphQL-Währungs-API-Anfrage Nullwerte für eine benutzerdefinierte Währung zurückgibt. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21 installiert ist. Die Patch-ID lautet ACSD-46988. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die GraphQL-Währungs-API-Anfrage gibt Nullwerte für eine benutzerdefinierte Währung zurück.

<u>Zu reproduzierende Schritte</u>:

1. Konfigurieren Sie die benutzerdefinierte Währung im Admin. Navigieren Sie zu **System** > **Konfiguration** > **Allgemein** > **Währungseinstellungen**.
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

* Adobe Commerce oder Magento Open Source vor Ort: [Tools für Qualitätsmuster > Verwendung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im Handbuch &quot;Qualitätsmuster-Tool&quot;.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Zusätzliche Schritte, die nach der Patch-Installation erforderlich sind

Für On-Premise-Nutzer:

* Ausführen: `composer require symfony/intl:"~5.4.11"`

Für Cloud-Benutzer:

* Ausführen: `composer require symfony/intl:"~5.4.11"`
* Push `composer.json` und `composer.lock` Dateien in das Git-Repository zusammen mit der Patch-Datei.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im Tool-Handbuch für Qualitätsmuster .
