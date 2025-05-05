---
title: 'MDVA-41628: Administratoren mit eingeschränkter Zugriffsberechtigung erhalten Zugriff auf neue Ressourcen'
description: Mit dem Patch MDVA-41628 wird das Problem behoben, dass Administratoren mit eingeschränkten Berechtigungen auf die neuen Ressourcen zugreifen können, wenn neue Module hinzugefügt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-41628. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
exl-id: 8f63ce9d-07b6-4d9d-a51b-b85b783b2adf
feature: Admin Workspace
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# MDVA-41628: Administratoren mit eingeschränkter Zugriffsberechtigung erhalten Zugriff auf neue Ressourcen

Mit dem Patch MDVA-41628 wird das Problem behoben, dass Administratoren mit eingeschränkten Berechtigungen auf die neuen Ressourcen zugreifen können, wenn neue Module hinzugefügt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-41628. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Administratoren mit beschränkten Zugangsrechten können auf die neuen Ressourcen zugreifen, wenn neue Module hinzugefügt werden.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine neue Administratorrolle mit eingeschränkten Ressourcen.
1. Erstellen Sie unter der in Schritt 1 erstellten Rolle einen neuen Admin-Benutzer.
1. Installieren und aktivieren Sie das benutzerdefinierte Modul , das einen neuen Satz von Menüelementen zusammen mit ACL-Ressourcen erstellt.
1. Melden Sie sich mit dem neu erstellten Admin-Benutzer an.

<u>Erwartete Ergebnisse</u>:

Der Admin-Benutzer mit eingeschränktem Zugriff kann nicht auf die neu erstellten Menüelemente zugreifen.

<u>Tatsächliche Ergebnisse</u>:

Der eingeschränkte Admin-Benutzer kann auf die neuen Menüelemente zugreifen, auch wenn die neuen Ressourcen nicht der Benutzerrolle zugewiesen sind.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) in unserer Entwicklerdokumentation.
