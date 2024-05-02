---
title: Benutzerdefinierte SSL-Zertifikatablaufinformationen
description: Dieser Artikel bietet eine Lösung für den Fall, dass ein benutzerdefiniertes SSL-Zertifikat mit einem von Adobe bereitgestellten SSL-Zertifikat aktualisiert wurde.
exl-id: cc968bae-f742-449b-b291-bc121ec45935
feature: Support
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Benutzerdefinierte SSL-Zertifikatablaufinformationen

Dieser Artikel bietet eine Lösung für den Fall, dass ein benutzerdefiniertes SSL-Zertifikat mit einem von Adobe bereitgestellten SSL-Zertifikat aktualisiert wurde.

## Betroffene Produkte und Versionen

Adobe Commerce zur Cloud-Infrastruktur, [alle unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problem

Adobe Commerce aktualisiert die SSL-Zertifikate 30 Tage vor Ablauf automatisch. Bei dieser Automatisierung wird nicht geprüft, ob es sich bei dem zu ersetzenden Zertifikat um eine interne SSL- oder eine benutzerdefinierte Drittanbieter-SSL handelt, und bei der Ablauferkennung durch eine gültige interne SSL-Verbindung ersetzt. Dies kann für Site-Eigentümer und -Benutzer, die erwarten, dass sich das benutzerdefinierte Zertifikat auf der Site befindet, Verwirrung stiften und andere Funktionsprobleme verursachen, darunter auch, aber nicht beschränkt auf, einen Site-Ausfall.

<u>Zu reproduzierende Schritte</u>

1. Benutzerdefiniertes SSL-Zertifikat, das für die Website installiert ist.
1. Die Automatisierung erkennt, dass das benutzerdefinierte SSL-Zertifikat 30 Tage vor seinem Ablauf liegt.
1. Adobe Commerce ersetzt das benutzerdefinierte Zertifikat automatisch durch unser internes Zertifikat.

<u>Erwartete Ergebnisse</u>

Adobe Commerce überspringt benutzerdefinierte Zertifikate beim Ausführen der automatisierten SSL-Zertifikataktualisierung.

<u>Tatsächliche Ergebnisse</u>

Adobe Commerce aktualisiert jedes Zertifikat, wenn es 30 Tage nach Ablauf ist.

## Lösung

Wenn ein Händler sich dafür entscheidet, sein eigenes benutzerdefiniertes SSL-Zertifikat zu verwenden, muss es mehr als 30 Tage vor Ablauf des Zertifikats aktualisiert werden, um sicherzustellen, dass es nicht durch ein internes Adobe Commerce-SSL-Zertifikat ersetzt wird.

Wenn Sie sich in einer Situation befinden, in der Ihr benutzerdefiniertes SSL durch unser internes SSL ersetzt wurde und Sie es durch Ihr aktualisiertes benutzerdefiniertes SSL-Zertifikat ersetzen möchten, wenden Sie sich an [Support-Anfrage senden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) mit dem Speicherort, an den Sie die neuen Zertifikatdateien hochgeladen haben. Bitte geben Sie das Anfangsdatum der neuen SSL-Verschlüsselung an. Sobald wir über diese Informationen verfügen, können wir mit der Installation des neuen SSL-Zertifikats fortfahren.

## Verwandtes Lesen

* [SSL-Zertifikate (TLS) für Magento Commerce Cloud: FAQ](/help/how-to/general/ssl-tls-certificates-for-magento-commerce-cloud-faq.md) in unserer Wissensdatenbank.
* [Befehlszeilen-Tools-Referenz: magento-cloud-Zertifikat:add](https://devdocs.magento.com/guides/v2.4/reference/cli/magento-cloud.html#certificateadd) in unserer Entwicklerdokumentation.
* [Checkliste für Launch](https://devdocs.magento.com/cloud/live/site-launch-checklist.html)in unserer Entwicklerdokumentation.
* [Zugriff auf das Site-weite Analyse-Tool](https://docs.magento.com/user-guide/reports/site-wide-analysis-tool.html#step-2-access-site-wide-analysis-tool) in unserem Benutzerhandbuch.
