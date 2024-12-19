---
title: Handbuch zur Fehlerbehebung beim Adobe Commerce Security Scan Tool
description: Erfahren Sie, wie Sie die verschiedenen Probleme mit dem Security Scan Tool für Adobe Commerce und Magento Open Source beheben können.
exl-id: 35e18a11-bda9-47eb-924a-1095f4f01017
feature: Compliance, Security
role: Developer
source-git-commit: 525352027bfa4a8728bdbbfe61af3dca5dbb18f9
workflow-type: tm+mt
source-wordcount: '889'
ht-degree: 0%

---

# Handbuch zur Fehlerbehebung beim Adobe Commerce Security Scan Tool

Erfahren Sie, wie Sie die verschiedenen Probleme mit dem Security Scan Tool für Adobe Commerce und Magento Open Source beheben können.

## Problem: Die Site kann nicht gesendet werden

Das Security Scan Tool erfordert, dass Sie die Eigentümerschaft Ihrer Website nachweisen, bevor die Domain zum Security Scan Tool hinzugefügt werden kann. Dies kann durch Hinzufügen eines Bestätigungscodes zu Ihrer Site mithilfe eines HTML-Kommentars oder des `<meta>`-Tags erfolgen. Der HTML-Kommentar sollte innerhalb des `<body>`-Tags platziert werden, z. B. im Fußzeilenbereich. Das `<meta>`-Tag sollte im `<head>` der Seite platziert werden.

Ein häufiges Problem, mit dem Händler konfrontiert sind, tritt auf, wenn das Sicherheits-Scan-Tool den Site-Eigentümer des Händlers nicht bestätigen kann.

Wenn Sie einen Fehler erhalten und Ihre Website nicht zur Suche einreichen können, lesen Sie den Artikel [Fehlermeldung beim Hinzufügen von Websites zur Sicherheits](/help/troubleshooting/miscellaneous/error-message-adding-site-into-security-scan.md)Suche) in unserer Support-Wissensdatenbank.

## Problem: Leere, vom Sicherheits-Scan-Tool generierte Berichte

Sie erhalten leere Suchberichte vom Security Scan Tool oder Berichte, die nur einen einzigen Fehler enthalten, wie *Das Security Tool konnte die Basis-URL nicht erreichen* oder *die Magento-Installation wurde auf der angegebenen URL nicht gefunden*.

### Lösung

1. Stellen Sie sicher, dass 52.87.98.44-, 34.196.167.176- und 3.218.25.102-IPs nicht an den Ports 80 und 443 blockiert sind.
1. Überprüfen Sie die gesendete URL auf Weiterleitungen (z. B. `https://mystore.com` Weiterleitungen zu `https://www.mystore.com` oder umgekehrt oder Weiterleitungen zu anderen Domain-Namen).
1. Untersuchen Sie die WAF-/Webserver-Zugriffsprotokolle auf abgelehnte/nicht erfüllte Anfragen. HTTP 403 `Forbidden` und HTTP 500 `Internal server error` sind die gebräuchlichen Serverantworten, die die Erstellung leerer Berichte verursachen. Im Folgenden finden Sie ein Beispiel für den Bestätigungs-Code, der Anfragen von Benutzeragenten blockiert:

```code block
if(req.http.user-agent ~ "(Chrome|Firefox)/[1-7][0-9]" && client.ip !~ useragent_allowlist)

{   error 403;   }
```

Weitere Informationen finden Sie auch [ Artikel in unserer Support](/help/troubleshooting/miscellaneous/the-security-scan-tool-report-is-blank.md)Wissensdatenbank unter Der Bericht zum Security Scan Tool ist leer.

## Problem: Das Sicherheitsproblem wurde behoben, wird aber in der Suche weiterhin als verwundbar angezeigt

Sie haben ein Sicherheitsproblem behoben und erwarten, dass die Sicherheitsprüfung zeigt, dass Sie für das neu behobene Problem nicht mehr anfällig sind. Stattdessen werden Sie in dem Bericht, der durch die Sicherheitsprüfung generiert wurde, weiterhin als anfällig für das Sicherheitsproblem gemeldet.

### Ursache

Die Metadaten der Cloud-Instanz werden nur für `active` und `live` Cloud-Projekte erfasst und sind KEIN Echtzeit-Prozess.

Das Statistiksammlungsskript wird einmal täglich ausgeführt, dann muss das Security Scan Tool die neuen Daten später abholen.

Die erwartete Latenz des Synchronisierungszyklus beträgt bis zu einer Woche und dauert mindestens 24 Stunden.

