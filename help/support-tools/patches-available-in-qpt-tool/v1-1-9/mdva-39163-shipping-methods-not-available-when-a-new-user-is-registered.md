---
title: "MDVA-39163: Versandmethoden nicht für neu registrierte Benutzer mit Produkten aus Gastsitzungen verfügbar"
description: Der Patch MDVA-39163 behebt das Problem, dass die Versandmethoden nicht verfügbar sind, wenn ein neuer Benutzer registriert wird und Produkte aus der Gastsitzung stammen. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-39163. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: f8661a4e-5832-41bb-be3d-4ea6c863fdb9
feature: CMS, Marketing Tools, Orders, Products, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# MDVA-39163: Versandmethoden für neu registrierte Benutzer mit Produkten aus Gastsitzungen nicht verfügbar

Der Patch MDVA-39163 behebt das Problem, dass die Versandmethoden nicht verfügbar sind, wenn ein neuer Benutzer registriert wird und Produkte aus der Gastsitzung stammen. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 ist installiert. Die Patch-ID lautet MDVA-39163. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.5 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Versandmethoden sind nicht verfügbar, wenn der neue Benutzer registriert wird und Produkte im Warenkorb aus der Gastsitzung stammen.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zu **Admin** > **Stores** > **Konfiguration** > **Vertrieb** > **Versandmethoden**. Nur aktivieren **Pauschalsatz** Versandmethode und deaktivieren Sie alles andere.
1. Im **Pauschalsatz** Versandmethode, wählen Sie die **spezifisch** Länderoption verfügbar in **Schiff in die betreffenden Länder** ein Land aus der Liste auswählen (z. B. USA).
1. Navigieren Sie zu **Admin** > **Stores** > **Konfiguration** > **Kunde** > **Kundenkonfiguration** und **E-Mail-Bestätigung anfordern** nach _Ja_.
1. Erstellen Sie eine neue E-Mail-Vorlage in **Admin** > **Marketing** > **E-Mail-Vorlagen** und Laden `Footer (magento/luma)` und ersetzen Sie den Vorlageninhalt durch einen CMS-Block.

   ```CMS
   {{block class="Magento\Cms\Block\Block" block_id="footer_links_block"}}
   ```

1. Navigieren Sie zu **Admin** > **Inhalt** > **Design** > **Konfiguration** und wählen Sie das Thema aus, das sich auf Ihre Frontend-Website bezieht. Wählen Sie für die Fußzeilenvorlage die neu erstellte E-Mail-Vorlage aus.
1. Gehen Sie zum Frontend und fügen Sie dem Warenkorb ein Produkt hinzu.
1. Erstellen Sie einen Kunden. Sie erhalten eine E-Mail, um die E-Mail-Adresse zu bestätigen. Klicken Sie auf den Verifizierungslink. Sie werden auf der Webseite angemeldet.
1. Navigieren Sie zu **Mein Konto** und eine Adresse hinzufügen. Legen Sie das Adressland auf das Versandland fest, das Sie zuvor in der Admin-Konfiguration festgelegt haben.
1. Gehen Sie zum Checkout.

<u>Erwartete Ergebnisse</u>:

Versandmethode ist verfügbar, da der Kunde eine Adresse hat, die mit dem Versandland kompatibel ist.

<u>Tatsächliche Ergebnisse</u>:

Die Versandmethode ist nicht verfügbar.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
