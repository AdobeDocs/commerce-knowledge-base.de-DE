---
title: 'MDVA-33606: Benutzer erhalten beim Speichern von der Hierarchie zugewiesener CMS-Seite einen Fehler.'
description: Der Patch MDVA-33606 behebt das Problem, dass Benutzer beim Speichern einer CMS-Seite, die der Hierarchie zugewiesen ist, den Fehler *Individuelle Einschränkungsverletzung gefunden* erhalten. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.3 installiert ist. Die Patch-ID lautet MDVA-33606. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.
exl-id: cdefece5-6d13-4003-87e9-810c665e940c
feature: CMS
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# MDVA-33606: Benutzer erhalten beim Speichern von der Hierarchie zugewiesener CMS-Seite einen Fehler

Der Patch MDVA-33606 behebt das Problem, bei dem Benutzer beim Speichern einer CMS-Seite, die der Hierarchie zugewiesen ist, den Fehler *Individuelle Einschränkungsverletzung gefunden* erhalten. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.3 installiert ist. Die Patch-ID lautet MDVA-33606. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1-2.4.2-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Beim Versuch, eine CMS-Seite zu speichern, die der Hierarchie zugewiesen ist, erhalten Benutzer die folgende Fehlermeldung: *Verletzung der eindeutigen Beschränkung gefunden*.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine neue CMS-Seite. Stellen Sie den Bereich auf &quot;Alle Store-Ansichten&quot;ein. Dies ist Ihre CMS-Seite 1.
1. Erstellen Sie eine neue Store-Ansicht. Dies ist Ihre Store-Ansicht 2.
1. Navigieren Sie zu **Inhalt** > **Hierarchie** > Fügen Sie die CMS-Seite 1 der Hierarchiestruktur hinzu.
1. Ändern Sie den Umfang in Speicheransicht 2.
   * Deaktivieren Sie &quot;Hierarchie des übergeordneten Knotens verwenden&quot;.
   * Fügen Sie CMS-Seite 1 zu diesem Bereich hinzu und speichern Sie ihn.
1. Ändern Sie jetzt den Umfang in die standardmäßige Store-Ansicht.
   * Deaktivieren Sie &quot;Hierarchie des übergeordneten Knotens verwenden&quot;.
   * Fügen Sie CMS-Seite 1 zu diesem Bereich hinzu und speichern Sie ihn.
1. Gehen Sie zu **Inhalt** > **Seiten** > **Neue Seite hinzufügen**.
   * Geben Sie die Seite als Seite 2 an.
   * Weisen Sie im Abschnitt Seite in Websites alle Store-Ansichten und beide Store-Ansichten (Standard-Store- und Store-Ansicht 2) zu und klicken Sie auf **Seite speichern**.
1. Öffnen Sie auf der CMS-Bearbeitungsseite die Registerkarte Hierarchie .
   * Weisen Sie Seite 2 dem Knoten &quot;Store View 2&quot;den Knoten &quot;Default&quot;und &quot;All Websites&quot;zu.

<u>Erwartete Ergebnisse</u>:

Sie können die CMS-Seite allen drei Knoten ohne Fehler zuweisen.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten den folgenden Fehler: *Die eindeutige Einschränkungsverletzung wurde gefunden*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitätspatches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Überprüfen Sie mithilfe des Qualitätssicherungswerkzeugs](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md), ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) verfügbare Patches.
