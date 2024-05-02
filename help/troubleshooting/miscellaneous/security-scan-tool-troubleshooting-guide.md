---
title: Handbuch zur Fehlerbehebung bei Adobe Commerce Security Scan-Tools
description: Erfahren Sie, wie Sie die verschiedenen Probleme mit dem Sicherheitsscan-Tool für Adobe Commerce und Magento Open Source beheben können.
exl-id: 35e18a11-bda9-47eb-924a-1095f4f01017
feature: Compliance, Security
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '859'
ht-degree: 0%

---

# Handbuch zur Fehlerbehebung bei Adobe Commerce Security Scan-Tools

Erfahren Sie, wie Sie die verschiedenen Probleme mit dem Sicherheitsscan-Tool für Adobe Commerce und Magento Open Source beheben können.

## Problem: Die Site kann nicht gesendet werden

Das Sicherheitsscan-Tool erfordert, dass Sie den Besitz Ihrer Site nachweisen, bevor die Domäne zum Sicherheitsscan-Tool hinzugefügt werden kann. Dies kann durch Hinzufügen eines Bestätigungscodes zu Ihrer Site mithilfe eines HTML-Kommentars oder der `<meta>` -Tag. Der HTML-Kommentar sollte in der `<body>` -Tag, z. B. im Fußzeilenbereich. Die `<meta>` -Tag in der Seite `<head>` Abschnitt.

Ein häufig auftretendes Problem bei Händlern tritt auf, wenn das Sicherheitsscan-Tool nicht in der Lage ist, den Site-Besitz des Händlers zu bestätigen.

Wenn Sie einen Fehler erhalten und Ihre Site nicht für die Prüfung einreichen können, lesen Sie den Abschnitt [Fehlermeldung beim Hinzufügen von Sites zum Sicherheitsscan](/help/troubleshooting/miscellaneous/error-message-adding-site-into-security-scan.md) Artikel zur Fehlerbehebung in unserer Support-Wissensdatenbank.

## Problem: Leere Berichte, die vom Sicherheitsscan-Tool generiert wurden

Sie erhalten leere Scan-Berichte vom Sicherheitsscan-Tool oder erhalten nur Berichte, die nur einen Fehler wie *Das Sicherheitstool konnte die Basis-URL nicht erreichen* oder *Die Magento-Installation wird unter der angegebenen URL nicht gefunden.*.

### Lösung

1. Stellen Sie sicher, dass 52.87.98.44, 34.196.167.176 und 3.218.25.102 IPs bei 80 und 443 Ports nicht blockiert werden.
1. Überprüfen Sie die gesendete URL auf Umleitungen (z. B. `https://mystore.com` umleitet auf `https://www.mystore.com` oder umgekehrt oder leitet zu anderen Domänennamen um).
1. Untersuchen Sie WAF-/Webserver-Zugriffsprotokolle auf abgelehnte/nicht erfüllte Anfragen. HTTP 403 `Forbidden` und HTTP 500 `Internal server error` sind die häufigsten Serverantworten, die die Erstellung leerer Berichte verursachen. Hier ist ein Beispiel für einen Bestätigungscode, der Anforderungen von Benutzeragenten blockiert:

```code block
if(req.http.user-agent ~ "(Chrome|Firefox)/[1-7][0-9]" && client.ip !~ useragent_allowlist)

{   error 403;   }
```

Sie können auch [Der Bericht zum Sicherheitsscan-Tool ist leer](/help/troubleshooting/miscellaneous/the-security-scan-tool-report-is-blank.md) in unserer Support-Wissensdatenbank für weitere Informationen.

## Problem: Das Sicherheitsproblem wurde behoben, wurde aber beim Scannen weiterhin als gefährdet angezeigt

Sie haben ein Sicherheitsproblem behoben und erwarten, dass der Sicherheitsscan zeigt, dass Sie nicht mehr anfällig für das neu gelöste Problem sind. Stattdessen werden Sie in dem vom Sicherheitsscan erstellten Bericht weiterhin als anfällig für das Sicherheitsproblem gemeldet.

### Ursache

Die Metadaten der Cloud-Instanz werden nur für `active` und `live` Cloud-Projekte und sind KEIN Echtzeit-Prozess.

Das Skript zur Statistikerfassung wird einmal täglich ausgeführt. Danach muss das Sicherheitsscan-Tool die neuen Daten später abrufen.

