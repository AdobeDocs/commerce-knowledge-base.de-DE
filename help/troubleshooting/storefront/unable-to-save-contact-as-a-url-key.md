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

# Kann nicht gespeichert werden *Kontakt* als URL-Schlüssel

Dieser Artikel bietet eine Behelfslösung für das Problem, wenn Sie nicht speichern können *Kontakt* als URL-Schlüssel (z. B. &quot;/contact&quot;) für Produkte oder CMS-Seiten.

## Betroffene Produkte und Versionen

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.x

## Problem

Sie können ein Produkt oder eine CMS-Seite nicht mit dem Begriff speichern *Kontakt* als URL-Schlüssel. Wenn Sie versuchen, den URL-Schlüssel zu speichern, erhalten Sie einen Fehler, der anzeigt, dass der URL-Schlüssel eine doppelte URL ist.

<u>Zu reproduzierende Schritte</u>:

Erstellen Sie eine CMS-Seite mit *Kontakt* als URL-Schlüssel.

<u>Erwartetes Ergebnis</u>:

Die Seite wird gespeichert mit *Kontakt* als URL-Schlüssel.

<u>Tatsächliches Ergebnis</u>:

Sie können die Seite nicht speichern. Sie erhalten den Fehler: *Der im Feld URL-Schlüssel angegebene Wert generiert eine bereits vorhandene URL.*

## Ursache

*Kontakt* ist ein reserviertes Wort, das in `vendor/magento/module-contact/view/frontend/layout/contact_index_index.xml`.

```xml
<router id="standard">
      <route id="contact" frontName="contact">
          <module name="Magento_Contact" />
      </route>
  </router>
```

## Lösung

Sie können den Begriff nicht verwenden *Kontakt* als URL-Schlüssel verwenden, können Sie jedoch den Begriff *Kontakt* mit einem anderen Buchstaben oder einer anderen Zahl kombiniert werden (z. B. *contact1* und *contact2*). Auch wenn der Begriff *contact+\&lt;another number=&quot;&quot; or=&quot;&quot; letter=&quot;&quot;>* kann der Begriff eine beliebige Zeichenfolge sein, solange die Länge 255 Zeichen nicht überschreitet.

Führen Sie die folgenden Schritte aus:

1. Melden Sie sich bei Commerce Admin an.
1. Navigieren Sie zu **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL URL Rewrites]**.
1. Klicks **[!UICONTROL Add URL Rewrite]**.
1. Auswählen *[!UICONTROL Custom]* auf [!UICONTROL Create URL Rewrite] angezeigt.
   1. Im [!UICONTROL Request Path], geben Sie &quot;contact&quot;ein. Beachten Sie Folgendes: [!UICONTROL Request Path] ist, was ein Benutzer im Browser eingibt, und [!UICONTROL Target Path] ist, zu der er umgeleitet werden sollte.
   1. Im [!UICONTROL Target Path], geben Sie den neuen URL-Schlüssel ein (z. B. &quot;contact1&quot;).
   1. Auswählen *[!UICONTROL No]* im [!UICONTROL Redirect] angezeigt.

## Verwandtes Lesen

* [URL-Neuschreibungen](https://docs.magento.com/user-guide/marketing/url-rewrite.html) in unserem Benutzerhandbuch.
* [Best Practices für SEO](https://docs.magento.com/user-guide/marketing/seo-best-practices.html) in unserem Benutzerhandbuch.
