---
title: Der Bericht zum Sicherheitsscan-Tool ist leer
description: In diesem Artikel wird das Problem behoben, dass das Sicherheitsscan-Tool anstelle des eigentlichen Berichts eine leere Seite anzeigt. Um dies zu beheben, müssen Sie möglicherweise die vom Tool verwendeten IPs zur Firewall-Zulassungsliste hinzufügen.
exl-id: e5f7f8c6-2dd3-44e3-8d19-f1f38d06dd6c
feature: Compliance, Security
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# Der Bericht zum Sicherheitsscan-Tool ist leer

In diesem Artikel wird das Problem behoben, dass das Sicherheitsscan-Tool anstelle des eigentlichen Berichts eine leere Seite anzeigt. Um dies zu beheben, müssen Sie möglicherweise die vom Tool verwendeten IPs zur Firewall-Zulassungsliste hinzufügen.

## Betroffene Produkte und Versionen:

* Adobe Commerce (alle Bereitstellungsmethoden und Magento Open Source, Alle Versionen)

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Konfigurieren Sie das Sicherheitsscan-Tool, um Ihre Website zu überprüfen, wie in [Sicherheitsprüfung](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan) in unserem Benutzerhandbuch beschrieben.
1. Wählen Sie in der Spalte Aktionen die Option **Scan ausführen**.

<u>Erwartete Ergebnisse</u>:

Zeigen Sie die Benachrichtigung zum Abschluss des Berichts und die Möglichkeit an, den Bericht zu öffnen.

<u>Tatsächliche Ergebnisse</u>:

Keine Benachrichtigung und kein Bericht verfügbar.

## Ursache

Dieses Problem tritt möglicherweise auf, weil das Sicherheitsscan-Tool Ihre Website nicht erreichen konnte. Dies bedeutet, dass entweder die Website nicht erreichbar ist oder das Sicherheitsscan-Tool blockiert wird.

## Lösung

Versuchen Sie, Ihre Website zu öffnen.

* Wenn die Seite erfolgreich geladen wird, müssen Sie möglicherweise die von den Security Scan Tools verwendeten IPs zur Firewall-Zulassungsliste hinzufügen. Die folgenden IPs werden verwendet: 52.87.98.44, 34.196.167.176, 3.218.25.102 in den Ports 80 und 443.
* Wenn die Site nicht geladen wird und die Meldung &quot;*&quot;Es ist ein Fehler bei der Verarbeitung Ihrer Anfrage aufgetreten&quot;* zurückgibt, überprüfen Sie Ihre Website auf mögliche Fehler.

## Verwandtes Lesen

* [Go live and launch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/launch/overview) in unserer Entwicklerdokumentation.
* [Sicherheitsscan](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan) in unserem Benutzerhandbuch.