Die folgenden Status können bei Prüfungen angezeigt werden:

1. **Pass**: Das Security Scan Tool hat Ihre aktualisierten Daten überprüft und die Änderungen genehmigt.
1. **Unbekannt**: Das Security Scan Tool enthält noch keine Daten zu Ihrer Domain. Warten Sie auf den nächsten Synchronisierungszyklus.
1. **Fehlgeschlagen**: Wenn der Status „Fehlgeschlagen“ anzeigt, müssen Sie das Problem beheben (2FA aktivieren, Admin-URL ändern usw.) und auf den nächsten Synchronisierungszyklus warten.

Wenn seit der Vornahme der Änderungen an der Instanz 24 Stunden vergangen sind und sie nicht im Bericht zur Sicherheitsprüfung angezeigt werden, können [ ein Support-Ticket ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). Geben Sie beim Senden des Tickets die Store-URL an.

## BotNet-Verdächtiger Fehler

Sie erhalten eine Benachrichtigung über den Fehler „BotNet-Verdächtiger“.

### Ursache

1. Der Domain-Name des Stores wurde bereits 2019 in eine „Liste potenzieller BotNet-Teilnehmer“ aufgenommen, und das Admin-Bedienfeld, der Downloader oder die RSS-Funktion wurden öffentlich zugänglich gemacht, und/oder seine URL wurde in den CC-Skimming-Foren erwähnt.
1. Der Warnhinweis kann durch Anzeichen einer Geschäftsgefährdung und/oder Malware verursacht werden, wie z. B. JavaScript auf der Seite.
1. Es handelt sich nicht unbedingt um ein laufendes Problem. Wenn der Store zuvor kompromittiert wurde, kann sein Hostname weiterhin als „Opfername“ im dunklen Web schwebend sein.
1. Sie kann auch nicht durch Adobe Commerce verursacht werden, sondern durch einen Systemkompromiss (auf Betriebssystemebene).

### Lösung

1. Überprüfen Sie die neu erstellten SSH-Konten, Dateisystemänderungen usw.
1. Führen Sie eine Sicherheitsüberprüfung durch.
1. Überprüfen Sie die Adobe Commerce-Version und das Upgrade, insbesondere wenn weiterhin Magento 1 ausgeführt wird, was nicht mehr unterstützt wird.
1. Wenn das Problem weiterhin besteht, [ Sie ein Support-Ticket ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) und geben Sie die Store-URL an.

## Problem: Kompromisseinspritzung fehlgeschlagen

Sie erhalten eine Fehlermeldung bezüglich eines „Compromising Injection“-Fehlers.

### Lösung

1. Überprüfen Sie die im Bericht des Security Scan Tools angegebenen Skripte.
1. Überprüfen Sie den Quelltext der Startseite für Inline-Skript-Injektionen.
1. Führen Sie eine Überprüfung der Systemkonfigurationsänderungen durch, insbesondere der benutzerdefinierten `HTML head` und `Miscellaneous HTML` in `footer` Abschnittswerten.
1. Code- und Datenbanküberprüfung auf unbekannte Änderungen und Anzeichen von injizierter Malware durchführen.

Wenn keiner der oben genannten Punkte hilft, [senden Sie ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) und geben Sie die Store-URL und die Fehlermeldung aus dem Bericht an.

## Häufig gestellte Fragen

### Beeinträchtigt die Sicherheitsüberprüfung die Leistung meiner Website?

Anzahl Bei der Sicherheitsprüfung werden alle Anfragen einzeln, wie bei einem einzelnen Benutzer, durchgeführt. Aus diesem Grund sollte die Sicherheitsprüfung die Leistung der Website nicht beeinträchtigen.

### Wie lange bewahrt Adobe Commerce Berichte zur Sicherheitsprüfung auf?

Sie können die 10 vorherigen Berichte von Ihrem Ende aus generieren. Wenn ältere Berichte erforderlich sind, wenden Sie sich an den Adobe Commerce-Support.

### Welche Informationen werden beim Einreichen eines Support-Tickets benötigt?

Stellen Sie sicher, dass Sie den Domain-Namen angeben.

### Was passiert, wenn ich meinen Speicher aus dem Scan-Tool entferne?

Wenn Sie die Store-Übermittlung löschen, werden alle damit verbundenen Daten einschließlich der Scanberichte gelöscht. Dieser Vorgang kann nicht rückgängig gemacht werden. Durch die Übermittlung der Store-Domain nach dem Löschen wird eine NEUE Übermittlung erstellt.
