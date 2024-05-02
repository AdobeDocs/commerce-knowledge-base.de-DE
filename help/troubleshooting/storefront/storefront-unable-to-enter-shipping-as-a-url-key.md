---
title: Versand kann nicht als URL-Schlüssel gespeichert werden
description: Dieser Artikel bietet eine Problemumgehung, wenn Sie "Versand"nicht als URL-Schlüssel (z. B. "/shipping") für Produkte oder CMS-Seiten speichern können. Wenn Sie versuchen, den URL-Schlüssel zu speichern, erhalten Sie einen Fehler, der anzeigt, dass der URL-Schlüssel eine doppelte URL ist.
exl-id: df19b597-f615-4b19-82c1-59cc179fa720
feature: Marketing Tools, Shipping/Delivery, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# Versand kann nicht als URL-Schlüssel gespeichert werden

Dieser Artikel bietet eine Problemumgehung, wenn Sie &quot;Versand&quot;nicht als URL-Schlüssel (z. B. &quot;/shipping&quot;) für Produkte oder CMS-Seiten speichern können. Wenn Sie versuchen, den URL-Schlüssel zu speichern, erhalten Sie einen Fehler, der anzeigt, dass der URL-Schlüssel eine doppelte URL ist.

## Betroffene Produkte und Versionen

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.x

## Problem

Sie können keine CMS-Seite mit dem Begriff &quot;Versand&quot;im URL-Schlüssel speichern.

<u>Zu reproduzierende Schritte</u>:

Erstellen Sie eine CMS-Seite mit URL-Schlüssel als &quot;Versand&quot;.

<u>Erwartetes Ergebnis</u>:

Die Seite wird mit &quot;Versand&quot;im URL-Schlüssel gespeichert.

<u>Tatsächliches Ergebnis</u>:

Das Speichern ist nicht möglich und es wird ein Fehler angezeigt: *Der im Feld URL-Schlüssel angegebene Wert generiert eine bereits vorhandene URL.*

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

Sie können den Begriff &quot;Versand&quot;nicht in Ihrem URL-Schlüssel verwenden. Sie können jedoch den Begriff &quot;Versand&quot;in Verbindung mit einem anderen Buchstaben oder einer anderen Nummer verwenden (z. B. &quot;Versand1&quot;und &quot;Versand2&quot;). Auch wenn der Begriff nicht &quot;Versand&quot;sein muss+&lt;another number=&quot;&quot; or=&quot;&quot; letter=&quot;&quot;> - der Begriff kann eine beliebige Zeichenfolge sein, solange die Länge 255 Zeichen nicht überschreitet.

Führen Sie die folgenden Schritte aus:

1. Melden Sie sich bei Commerce Admin an.
1. Navigieren Sie zu **Marketing** > SEO &amp; Suche > **URL-Neuschreibungen**.
1. Klicks **URL-Neufassung hinzufügen**.
1. Auswählen *Benutzerdefiniert* in der Dropdown-Liste URL-Neuschreiben erstellen .
   1. Geben Sie im Anfragepfad &quot;Versand&quot;ein. Hinweis: Der Anfragepfad ist der vom Benutzer im Browser eingegebene Pfad und der Zielpfad ist der Ort, an den er umgeleitet werden soll.
   1. Geben Sie im Zielpfad den neuen URL-Schlüssel ein (z. B. &quot;shipping1&quot;).
   1. Auswählen **Nein** in der Dropdown-Liste Umleitung .

## Verwandtes Lesen

* [URL-Neuschreibungen](https://docs.magento.com/user-guide/marketing/url-rewrite.html) in unserem Benutzerhandbuch.
* [Best Practices für SEO](https://docs.magento.com/user-guide/marketing/seo-best-practices.html) in unserem Benutzerhandbuch.
