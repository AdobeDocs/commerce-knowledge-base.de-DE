---
title: Der Bericht des Security Scan Tools ist leer
description: Dieser Artikel bietet eine Lösung für das Problem, dass das Security Scan Tool eine leere Seite anstelle des eigentlichen Berichts anzeigt. Um dies zu beheben, müssen Sie die vom Tool verwendeten IP-Adressen möglicherweise der Firewall-Zulassungsliste hinzufügen.
exl-id: e5f7f8c6-2dd3-44e3-8d19-f1f38d06dd6c
feature: Compliance, Security
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# Der Bericht des Security Scan Tools ist leer

Dieser Artikel bietet eine Lösung für das Problem, dass das Security Scan Tool eine leere Seite anstelle des eigentlichen Berichts anzeigt. Um dies zu beheben, müssen Sie die vom Tool verwendeten IP-Adressen möglicherweise der Firewall-Zulassungsliste hinzufügen.

## Betroffene Produkte und Versionen:

* Adobe Commerce (alle Bereitstellungsmethoden) und Magento Open Source, Alle Versionen

## Problem

<u>Schritte zur Reproduktion</u>:

1. Konfigurieren Sie das Sicherheits-Scan-Tool, um Ihre Website zu überprüfen[ wie unter ](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/security/security-scan) beschrieben.
1. Wählen Sie in der Spalte Aktionen die Option **Suche ausführen** aus.

<u>Erwartete Ergebnisse</u>:

Anzeigen der Benachrichtigung zum Abschluss des Berichts und der Möglichkeit, den Bericht zu öffnen.

<u>Tatsächliche Ergebnisse</u>:

Keine Benachrichtigung und kein Bericht verfügbar.

## Ursache

Dieses Problem kann auftreten, weil das Security Scan Tool Ihre Website nicht erreichen konnte. Das bedeutet, dass entweder die Website nicht erreichbar ist oder das Security Scan Tool blockiert wird.

## Lösung

Versuchen Sie, Ihre Website zu öffnen.

* Auf die Zulassungsliste setzen Wenn die Seite erfolgreich geladen wurde, müssen Sie möglicherweise die von den Security Scan Tools verwendeten IPs zur Firewall hinzufügen. Die folgenden IPs werden verwendet: 52.87.98.44, 34.196.167.176, 3.218.25.102 an den Ports 80 und 443.
* Wenn die Site nicht geladen wird und die *„Bei der Verarbeitung Ihrer Anfrage ist ein Fehler aufgetreten“ zurückgibt* überprüfen Sie Ihre Website auf mögliche Fehler.

## Verwandtes Lesen

* [Live-Schaltung und ](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/launch/overview)) in unserer Entwicklerdokumentation.
* [Security Scan](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/security/security-scan) in unserem Benutzerhandbuch.
