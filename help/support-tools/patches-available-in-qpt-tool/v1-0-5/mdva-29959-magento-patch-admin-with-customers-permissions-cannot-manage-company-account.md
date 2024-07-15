---
title: 'Patch "MDVA-29959: Administrator mit "Kunden"-Berechtigungen kann Unternehmenskonto nicht verwalten"'
description: Der im [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)-Tool Version 1.0.5 verfügbare Patch MDVA-29959 behebt das Problem, dass ein eingeschränkter Administrator mit allen Berechtigungen für "Customer"-ACL Unternehmen nicht verwalten kann (Hinzufügen oder Löschen eines Unternehmens). Bitte beachten Sie, dass das Problem in B2B für Adobe Commerce 2.3.4 behoben ist.
exl-id: ee246380-d37e-4c24-8435-97ae80088227
feature: Admin Workspace, B2B, Companies, Roles/Permissions
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# Patch MDVA-29959: Administrator mit &quot;Kunden&quot;-Berechtigungen kann Unternehmenskonten nicht verwalten

Der Patch MDVA-29959, der im Tool [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) Version 1.0.5 verfügbar ist, behebt das Problem, dass ein eingeschränkter Admin-Benutzer mit allen Berechtigungen für &quot;Customer&quot;ACL Unternehmen nicht verwalten kann (Hinzufügen oder Löschen eines Unternehmens). Bitte beachten Sie, dass das Problem in B2B für Adobe Commerce 2.3.4 behoben ist.

## Betroffene Produkte und Versionen

B2B für Adobe Commerce auf Cloud-Infrastruktur 2.3.0-2.3.3-p1.

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Admin-Benutzer mit allen Berechtigungen für &quot;Kunden&quot;-ACL können Unternehmen nicht verwalten (Unternehmen hinzufügen oder löschen).

<u>Zu reproduzierende Schritte</u>

1. Erstellen Sie in Commerce Admin eine neue Administratorrolle und weisen Sie dieser Rolle einen Benutzer zu.
1. Weisen Sie der Rolle nur &quot;Kunden&quot;-Ressourcen zu.
1. Melden Sie sich als Benutzer mit dieser Rolle an.
1. Versuchen Sie, ein Unternehmenskonto zu löschen.

<u>Erwartetes Ergebnis:</u>

Das Unternehmenskonto wurde erfolgreich gelöscht.

<u>Tatsächliches Ergebnis:</u>

Sie können das Unternehmenskonto nicht löschen. Sie erhalten die *Entschuldigung, Sie benötigen Berechtigungen zum Anzeigen dieses Inhalts.* -Fehlermeldung.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
