---
title: '*contact* kann nicht als URL-Schlüssel gespeichert werden'
description: Dieser Artikel bietet eine Problemumgehung, wenn Sie *contact* nicht als URL-Schlüssel (z. B. "/contact") für Produkte oder CMS-Seiten speichern können. Wenn Sie versuchen, den URL-Schlüssel zu speichern, erhalten Sie einen Fehler, der anzeigt, dass der URL-Schlüssel eine doppelte URL ist.
exl-id: eb340813-aba5-43a4-af5d-8fb64c93e021
feature: CMS, Marketing Tools, Storefront
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# *contact* kann nicht als URL-Schlüssel gespeichert werden

Dieser Artikel bietet eine Problemumgehung, wenn Sie *contact* nicht als URL-Schlüssel (z. B. &quot;/contact&quot;) für Produkte oder CMS-Seiten speichern können.

## Betroffene Produkte und Versionen

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.x

## Problem

Sie können ein Produkt oder eine CMS-Seite nicht mit dem Begriff *contact* als URL-Schlüssel speichern. Wenn Sie versuchen, den URL-Schlüssel zu speichern, erhalten Sie einen Fehler, der anzeigt, dass der URL-Schlüssel eine doppelte URL ist.

<u>Zu reproduzierende Schritte</u>:

Erstellen Sie eine CMS-Seite mit *contact* als URL-Schlüssel.

<u>Erwartetes Ergebnis</u>:

Die Seite wird mit *contact* als URL-Schlüssel gespeichert.

<u>Tatsächliches Ergebnis</u>:

Sie können die Seite nicht speichern. Sie erhalten den Fehler: *Der im Feld URL-Schlüssel angegebene Wert generiert eine bereits vorhandene URL.*

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

Sie können den Begriff *contact* nicht als URL-Schlüssel verwenden. Sie können jedoch den Begriff *contact* in Verbindung mit einem anderen Brief oder einer anderen Nummer verwenden (z. B. *contact1* und *contact2*). Der Begriff muss zwar nicht &quot;*contact+\&lt;andere Zahl oder Buchstabe\>*&quot;lauten, der Begriff kann jedoch eine beliebige Zeichenfolge sein, solange die Länge 255 Zeichen nicht überschreitet.

Führen Sie die folgenden Schritte aus:

1. Melden Sie sich bei Commerce Admin an.
1. Gehen Sie zu **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL URL Rewrites]**.
1. Klicken Sie auf **[!UICONTROL Add URL Rewrite]**.
1. Wählen Sie *[!UICONTROL Custom]* in der Dropdownliste [!UICONTROL Create URL Rewrite] aus.
   1. Geben Sie in das Feld [!UICONTROL Request Path] &quot;contact&quot;ein. Beachten Sie, dass der [!UICONTROL Request Path] ist, was ein Benutzer in den Browser eingibt, und der [!UICONTROL Target Path] ist, zu dem er umleiten soll.
   1. Geben Sie im [!UICONTROL Target Path] den neuen URL-Schlüssel ein (z. B. &quot;contact1&quot;).
   1. Wählen Sie *[!UICONTROL No]* in der Dropdownliste [!UICONTROL Redirect] aus.

## Verwandtes Lesen

* [URL schreibt ](https://docs.magento.com/user-guide/marketing/url-rewrite.html) in unser Benutzerhandbuch um.
* [Best Practices für SEO](https://docs.magento.com/user-guide/marketing/seo-best-practices.html) in unserem Benutzerhandbuch.
