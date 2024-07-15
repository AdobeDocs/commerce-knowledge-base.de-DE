---
title: "MDVA-28661: Problem mit der Benutzerverwaltung im Unternehmen beim Ändern der Admin-E-Mail"
description: Der Patch MDVA-28861 behebt das Problem, dass Benutzer beim Ändern der Admin-E-Mail einen Fehler erhalten. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 installiert ist. Die Patch-ID lautet MDVA-28861.
exl-id: 2d6691e5-baaf-4cef-ae7e-2b6ccc7f2cd3
feature: Admin Workspace, Communications, Companies
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# MDVA-28661: Problem mit der Verwaltung von Unternehmensbenutzern beim Ändern der Admin-E-Mail

Der Patch MDVA-28861 behebt das Problem, dass Benutzer beim Ändern der Admin-E-Mail einen Fehler erhalten. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 installiert ist. Die Patch-ID lautet MDVA-28861.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce lokal und Adobe Commerce auf Cloud-Infrastruktur 2.3.0 bis 2.4.1 (einschließlich 2.3.5-p1) mit B2B-Erweiterung

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Nach Änderung der E-Mail-Adresse **Unternehmensadministrator** wird ein Fehler zurückgegeben und die Liste **Unternehmensbenutzer** wird nicht angezeigt.

<u>Zu reproduzierende Schritte</u>:

1. Aktiviert die Funktion &quot;Unternehmen&quot;(Weitere Informationen dazu finden Sie in der Entwicklerdokumentation unter [B2B installieren: Aktivieren Sie B2B-Funktionen in Commerce Admin](https://devdocs.magento.com/extensions/b2b/#enable-b2b-features-in-magento-admin) und erstellen Sie ein neues Unternehmen mit zwei Benutzern - einem Administrator und zwei Benutzern -, die alle E-Mail-Adressen enthalten).
1. Gehen Sie zu **Commerce Admin** > **Customers** > **Unternehmen** und öffnen Sie Ihr Unternehmenskonto.
1. Öffnen Sie die Registerkarte **Unternehmensadministrator** und ändern Sie den Administrator in den ersten Benutzer, wozu auch gehört, die E-Mail-Adresse **Unternehmensadministrator** in die E-Mail des ersten Benutzers zu ändern.
1. Gehen Sie zum Adobe Commerce-Frontend und melden Sie sich als erster Benutzer an.
1. Wechseln Sie zum Abschnitt **Firmenbenutzer** .

<u>Erwartete Ergebnisse</u>:

Die Liste **Firmenbenutzer** sollte erwartungsgemäß angezeigt werden.

<u>Tatsächliche Ergebnisse</u>:

Die Liste **Firmenbenutzer** wird nicht angezeigt und es wird ein Fehler ähnlich dem folgenden angezeigt:

```bash
No such entity with id = 2
```

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.

Weitere Informationen zur Funktionalität von B2B Company finden Sie in diesen Artikeln in unserer Entwicklerdokumentation:

* [B2B-Entwicklerhandbuch](https://devdocs.magento.com/guides/v2.4/b2b/bk-b2b.html)
* [Verwalten von Unternehmensrollen](https://devdocs.magento.com/guides/v2.4/b2b/roles.html)
* [Adobe Commerce Enterprise B2B Extension configuration paths reference](https://devdocs.magento.com/guides/v2.4/config-guide/prod/config-reference-b2b.html)
