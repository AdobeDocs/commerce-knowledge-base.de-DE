---
title: Benutzerdefinierte SSL-Zertifikatgültigkeitsinformationen
description: Dieser Artikel bietet eine Lösung für den Fall, dass ein benutzerdefiniertes SSL-Zertifikat mit einem von der Adobe bereitgestellten SSL-Zertifikat aktualisiert wurde.
exl-id: cc968bae-f742-449b-b291-bc121ec45935
feature: Support
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Benutzerdefinierte SSL-Zertifikatgültigkeitsinformationen

Dieser Artikel bietet eine Lösung für den Fall, dass ein benutzerdefiniertes SSL-Zertifikat mit einem von der Adobe bereitgestellten SSL-Zertifikat aktualisiert wurde.

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur, [alle unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problem

Adobe Commerce aktualisiert SSL-Zertifikate automatisch 30 Tage vor ihrem Ablauf. Bei dieser Automatisierung wird nicht geprüft, ob es sich bei dem ersetzten Zertifikat um ein internes SSL oder ein benutzerdefiniertes SSL eines Drittanbieters handelt, sondern es wird bei Erkennen des Ablaufs durch ein gültiges internes SSL ersetzt. Dies kann zu Verwirrung bei Site-Besitzern und -Benutzern führen, die erwarten, dass sie das benutzerdefinierte Zertifikat auf der Site haben, sowie zu potenziellen anderen Funktionsproblemen, einschließlich, aber nicht beschränkt auf einen Site-Ausfall.

<u>Schritte zur Reproduktion</u>

1. Benutzerdefiniertes SSL-Zertifikat für die Website installiert.
1. Die Automatisierung erkennt, dass das benutzerdefinierte SSL-Zertifikat 30 Tage vor dem Ablauf ist.
1. Adobe Commerce ersetzt automatisch das benutzerdefinierte Zertifikat durch unser internes Zertifikat.

<u>Erwartete Ergebnisse</u>

Adobe Commerce überspringt benutzerdefinierte Zertifikate beim Ausführen seiner automatisierten SSL-Zertifikataktualisierung.

<u>Tatsächliche Ergebnisse</u>

Adobe Commerce aktualisiert alle Zertifikate 30 Tage nach ihrem Ablauf.

## Lösung

Wenn ein Händler sich dafür entscheidet, sein eigenes benutzerdefiniertes SSL-Zertifikat zu verwenden, muss es mehr als 30 Tage vor Ablauf des Zertifikats aktualisiert werden, um sicherzustellen, dass es nicht durch ein internes Adobe Commerce-SSL-Zertifikat ersetzt wird.

Wenn Sie sich in einer Situation befinden, in der Ihre benutzerdefinierte SSL durch unsere interne SSL ersetzt wurde, und Sie sie durch Ihr aktualisiertes benutzerdefiniertes SSL-Zertifikat ersetzen möchten, [ Sie (eine Support-Anfrage einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) mit dem Speicherort, an den Sie Ihre neuen Zertifikatdateien hochgeladen haben. Bitte das Startdatum der neuen SSL angeben. Sobald wir diese Informationen haben, können wir mit der Installation des neuen SSL-Zertifikats fortfahren.

## Verwandtes Lesen

* [SSL (TLS)-Zertifikate zum Magento Commerce Cloud: ](/help/how-to/general/ssl-tls-certificates-for-magento-commerce-cloud-faq.md) in unserer Support-Wissensdatenbank.
* [Referenz zu Befehlszeilen-Tools: magento-cloud certificate:add](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli/cloud-cli-reference#certificateadd) in unserer Entwicklerdokumentation.
* [Checkliste starten](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/launch/checklist) in unserer Entwicklerdokumentation.
* [Zugriff auf das Site-Wide Analysis Tool](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/access#step-2-access-site-wide-analysis-tool) in unserem Benutzerhandbuch.
