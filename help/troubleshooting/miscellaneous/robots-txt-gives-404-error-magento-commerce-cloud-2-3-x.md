---
title: robots.txt gibt 404-Fehler Adobe Commerce in der Cloud-Infrastruktur
description: Dieser Artikel enthält eine Fehlerbehebung für den Fall, dass die Datei "robots.txt"in Adobe Commerce einen 404-Fehler in der Cloud-Infrastruktur ausgibt.
exl-id: 6f0b9f47-1901-4c43-88d8-fd992015d70f
feature: Cloud, Marketing Tools, Paas
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# robots.txt gibt 404-Fehler Adobe Commerce in der Cloud-Infrastruktur

Dieser Artikel enthält eine Fehlerbehebung für den Zeitpunkt, zu dem die Variable `robots.txt` -Datei gibt in Adobe Commerce in der Cloud-Infrastruktur einen 404-Fehler aus.

## Betroffene Produkte und Versionen

Adobe Commerce in der Cloud-Infrastruktur (alle Versionen)

## Problem

Die `robots.txt` -Datei funktioniert nicht und gibt eine Nginx-Ausnahme aus. Die `robots.txt` wird dynamisch &quot;on the fly&quot; generiert. Die `robots.txt` auf die Datei nicht zugreifen kann. `/robots.txt` URL, da Nginx über eine Neuschreibungsregel verfügt, die alle `/robots.txt` Anforderungen an `/media/robots.txt` nicht vorhanden ist.

## Ursache

Dies geschieht normalerweise, wenn Nginx nicht ordnungsgemäß konfiguriert ist.

## Lösung

Die Lösung besteht darin, die Nginx-Regel zu deaktivieren, die umleitet `/robots.txt` Anforderungen an `/media/robots.txt` -Datei. Händler mit aktiviertem Self-Service können dies allein tun, und Händler ohne aktivierten Self-Service müssen ein Support-Ticket erstellen.

Wenn Sie die Self-Service-Funktion nicht aktiviert haben (oder nicht sicher sind, ob sie aktiviert ist), [Senden eines Magento Support-Tickets](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) Anforderung der Entfernung der Nginx-Umleitungsregel aus `/robots.txt` Anforderungen an `/media/robots.txt`.

Wenn Sie die Self-Service-Funktion aktiviert haben, aktualisieren Sie bitte ECE-Tools auf mindestens 2002.0.12 und entfernen Sie die Nginx-Weiterleitungsregel in Ihrer `.magento.app.yaml` -Datei. Weitere Informationen finden Sie unter [Sitemap- und Suchmaschinenroboter hinzufügen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap.html) in unserer Entwicklerdokumentation für weitere Informationen.

## Verwandte Informationen

* [Blockieren von böswilligem Traffic für Magento Commerce Cloud auf Fastly-Ebene](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) in unserer Wissensdatenbank.
* [Sitemap- und Suchmaschinenroboter hinzufügen](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) in unserer Entwicklerdokumentation.
* [Suchmaschinen-Roboter](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots) in unserem Benutzerhandbuch.
