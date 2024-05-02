---
title: "MDVA-30107: Store-Umschalter funktioniert nicht erwartungsgemäß"
description: Der MDVA-30107-Patch behebt das Problem, dass der Store-Switch nicht wie erwartet funktioniert, wenn verschiedene Basis-URLs für Store-Ansichten verwendet werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 installiert ist.
exl-id: feaef9ed-615f-4a0a-a7c5-1833f993d27f
feature: Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# MDVA-30107: Store-Umschalter funktioniert nicht erwartungsgemäß

Der MDVA-30107-Patch behebt das Problem, dass der Store-Switch nicht wie erwartet funktioniert, wenn verschiedene Basis-URLs für Store-Ansichten verwendet werden. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 ist installiert.

## Betroffene Produkte und Versionen

* Adobe Commerce vor Ort 2.3.0 - 2.3.5.x
* Adobe Commerce auf Cloud-Infrastruktur 2.3.0 - 2.3.5.x

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn ein Benutzer mithilfe des Store-Switchers zwischen Stores wechselt, schlägt die Anfrage fehl, wenn der Ziel-Store über eine andere Basis-URL verfügt.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie zwei oder mehr Stores mit unterschiedlichen Basis-URLs.
1. Gehen Sie auf eine Kategorieseite auf einer Storefront eines dieser Stores.
1. Versuchen Sie, mit dem Store-Umschalter zum anderen Store zu wechseln.

<u>Erwartete Ergebnisse</u>:

Sie werden zu einer ähnlichen Seite des anderen Stores umgeleitet.

<u>Tatsächliche Ergebnisse</u>:

Sie werden zur Homepage des gleichen Stores weitergeleitet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
