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

# Kann nicht gespeichert werden _Versand_ als URL-Schlüssel

Dieser Artikel bietet eine Problemumgehung, wenn Sie den Versand nicht als URL-Schlüssel speichern können (_z. B. /shipping_) für Produkte oder CMS-Seiten. Wenn Sie versuchen, den URL-Schlüssel zu speichern, erhalten Sie einen Fehler, der anzeigt, dass der URL-Schlüssel eine doppelte URL ist.

## Betroffene Produkte und Versionen

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.x

## Problem

Sie können eine CMS-Seite nicht mit dem Begriff speichern _Versand_ im URL-Schlüssel.

<u>Zu reproduzierende Schritte</u>:

Erstellen Sie eine **[!UICONTROL CMS page]** mit dem URL-Schlüssel als _Versand_.

<u>Erwartetes Ergebnis</u>:

Die Seite speichert mit _Versand_ als URL-Schlüssel.

<u>Tatsächliches Ergebnis</u>:

Sie können nicht speichern, da dieser Fehler auftritt:
*Der im Feld URL-Schlüssel angegebene Wert generiert eine bereits vorhandene URL.*

## Ursache

Der Versand ist ein reserviertes Wort, das in `vendor/magento/module-shipping/etc/frontend/routes.xml`.

```xml
<router id="standard">
      <route id="shipping" frontName="shipping">
          <module name="Magento_Shipping" />
      </route>
  </router>
```

## Lösung

Sie können den Begriff nicht verwenden _Versand_ in Ihrem URL-Schlüssel - Sie können jedoch den Begriff _Versand_ kombiniert mit einem anderen Buchstaben oder einer anderen Zahl (_Beispiel: shipping1 und shipping2_).

Auch wenn der Begriff _Versand_+&lt;another number=&quot;&quot; or=&quot;&quot; letter=&quot;&quot;> - der Begriff kann eine beliebige Zeichenfolge sein, solange die Länge nicht überschreitet *255* Zeichen.

## Führen Sie die folgenden Schritte aus:

1. Melden Sie sich bei Adobe Commerce Admin an.
1. Navigieren Sie zu **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL URL Rewrites]**.
1. Klicks **[!UICONTROL Add URL Rewrite]**.
1. Auswählen **[!UICONTROL Custom]** im **[!UICONTROL Create URL Rewrite]** angezeigt.
   1. Geben Sie die [!UICONTROL Request Path] as **_Versand_**.
   1. Im **[!UICONTROL Target Path]** Geben Sie den neuen URL-Schlüssel (_Beispiel: &quot;shipping1&quot;_).
   1. Auswählen **[!UICONTROL No]** im **[!UICONTROL Redirect]** angezeigt.


      (**Hinweis**: Der Anfragepfad ist der vom Benutzer im Browser eingegebene Pfad und der Zielpfad ist der Ort, an den er umgeleitet werden soll.)

Vermeiden Sie außerdem die Verwendung dieser Suchbegriffe, die als *reserviert* Suchbegriffe, die die gleiche Ausnahme verursachen. Wenn Sie einen der folgenden Suchbegriffe als URL-Schlüsselwert verwenden, wird derselbe Fehler angezeigt.


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

* [URL-Neuschreibungen](https://docs.magento.com/user-guide/marketing/url-rewrite.html) im Benutzerhandbuch zu Merchandising und Promotions.
* [Best Practices für SEO](https://docs.magento.com/user-guide/marketing/seo-best-practices.html) im Benutzerhandbuch zu Merchandising und Promotions.
