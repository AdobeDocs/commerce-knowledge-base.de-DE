---
title: robots.txt gibt 404 Fehler in Adobe Commerce in Cloud-Infrastruktur
description: Dieser Artikel bietet eine Fehlerbehebung für den Fall, dass die Datei „robots.txt“ einen 404-Fehler in Adobe Commerce in der Cloud-Infrastruktur ausgibt.
exl-id: 6f0b9f47-1901-4c43-88d8-fd992015d70f
feature: Cloud, Marketing Tools, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# robots.txt gibt 404 Fehler in Adobe Commerce in Cloud-Infrastruktur

Dieser Artikel bietet eine Fehlerbehebung für den Fall, dass die `robots.txt`-Datei einen 404-Fehler in Adobe Commerce in der Cloud-Infrastruktur ausgibt.

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur (alle Versionen)

## Problem

Die `robots.txt` funktioniert nicht und löst eine Nginx-Ausnahme aus. Die `robots.txt` wird dynamisch „on the fly“ generiert. Auf die `robots.txt`-Datei kann über die `/robots.txt`-URL nicht zugegriffen werden, da Nginx über eine Rewrite-Regel verfügt, die alle `/robots.txt`-Anfragen an die nicht vorhandene `/media/robots.txt`-Datei weiterleitet.

## Ursache

Dies geschieht in der Regel, wenn Nginx nicht ordnungsgemäß konfiguriert ist.

## Lösung

Die Lösung besteht darin, die Nginx-Regel zu deaktivieren, die `/robots.txt` Anfragen an die `/media/robots.txt`-Datei weiterleitet. Händler mit aktivierter Self-Service-Funktion können dies selbstständig tun, und Händler ohne aktivierter Self-Service-Funktion müssen ein Support-Ticket erstellen.

Wenn Sie den Self-Service nicht aktiviert haben (oder nicht sicher sind, ob er aktiviert ist), [senden Sie ein Magento-Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) und fordern Sie die Entfernung der Nginx-Umleitungsregel von `/robots.txt` Anfragen an `/media/robots.txt` an.

Wenn Sie den Self-Service aktiviert haben, aktualisieren Sie bitte ECE-Tools auf mindestens 2002.0.12 und entfernen Sie die Nginx-Umleitungsregel in Ihrer `.magento.app.yaml`. Weitere Informationen finden Sie in [ Entwicklerdokumentation unter „Hinzufügen von Sitemaps ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap.html?lang=de) Suchmaschinenrobotern“.

## Verwandtes Lesen

* [Wie Sie bösartigen Traffic für Magento Commerce Cloud auf Fastly-Ebene blockieren](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) finden Sie in unserer Support-Wissensdatenbank.
* [Hinzufügen von Sitemap- und Suchmaschinenrobotern](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap) in unserer Entwicklerdokumentation.
* [Suchmaschinenroboter](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html?lang=de#search-engine-robots) in unserem Benutzerhandbuch.
