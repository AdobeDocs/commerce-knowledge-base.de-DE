---
title: "MDVA-32012 Patch: S. Korean and Argentina zip codes validation"
description: Der Patch MDVA-32012 behebt das Problem, dass argentinische und südkoreanische Postleitzahlen aufgrund von Änderungen oder Abweichungen in den nationalen Postleitzahlformaten nicht validiert werden. Südkoreanische Postleitzahlen müssen jetzt 5-stellig sein, während sie früher 6-stellig waren. Argentinische Postleitzahlen können numerisch und alphanumerisch sein. Der Patch MDVA-32012 bedeutet, dass diese Formate für Postleitzahlwerte für diese Länder validiert werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.2 behoben sein soll.
exl-id: 9602f50d-6acd-4724-9734-6aeb65393a25
feature: Communications
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---

# MDVA-32012 Patch: S. Korean and Argentina zip codes validation

Der Patch MDVA-32012 behebt das Problem, dass argentinische und südkoreanische Postleitzahlen aufgrund von Änderungen oder Abweichungen in den nationalen Postleitzahlformaten nicht validiert werden. Südkoreanische Postleitzahlen müssen jetzt 5-stellig sein, während sie früher 6-stellig waren. Argentinische Postleitzahlen können numerisch und alphanumerisch sein. Der Patch MDVA-32012 bedeutet, dass diese Formate für Postleitzahlwerte für diese Länder validiert werden. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 ist installiert. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.2 behoben sein soll.

## Betroffene Produkte und Versionen

* Der Patch wurde für Adobe Commerce in der Cloud-Infrastruktur 2.3.5 entwickelt.
* Der Patch ist auch mit den folgenden Adobe Commerce-Versionen kompatibel: Adobe Commerce für Cloud-Infrastruktur und Adobe Commerce On-Premise 2.3.0 - 2.4.1.

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn Sie eine 5-stellige südkoreanische oder alphanumerische argentinische Postleitzahl eingeben, wird eine Warnung ausgegeben:

*Die angegebene Postleitzahl scheint ungültig zu sein. Beispiel: [1234 (bei alphanumerischer argentinischer Adresse)] oder [123-456 (bei Angabe einer 5-stelligen südkoreanischen Adresse)]. Wenn du glaubst, dass es der Richtige ist, kannst du diesen Hinweis ignorieren.*

<u>Zu reproduzierende Schritte</u>:

1. Öffnen Sie die Storefront.
1. Artikel zum Warenkorb hinzufügen.
1. Prozess zum Checkout.
1. Fügen Sie eine neue Adresse mit Südkorea für das Land hinzu und geben Sie eine 5-stellige Postleitzahl ein oder fügen Sie eine neue Adresse mit Argentinien für das Land hinzu und geben Sie eine alphanumerische Postleitzahl ein.
1. Versuchen Sie zu speichern.

<u>Erwartete Ergebnisse</u>:

Die Adresse sollte ohne Warnung gespeichert werden.

<u>Tatsächliche Ergebnisse</u>:

Beim Speichern einer Adresse wird eine Warnung zurückgegeben.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
