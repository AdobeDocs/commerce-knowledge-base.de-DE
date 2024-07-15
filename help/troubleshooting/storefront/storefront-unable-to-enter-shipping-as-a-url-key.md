---
title: Versandzeitpunkt als URL-Schlüssel nicht speichern
description: Dieser Artikel bietet eine Problemumgehung, wenn Sie den Versand nicht als URL-Schlüssel (_z. B. /shipping_) für Produkte oder CMS-Seiten speichern können. Wenn Sie versuchen, den URL-Schlüssel zu speichern, erhalten Sie eine Fehlermeldung, die anzeigt, dass der URL-Schlüssel eine doppelte URL ist.
exl-id: df19b597-f615-4b19-82c1-59cc179fa720
feature: Marketing Tools, Shipping/Delivery, Storefront
role: Admin
source-git-commit: 1ce963142a261a17e2b42f79dd567c8484ec5b3e
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# _shipping_ kann nicht als URL-Schlüssel gespeichert werden

Dieser Artikel bietet eine Problemumgehung, wenn Sie den Versand nicht als URL-Schlüssel (_z. B. /shipping_) für Produkte oder CMS-Seiten speichern können. Wenn Sie versuchen, den URL-Schlüssel zu speichern, erhalten Sie einen Fehler, der anzeigt, dass der URL-Schlüssel eine doppelte URL ist.

## Betroffene Produkte und Versionen

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.x

## Problem

Sie können keine CMS-Seite mit dem Begriff _shipping_ im URL-Schlüssel speichern.

<u>Zu reproduzierende Schritte</u>:

Erstellen Sie eine **[!UICONTROL CMS page]** mit dem URL-Schlüssel _shipping_ .

<u>Erwartetes Ergebnis</u>:

Die Seite wird mit _shipping_ als URL-Schlüssel gespeichert.

<u>Tatsächliches Ergebnis</u>:

Sie können nicht speichern, da dieser Fehler auftritt:
*Der im Feld &quot;URL-Schlüssel&quot;angegebene Wert generiert eine bereits vorhandene URL.*

## Ursache

Der Versand ist ein reserviertes Wort, das in `vendor/magento/module-shipping/etc/frontend/routes.xml` definiert ist.

```xml
<router id="standard">
      <route id="shipping" frontName="shipping">
          <module name="Magento_Shipping" />
      </route>
  </router>
```

## Lösung

Sie können den Begriff _shipping_ nicht in Ihrem URL-Schlüssel verwenden. Sie können jedoch den Begriff _shipping_ in Kombination mit einem anderen Brief oder einer anderen Nummer (_z. B. shipping1 und shipping2_) verwenden.

Obwohl der Begriff nicht _shipping_+&lt;another number or letter> lauten muss, kann der Begriff eine beliebige Zeichenfolge sein, solange die Länge nicht mehr als *255* Zeichen beträgt.

## Führen Sie die folgenden Schritte aus:

1. Melden Sie sich bei Adobe Commerce Admin an.
1. Gehen Sie zu **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL URL Rewrites]**.
1. Klicken Sie auf **[!UICONTROL Add URL Rewrite]**.
1. Wählen Sie **[!UICONTROL Custom]** in der Dropdownliste **[!UICONTROL Create URL Rewrite]** aus.
   1. Geben Sie [!UICONTROL Request Path] als **_shipping_** ein.
   1. Geben Sie in &quot;**[!UICONTROL Target Path]**&quot;den neuen URL-Schlüssel ein (_z. B. &quot;shipping1&quot;_).
   1. Wählen Sie **[!UICONTROL No]** in der Dropdownliste **[!UICONTROL Redirect]** aus.


      (**Hinweis**: Der Anfragepfad ist der vom Benutzer im Browser eingegebene Pfad und der Zielpfad ist der Ort, an den er umgeleitet werden soll.)

Vermeiden Sie außerdem die Verwendung dieser Suchbegriffe, die als *reservierte* Schlüsselwörter gekennzeichnet sind, die dazu führen, dass dieselbe Ausnahme erscheint. Wenn Sie einen der folgenden Suchbegriffe als URL-Schlüsselwert verwenden, wird derselbe Fehler angezeigt.


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

* [URL schreibt ](https://docs.magento.com/user-guide/marketing/url-rewrite.html) in unserem Benutzerhandbuch zu Merchandising und Promotions um.
* [Best Practices für SEO](https://docs.magento.com/user-guide/marketing/seo-best-practices.html) in unserem Benutzerhandbuch für Merchandising und Promotions.
