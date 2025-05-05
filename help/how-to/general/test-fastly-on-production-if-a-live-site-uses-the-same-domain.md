---
title: Schnelles Testen in der Produktion, wenn eine Live-Site dieselbe Domain verwendet
description: Wenn Sie eine Live-Site in Ihrer Produktions-Domain („example.com„) haben und Ihren neuen Store in der Produktionsumgebung der Cloud-Infrastruktur in Adobe Commerce mit aktiviertem Fastly CDN testen müssen, empfehlen wir die Verwendung der Subdomain (wie „prod.example.com„), die Sie zuvor zu Fastly hinzugefügt haben, für alle Testaktivitäten vor dem Start. Dieser Artikel beschreibt die Details und enthält nützliche Links zu den zugehörigen Adobe Commerce-Dokumentationsressourcen.
exl-id: bc9d11c8-ce47-461d-b5b8-c03494bc4ceb
feature: Cache
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 0%

---

# Schnelles Testen in der Produktion, wenn eine Live-Site dieselbe Domain verwendet

Wenn Sie eine Live-Site in Ihrer Produktions-Domain (`example.com`) verwenden und Ihren neuen Store in der Produktionsumgebung der Cloud-Infrastruktur in Adobe Commerce mit aktiviertem Fastly CDN testen müssen, empfehlen wir die Verwendung der Subdomain (wie `prod.example.com`), die Sie zuvor zu Fastly hinzugefügt haben, für alle Testaktivitäten vor dem Start. Dieser Artikel beschreibt die Details und enthält nützliche Links zu den zugehörigen Adobe Commerce-Dokumentationsressourcen.

## Problem

Ihr aktueller Store, der die `example.com` Produktions-Domain verwendet, ist live und funktioniert. Sie müssen jedoch Ihren neuen Store testen, der mit Adobe Commerce in der Cloud-Infrastruktur erstellt und in der Produktionsumgebung bereitgestellt wird, wobei der Fastly-Dienst für den vollständigen Seitencache aktiviert sein muss.

Das Problem besteht darin, dass die Produktionsumgebung Ihres Adobe Commerce on Cloud-Infrastrukturprojekts dieselbe Live-Domain (`example.com`) verwendet und Sie Ihre neue Site nicht zu dieser Domain wechseln können, während Ihr aktueller Live Store gleichzeitig in derselben Domain ausgeführt wird.

### Warum sollte Fastly für Tests in der Produktionsumgebung verwendet werden?

Theoretisch könnten Sie die Verwendung von Fastly CDN überspringen und Ihren Adobe Commerce im Cloud-Infrastrukturspeicher in der Produktionsumgebung testen, ohne den vollständigen Seitencache zu aktivieren.

Wenn jedoch der vollständige Seiten-Cache aktiviert ist, funktioniert Ihr Store anders. Sie erfahren nie die tatsächliche Live-Performance Ihrer Site, wenn Sie sie vor dem Start nicht mit CDN getestet haben. Das Testen Ihres Stores in der Produktionsumgebung mit aktiviertem Fastly CDN ist die offizielle Adobe Commerce-Empfehlung.

## Lösung: Produktions-Subdomain verwenden

Verwenden Sie die Subdomain der ersten Ebene (`prod.example.com`) für Ihren neuen Adobe Commerce in Cloud Infrastructure Store in der Produktionsumgebung, während die aktuelle Live-Site in der Basis-Domain (`example.com`) beibehalten wird.

Bei der Planung Ihres Adobe Commerce in einem Cloud-Infrastrukturprojekt können Sie eine solche Produktions-Subdomain angeben und das Cloud-Infrastrukturteam bitten, die Subdomain auf den Fastly-Service zu verweisen.

Führen Sie die folgenden Schritte aus, um die Subdomain in Ihrem Adobe Commerce in einem Cloud-Infrastrukturprojekt zu verarbeiten:

* [Senden eines Support-Tickets](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) mit der Aufforderung, die Subdomain zur Fastly-Service-/Nginx-Konfiguration (für Adobe Commerce auf der Cloud-Infrastruktur-Pro-Planarchitektur) hinzuzufügen.
* Konfigurieren Sie die entsprechenden DNS-Einstellungen auf Ihrer Seite.

Nachdem Sie die Schritte für die Konfiguration der Subdomain ausgeführt haben, müssen Sie auch diese Schritte ausführen, um Ihre Produktions-Domain für das SSL-Zertifikat zu validieren:

* Laden Sie den DNS-TXT-Eintrag zur SSL-Validierung Ihrer Produktions-Domain hoch.
* [Senden eines Support-Tickets](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) mit der Anforderung, die Produktions-Domain für das SSL-Zertifikat zu validieren.

Durch die Verwendung der Subdomain können Sie einen „Soft Launch“ Ihres Stores in Zukunft durchführen - da ein solcher Launch nur die Aktualisierung der entsprechenden DNS-Einstellungen erfordert.

## Verwandte Dokumentation

In unserer Support-Wissensdatenbank:

* [Konfigurieren von Fastly-DNS-Einstellungen in Staging- und Produktionsumgebungen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/configure-fastly-dns-settings-on-staging-and-production-environments.html?lang=de)
* [Richten Sie Fastly für den Starter-Plan in der Cloud ein](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/set-up-fastly-for-starter-plan-on-cloud.html?lang=de)
* [Potenzielle Blocker für den Start auf Adobe Commerce in der Cloud-Infrastruktur](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/blockers-launching-on-magento-commerce-cloud.html?lang=de)

In unserer Entwicklerdokumentation:

* [Fastly-Übersicht](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html?lang=de)
* [Go-Live-Checkliste: DNS-Konfigurationen für Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html?lang=de)
