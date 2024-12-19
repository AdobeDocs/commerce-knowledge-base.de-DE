---
title: Versand kann nicht als URL-Schlüssel gespeichert werden
description: Dieser Artikel bietet eine Problemumgehung, wenn Sie den Versand für Produkte oder CMS-Seiten nicht als URL-Schlüssel (_z. B. /shipping_) speichern können. Beim Versuch, den URL-Schlüssel zu speichern, wird eine Fehlermeldung angezeigt, die darauf hinweist, dass es sich bei dem URL-Schlüssel um ein Duplikat einer URL handelt.
exl-id: df19b597-f615-4b19-82c1-59cc179fa720
feature: Marketing Tools, Shipping/Delivery, Storefront
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# _Versand_ kann nicht als URL-Schlüssel gespeichert werden

Dieser Artikel bietet eine Problemumgehung, wenn Sie den Versand für Produkte oder CMS-Seiten nicht als URL-Schlüssel speichern können _z. B. /shipping_. Beim Versuch, den URL-Schlüssel zu speichern, wird eine Fehlermeldung angezeigt, die darauf hinweist, dass es sich bei dem URL-Schlüssel um eine doppelte URL handelt.

## Betroffene Produkte und Versionen

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.x

## Problem

Eine CMS-Seite mit dem Begriff &quot;_&quot;_ URL-Schlüssel kann nicht gespeichert werden.

<u>Schritte zur Reproduktion</u>:

Erstellen Sie eine **[!UICONTROL CMS page]** mit dem URL-Schlüssel _shipping_.

<u>Erwartetes Ergebnis</u>:

Die Seite wird mit _Versand_ als URL-Schlüssel gespeichert.

<u>Tatsächliches </u>:

Speichern nicht möglich, da dieser Fehler auftritt:
*Der im Feld URL-Schlüssel angegebene Wert würde eine bereits vorhandene URL generieren.*

## Ursache

Versand ist ein reserviertes Wort, das in `vendor/magento/module-shipping/etc/frontend/routes.xml` definiert ist.

```xml
<router id="standard">
      <route id="shipping" frontName="shipping">
          <module name="Magento_Shipping" />
      </route>
  </router>
```

## Lösung

Sie können den Begriff _Versand_ in Ihrem URL-Schlüssel nicht verwenden. Sie können jedoch den Begriff _Versand_ in Kombination mit einem anderen Buchstaben oder einer anderen Zahl verwenden (_z. B. shipping1 und shipping2_).

Obwohl der Begriff nicht zwingend _Shipping_+&lt;eine andere Zahl oder ein anderer Buchstabe> sein muss - der Begriff kann eine beliebige Zeichenfolge sein, solange die Länge nicht mehr als *255* Zeichen beträgt.

## Führen Sie die folgenden Schritte aus:

1. Melden Sie sich beim Adobe Commerce Admin an.
1. Navigieren Sie zu **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL URL Rewrites]**.
1. Klicken Sie auf **[!UICONTROL Add URL Rewrite]**.
1. Wählen Sie **[!UICONTROL Custom]** in der Dropdown-Liste **[!UICONTROL Create URL Rewrite]** aus.
   1. Geben Sie den [!UICONTROL Request Path] als **_Shipping_** ein.
   1. Geben Sie im **[!UICONTROL Target Path]** den neuen URL-Schlüssel ein (_. B. „shipping1“_).
   1. Wählen Sie **[!UICONTROL No]** in der Dropdown-Liste **[!UICONTROL Redirect]** aus.


      (**Hinweis**: Der Anfragepfad ist der Pfad, den ein Benutzer im Browser eingibt, und der Zielpfad ist, an den er umgeleitet werden soll.)

Vermeiden Sie außerdem die Verwendung dieser Schlüsselwörter, die als *reservierte* Schlüsselwörter gekennzeichnet sind, wodurch dieselbe Ausnahme auftritt. Wenn Sie eines der unten aufgeführten Keywords als URL-Schlüsselwert verwenden, wird derselbe Fehler angezeigt.


```
"admin"
"adminAnalytics"
"analytics"
"api"
"backup"
"bulk"
"captcha"
"catalog"
"catalogsearch"
"checkout"
"cms"
"contact"
"cookie"
"customer"
"directory"
"downloadable"
"giftmessage"
"groupedProduct"
"indexer"
"instantpurchase"
"loginascustomer"
"marketplace"
"mui"
"multishipping"
"newsletter"
"oauth"
"paypal"
"persistent"
"productalert"
"releaseNotification"
"reports"
"review"
"robots"
"rss"
"sales"
"search"
"security"
"sendfriend"
"shipping"
"stores"
"swagger"
"swatches"
"tax"
"theme"
"translation"
"vault"
"wishlist"
```

## Verwandtes Lesen

* [URL-Neuschreibungen](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/seo/url-rewrites/url-rewrite) in unserem Merchandising- und Promotions-Benutzerhandbuch.
* [Best Practices für SEO](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/seo/seo-overview) in unserem Benutzerhandbuch zu Merchandising und Promotions.
