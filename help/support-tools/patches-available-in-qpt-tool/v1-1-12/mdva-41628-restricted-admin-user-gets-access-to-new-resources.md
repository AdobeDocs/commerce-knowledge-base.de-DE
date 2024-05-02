---
title: "MDVA-41628: Eingeschränkte Administratoren erhalten Zugriff auf neue Ressourcen"
description: Der Patch MDVA-41628 behebt das Problem, dass die eingeschränkten Admin-Benutzer auf die neuen Ressourcen zugreifen können, wenn neue Module hinzugefügt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-41628. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: 8f63ce9d-07b6-4d9d-a51b-b85b783b2adf
feature: Admin Workspace
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# MDVA-41628: Eingeschränkte Administratoren erhalten Zugriff auf neue Ressourcen

Der Patch MDVA-41628 behebt das Problem, dass die eingeschränkten Admin-Benutzer auf die neuen Ressourcen zugreifen können, wenn neue Module hinzugefügt werden. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-41628. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.3 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Eingeschränkte Admin-Benutzer können Zugriff auf die neuen Ressourcen erhalten, wenn neue Module hinzugefügt werden.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine neue Administratorrolle mit eingeschränkten Ressourcen.
1. Erstellen Sie einen neuen Admin-Benutzer unter der in Schritt 1 erstellten Rolle.
1. Installieren und aktivieren Sie das benutzerdefinierte Modul, das einen neuen Satz von Menüelementen sowie ACL-Ressourcen erstellt.
1. Melden Sie sich mit dem neu erstellten Admin-Benutzer an.

<u>Erwartete Ergebnisse</u>:

Der Administrator-Benutzer mit eingeschränktem Zugriff kann nicht auf die neu erstellten Menüelemente zugreifen.

<u>Tatsächliche Ergebnisse</u>:

Der eingeschränkte Administrator kann auf die neuen Menüelemente zugreifen, auch wenn die neuen Ressourcen nicht der Benutzerrolle zugewiesen sind.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
