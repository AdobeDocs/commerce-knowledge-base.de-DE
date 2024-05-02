---
title: "MDVA-39986: Bestellungen können nicht in der Admin-Konsole im Safari-Browser auf macOS platziert werden"
description: Der Patch MDVA-39986 behebt das Problem, dass Benutzer keine Bestellungen über den Safari-Browser in macOS im Admin aufgeben können. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-39986. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.
exl-id: a35b6253-e03f-4bdb-a3a3-fceb70588c6e
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# MDVA-39986: Bestellungen können nicht in der Admin-Konsole des Safari-Browsers in macOS platziert werden

Der Patch MDVA-39986 behebt das Problem, dass Benutzer keine Bestellungen über den Safari-Browser in macOS im Admin aufgeben können. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.2 ist installiert. Die Patch-ID lautet MDVA-39986. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1 - 2.4.2-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Benutzer können über den Safari-Browser in macOS keine Bestellungen im Admin aufgeben.

<u>Zu reproduzierende Schritte</u>:

1. Bestellung aufgeben.
1. Navigieren Sie mit dem Safari-Browser in macOS zum Administrator und öffnen Sie die zuvor erstellte Bestellung.
1. Klicken Sie auf **Neu anordnen**.
1. Versuchen Sie zu aktualisieren **Produktmenge**.

<u>Erwartete Ergebnisse</u>:

Benutzer sollten in der Lage sein, mit dem Safari-Browser in macOS eine neue Bestellung durchzuführen.

<u>Tatsächliche Ergebnisse</u>:

Benutzer erhalten einen JS-Fehler, bei dem das Rotationsrad angezeigt und endlos ausgeführt wird.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
