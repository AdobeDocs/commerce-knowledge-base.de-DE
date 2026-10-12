---
title: '*Kontakt* kann nicht als URL-Schlüssel gespeichert werden'
description: Dieser Artikel bietet eine Problemumgehung, wenn Sie *Kontakt* nicht als URL-Schlüssel (z. B. "/contact„) für Produkte oder CMS-Seiten speichern können. Beim Versuch, den URL-Schlüssel zu speichern, wird eine Fehlermeldung angezeigt, die darauf hinweist, dass es sich bei dem URL-Schlüssel um eine doppelte URL handelt.
exl-id: eb340813-aba5-43a4-af5d-8fb64c93e021
feature: CMS, Marketing Tools, Storefront
role: Admin
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: ddbd0f6e-b569-5a04-8a70-55058777c373
    internal-label: CMS
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%
---
# &lbrace;*&rbrace; kann nicht* URL-Schlüssel gespeichert werden

Dieser Artikel bietet eine Problemumgehung, wenn Sie *Kontakt“ nicht als* (z. B. &quot;/contact„) für Produkte oder CMS-Seiten speichern können.

## Betroffene Produkte und Versionen

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.x

## Problem

Sie können ein Produkt oder eine CMS-Seite nicht mit dem Begriff *Kontakt* als URL-Schlüssel speichern. Beim Versuch, den URL-Schlüssel zu speichern, wird eine Fehlermeldung angezeigt, die darauf hinweist, dass es sich bei dem URL-Schlüssel um eine doppelte URL handelt.

<u>Schritte zur Reproduktion</u>:

Erstellen Sie eine CMS-Seite mit *Kontakt* als URL-Schlüssel.

<u>Erwartetes Ergebnis</u>:

Die Seite wird mit &quot;*&quot;* URL-Schlüssel gespeichert.

<u>Tatsächliches </u>:

Sie können die Seite nicht speichern. Sie erhalten die folgende Fehlermeldung: *Der im Feld URL-Schlüssel angegebene Wert würde eine bereits vorhandene URL generieren.*

## Ursache

*Kontakt* ist ein reserviertes Wort, das in `vendor/magento/module-contact/view/frontend/layout/contact_index_index.xml` definiert ist.

```xml
<router id="standard">
      <route id="contact" frontName="contact">
          <module name="Magento_Contact" />
      </route>
  </router>
```

## Lösung

Sie können den Begriff *Kontakt* nicht als URL-Schlüssel verwenden. Sie können jedoch den Begriff *Kontakt* in Kombination mit einem anderen Buchstaben oder einer anderen Nummer verwenden (z. B. *contact1* und *contact2*). Obwohl der Begriff nicht unbedingt *Kontakt+\&lt;eine andere Zahl oder ein anderer Buchstabe\>* sein muss, kann der Begriff eine beliebige Zeichenfolge sein, solange die Länge 255 Zeichen nicht überschreitet.

Führen Sie die folgenden Schritte aus:

1. Anmelden bei Commerce Admin.
1. Navigieren Sie zu **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL URL Rewrites]**.
1. Klicken Sie auf **[!UICONTROL Add URL Rewrite]**.
1. Wählen Sie *[!UICONTROL Custom]* in der Dropdown-Liste [!UICONTROL Create URL Rewrite] aus.
   1. Geben Sie in der [!UICONTROL Request Path] „Kontakt“ ein. Beachten Sie, dass der [!UICONTROL Request Path] von einem Benutzer im Browser eingegeben wird und der [!UICONTROL Target Path] ist, zu dem er umgeleitet werden soll.
   1. Geben Sie im [!UICONTROL Target Path] den neuen URL-Schlüssel ein (z. B. „contact1„).
   1. Wählen Sie *[!UICONTROL No]* in der Dropdown-Liste [!UICONTROL Redirect] aus.

## Verwandtes Lesen

* [URL-Neuschreibungen](https://experienceleague.adobe.com/de/docs/commerce-admin/marketing/seo/url-rewrites/url-rewrite) in unserem Benutzerhandbuch.
* [SEO Best Practices](https://experienceleague.adobe.com/de/docs/commerce-admin/marketing/seo/seo-overview) in unserem Benutzerhandbuch.
