---
title: Der Bericht des Security Scan Tools ist leer
description: Dieser Artikel bietet eine Lösung für das Problem, dass das Security Scan Tool eine leere Seite anstelle des eigentlichen Berichts anzeigt. Um dies zu beheben, müssen Sie die vom Tool verwendeten IP-Adressen möglicherweise der Firewall-Zulassungsliste hinzufügen.
exl-id: e5f7f8c6-2dd3-44e3-8d19-f1f38d06dd6c
feature: Compliance, Security
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
    internal-label: Compliance
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%
---
# Der Bericht des Security Scan Tools ist leer

Dieser Artikel bietet eine Lösung für das Problem, dass das Security Scan Tool eine leere Seite anstelle des eigentlichen Berichts anzeigt. Um dies zu beheben, müssen Sie die vom Tool verwendeten IP-Adressen möglicherweise der Firewall-Zulassungsliste hinzufügen.

## Betroffene Produkte und Versionen:

* Adobe Commerce (alle Bereitstellungsmethoden) und Magento Open Source, Alle Versionen

## Problem

<u>Schritte zur Reproduktion</u>:

1. Konfigurieren Sie das Sicherheits-Scan-Tool, um Ihre Website zu überprüfen[&#x200B; wie unter &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan) beschrieben.
1. Wählen Sie in der Spalte Aktionen die Option **Suche ausführen** aus.

<u>Erwartete Ergebnisse</u>:

Anzeigen der Benachrichtigung zum Abschluss des Berichts und der Möglichkeit, den Bericht zu öffnen.

<u>Tatsächliche Ergebnisse</u>:

Keine Benachrichtigung und kein Bericht verfügbar.

## Ursache

Dieses Problem kann auftreten, weil das Security Scan Tool Ihre Website nicht erreichen konnte. Das bedeutet, dass entweder die Website nicht erreichbar ist oder das Security Scan Tool blockiert wird.

## Lösung

Versuchen Sie, Ihre Website zu öffnen.

* Wenn die Seite erfolgreich geladen wurde, müssen Sie möglicherweise die von den Security Scan Tools verwendeten IPs zur Firewall hinzufügen. Die folgenden IPs werden verwendet: 52.87.98.44, 34.196.167.176, 3.218.25.102 an den Ports 80 und 443.
* Wenn die Site nicht geladen wird und die *„Bei der Verarbeitung Ihrer Anfrage ist ein Fehler aufgetreten“ zurückgibt* überprüfen Sie Ihre Website auf mögliche Fehler.

## Verwandtes Lesen

* [Live-Schaltung und &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/launch/overview)) in unserer Entwicklerdokumentation.
* [Security Scan](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan) in unserem Benutzerhandbuch.
