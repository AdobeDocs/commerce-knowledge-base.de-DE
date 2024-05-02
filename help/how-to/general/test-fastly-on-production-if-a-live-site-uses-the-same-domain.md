---
title: Testen Sie schnell bei der Produktion, wenn eine Live-Site dieselbe Domäne verwendet
description: Wenn Sie eine Live-Site in Ihrer Produktionsdomäne ("example.com") eingerichtet haben und Ihren neuen Store in Adobe Commerce in der Produktionsumgebung der Cloud-Infrastruktur testen müssen, in der Fastly CDN aktiviert ist, empfehlen wir die Verwendung der Subdomain (z. B. "prod.example.com"), die Sie zuvor zu Fastly hinzugefügt haben, für alle Testaktivitäten vor dem Start. In diesem Artikel werden die Details erläutert und nützliche Links zu den entsprechenden Adobe Commerce-Dokumentationsressourcen bereitgestellt.
exl-id: bc9d11c8-ce47-461d-b5b8-c03494bc4ceb
feature: Cache
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 0%

---

# Testen Sie schnell bei der Produktion, wenn eine Live-Site dieselbe Domäne verwendet

Wenn eine Live-Site in Ihrer Produktionsdomäne aktiv ist (`example.com`). Wenn Sie Ihren neuen Store in Adobe Commerce in der Produktionsumgebung der Cloud-Infrastruktur testen müssen und Fastly CDN aktiviert ist, empfehlen wir die Verwendung der Subdomain (wie `prod.example.com`), nachdem es zuvor zu Fastly hinzugefügt wurde, für alle Testaktivitäten vor dem Start. In diesem Artikel werden die Details erläutert und nützliche Links zu den entsprechenden Adobe Commerce-Dokumentationsressourcen bereitgestellt.

## Problem

Ihr aktueller Store, der die `example.com` Die Produktionsdomäne ist live und läuft. Sie müssen jedoch Ihren neuen Store testen, der mit Adobe Commerce in der Cloud-Infrastruktur erstellt und in der Produktionsumgebung bereitgestellt wurde und für den der Fastly full page cache service aktiviert ist.

Das Problem besteht darin, dass die Produktionsumgebung Ihres Adobe Commerce-Projekts in der Cloud-Infrastruktur dieselbe Live-Domäne (`example.com`), und Sie können Ihre neue Site nicht zu dieser Domäne wechseln, während Ihr aktueller Live Store gleichzeitig in derselben Domäne ausgeführt wird.

### Warum verwenden Sie Fastly zum Testen in der Produktionsumgebung?

Theoretisch können Sie die Verwendung von Fastly CDN überspringen und Ihre Adobe Commerce im Cloud-Infrastrukturspeicher der Produktionsumgebung testen, ohne dass der vollständige Seiten-Cache aktiviert ist.

Wenn jedoch der vollständige Seiten-Cache aktiviert ist, funktioniert Ihr Store anders. Sie kennen die tatsächliche Live-Leistung Ihrer Site nie, wenn Sie sie vor dem Start nicht mit CDN getestet haben. Das Testen Ihres Stores bei der Produktion mit aktiviertem Fastly CDN ist die offizielle Adobe Commerce-Empfehlung.

## Lösung: Subdomain für die Produktion verwenden

Verwenden Sie die Subdomain der ersten Ebene (`prod.example.com`) für Ihre neue Adobe Commerce im Cloud-Infrastrukturspeicher in der Produktionsumgebung, während die aktuelle Live-Site in der Basisdomäne (`example.com`).

Bei der Planung Ihres Adobe Commerce-Projekts für die Cloud-Infrastruktur können Sie eine solche Produktions-Subdomain angeben und das Cloud-Infrastrukturteam auffordern, die Subdomain auf den Fastly-Dienst zu verweisen.

Führen Sie die folgenden Schritte aus, um die Subdomain in Ihrem Adobe Commerce-Projekt in der Cloud-Infrastruktur zu verarbeiten:

* [Support-Ticket senden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) Anfrage zum Hinzufügen der Subdomain zur Fastly Service/Nginx-Konfiguration (für Adobe Commerce auf Cloud Infrastructure Pro Plan-Architektur).
* Konfigurieren Sie die entsprechenden DNS-Einstellungen auf Ihrer Seite.

Nachdem Sie die Schritte zur Konfiguration der Subdomain ausgeführt haben, müssen Sie auch die folgenden Schritte ausführen, um Ihre Produktionsdomäne auf das SSL-Zertifikat zu überprüfen:

* Laden Sie den DNS-TXT-Eintrag für die SSL-Validierung Ihrer Produktionsdomäne hoch.
* [Support-Ticket senden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) Anforderung zur Validierung der Produktionsdomäne für das SSL-Zertifikat.

Durch die Verwendung der Subdomain können Sie in Zukunft einen &quot;Soft Launch&quot;Ihres Stores ausführen - da für einen solchen Launch nur die entsprechenden DNS-Einstellungen aktualisiert werden müssen.

## Verwandte Dokumentation

In unserer Support-Wissensdatenbank:

* [Fastly-DNS-Einstellungen in Staging- und Produktionsumgebungen konfigurieren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/configure-fastly-dns-settings-on-staging-and-production-environments.html)
* [Schnelles Einrichten des Starter-Plans für Cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/set-up-fastly-for-starter-plan-on-cloud.html)
* [Potenzielle Blocker für den Start auf Adobe Commerce in der Cloud-Infrastruktur](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/blockers-launching-on-magento-commerce-cloud.html)

In unserer Entwicklerdokumentation:

* [Schnelle Übersicht](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html)
* [Go live checklist: DNS-Konfigurationen für Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html)
