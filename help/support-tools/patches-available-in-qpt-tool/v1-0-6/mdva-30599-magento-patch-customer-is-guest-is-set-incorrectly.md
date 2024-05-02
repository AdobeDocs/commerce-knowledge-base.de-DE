---
title: "MDVA-30599: customer_is_Guest ist falsch eingestellt"
description: Der Patch MDVA-30599 behebt das Problem, dass mit API erstellte Gastangebote fälschlicherweise als Anführungszeichen für angemeldete Kunden markiert werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 installiert ist. Das Problem wurde in Adobe Commerce 2.4.2 behoben.
exl-id: e16bb926-241b-451e-89a5-33000f73c5b7
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# MDVA-30599: customer_is_Guest ist falsch eingestellt

Der Patch MDVA-30599 behebt das Problem, dass mit API erstellte Gastangebote fälschlicherweise als Anführungszeichen für angemeldete Kunden markiert werden. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 installiert ist. Das Problem wurde in Adobe Commerce 2.4.2 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.3.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4 - 2.4.0

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Mit der API erstellte Gastangebote werden fälschlicherweise als Anführungszeichen für angemeldete Kunden markiert.

<u>Zu reproduzierende Schritte</u>:

1. Fügen Sie in der Adobe Commerce-Storefront als Gastbenutzer ein Produkt zum Warenkorb hinzu.
1. Suchen Sie in Ihrer Adobe Commerce-DB die entsprechende `quote_id_mask`.
1. Senden einer API-Anfrage an `quoteGuestCartRepositoryV1` Warenkorb-Repository-Oberfläche für Gastkarts. Dies kann über Swagger oder cURL-Anfrage erfolgen.

```curl
curl -X GET "http://web2-73.sparta.corp.magento.com/dev/support/ee24dev/rest/all/V1/guest-carts/ToOwPtSBxkorkCLq6ztwupPd99y8zhky" -H "accept: application/json"
```

<u>Erwartete Ergebnisse</u>:

Als Antwort erhalten Sie `"customer_is_guest": true`

<u>Tatsächliche Ergebnisse</u>:

Als Antwort erhalten Sie `"customer_is_guest": false`

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Zusätzliche Schritte, die nach der Patch-Installation erforderlich sind

Der Patch wird für alle neuen Gastkarts wirksam sein. Wenn Sie bestehende Warenkorb korrigieren müssen, legen Sie `quote.customer_is_guest = 1` für die Aufzeichnungen, `quote.customer_id` ist NULL. Sie können eine Abfrage ausführen, die der folgenden ähnelt:

```sql
UPDATE quote SET customer_is_guest = 1 WHERE customer_id IS NULL;
```

>[!WARNING]
>
>Es wird dringend empfohlen, die Abfrage in der Staging-/Integrationsumgebung zu testen, bevor sie in der Produktion ausgeführt wird. Es wird außerdem empfohlen, vor allen Manipulationen mit DB eine aktuelle Sicherung zu erstellen.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
