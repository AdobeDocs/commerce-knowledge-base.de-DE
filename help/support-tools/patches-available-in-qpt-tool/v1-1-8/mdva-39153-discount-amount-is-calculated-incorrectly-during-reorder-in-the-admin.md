---
title: "MDVA-39153: Rabattbetrag wird bei der Neubestellung in der Admin-Konsole falsch berechnet"
description: Der Patch MDVA-39153 behebt das Problem, dass der Rabattbetrag bei der Neubestellung in der Admin-Konsole falsch berechnet wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 installiert ist. Die Patch-ID lautet MDVA-39153. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
exl-id: d4d11bea-a528-4eb5-8a57-8a7330975e4a
feature: Admin Workspace, Orders, Personalization, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# MDVA-39153: Der Rabattbetrag wird bei der Neubestellung in der Admin-Konsole falsch berechnet

Der Patch MDVA-39153 behebt das Problem, dass der Rabattbetrag bei der Neubestellung in der Admin-Konsole falsch berechnet wird. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 ist installiert. Die Patch-ID lautet MDVA-39153. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Rabattbetrag wird bei der Neuanordnung in der Admin-Konsole falsch berechnet.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zu **Admin** > **Stores** > **Konfiguration** > **Vertrieb** > **Steuern**.
1. Schalten Sie die Steuer für den Versand ein, die die Steuer im Warenkorb anzeigt.
1. Aktivieren und konfigurieren Sie die Versandmethode Tabellenrate ($15).
1. Erstellen Sie eine Steuerregel für den integrierten Steuersatz (für CA).
1. Erstellen Sie eine Preisregel für den Warenkorb mit einem festgelegten Rabatt von 5 USD, der auf den gesamten Warenkorb und den Versandbetrag angewendet wird.
1. Fügen Sie dem Warenkorb ein Produkt mit einem Preis von 12 USD hinzu und rufen Sie die Seite Warenkorb auf.
1. Wenden Sie den Rabatt auf den Warenkorb an.
1. Setzen Sie die Versandmethode im Abschnitt &quot;Schätzungen&quot;auf &quot;Pauschalpreis&quot;.
1. Fahren Sie mit dem Checkout bis zum Review-Schritte fort (platzieren Sie die Bestellung nicht).
1. Gehen Sie zur Homepage und gehen Sie dann zurück zum Warenkorb.
1. Ändern Sie die Versandmethode im Abschnitt &quot;Schätzungen&quot;in &quot;Tabellenrate&quot;.

<u>Erwartete Ergebnisse</u>:

Der Rabatt bleibt gleich - 5 USD.

<u>Tatsächliche Ergebnisse</u>:

Der Rabatt beträgt 6,31 USD.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