Die erwartete Latenz des Synchronisierungszyklus beträgt bis zu eine Woche und dauert mindestens 24 Stunden.

Die folgenden Status können in Prüfungen angezeigt werden:

1. **Pass**: Das Sicherheitsscan-Tool hat Ihre aktualisierten Daten gescannt und die Änderungen genehmigt.
1. **unbekannt**: Das Sicherheitsscan-Tool hat noch keine Daten zu Ihrer Domäne. Warten Sie auf den nächsten Synchronisierungszyklus.
1. **Fail**: Wenn der Status &quot;Fail&quot;anzeigt, müssen Sie das Problem beheben (2FA aktivieren, Admin-URL ändern usw.) und warten Sie auf den nächsten Synchronisierungszyklus.

Wenn 24 Stunden vergangen sind, seit die Änderungen an der Instanz vorgenommen wurden, und sie nicht im Bericht Sicherheitsscan enthalten sind, können Sie [Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). Geben Sie die Store-URL beim Senden des Tickets an.

## BotNet-Fehler bei Verdacht

Sie erhalten eine Benachrichtigung bezüglich des Fehlers &quot;BotNet Suspect&quot;.

### Ursache

1. Der Name der Store-Domäne wurde 2019 in die &quot;Liste potenzieller BotNet-Teilnehmer&quot;aufgenommen und die Admin-Bedienfeld-, Download- oder RSS-Funktionen wurden öffentlich verfügbar gemacht. Die URL wurde in den CC-Skimming-Foren erwähnt.
1. Der Warnhinweis kann durch Anzeichen von Store-Kompromissen und/oder Malware wie JavaScript auf der Seite verursacht werden.
1. Es handelt sich dabei nicht unbedingt um ein laufendes Thema. Wenn der Laden zuvor kompromittiert wurde, kann sein Hostname immer noch als &#39;Opfer&#39;-Name um das dunkle Netz schwimmen.
1. Dies kann auch nicht durch Adobe Commerce, sondern durch einen Systemkompromiss (auf Betriebssystemebene) verursacht werden.

### Lösung

1. Suchen Sie nach den neu erstellten SSH-Konten, Dateisystemänderungen usw.
1. Führen Sie eine Sicherheitsüberprüfung durch.
1. Überprüfen Sie die Adobe Commerce-Version und das Upgrade, insbesondere wenn noch Magento 1 ausgeführt wird, was nicht mehr unterstützt wird.
1. Wenn das Problem weiterhin besteht, [Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) und geben Sie die Store-URL an.

## Problem: Versagen der Kompromittion

Sie erhalten eine Fehlermeldung bezüglich eines Fehlers bei der &quot;Kompromissionsinjektion&quot;.

### Lösung

1. Überprüfen Sie die im Tool-Bericht Sicherheitsscan angegebenen Skripte.
1. Überprüfen Sie den Quelltext der Homepage auf Inline-Skriptinjektionen.
1. Überprüfung der Systemkonfigurationsänderungen, insbesondere benutzerdefinierter `HTML head` und `Miscellaneous HTML` in `footer` -Abschnittswerte.
1. Führen Sie eine Code- und Datenbanküberprüfung auf unbekannte Änderungen und Anzeichen von injizierter Malware durch.

Wenn keiner der oben genannten Punkte hilft, [Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) und geben Sie die Store-URL und die Fehlermeldung aus dem Bericht an.

## Häufig gestellte Fragen

### Wirkt sich die Sicherheitsprüfung auf die Leistung auf meiner Website aus?

Anzahl Der Sicherheits-Scan stellt alle Anfragen einzeln wie ein Benutzer. Aus diesem Grund sollte der Sicherheits-Scan die Leistung der Website nicht beeinträchtigen.

### Wie lange bewahrt Adobe Commerce Sicherheitsscan-Berichte auf?

Sie können die vorherigen 10 Berichte von Ihrem Ende generieren. Wenn ältere Berichte erforderlich sind, wenden Sie sich an den Adobe Commerce-Support. Bis zu einem Jahr zuvor können Sicherheitsüberprüfungsberichte eingeholt werden.

### Welche Informationen sind beim Senden eines Support-Tickets erforderlich?

Geben Sie unbedingt den Domänennamen an.
