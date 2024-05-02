---
title: Aktualisierung der Adobe Commerce Support-Ticketlebenszyklus-Richtlinie
description: Dieser Artikel enthält Informationen zur Aktualisierung der Adobe Commerce Support-Ticketlebenszyklusrichtlinien.
exl-id: c3fbcb4a-107f-48b3-afed-b9a0c5d0425c
source-git-commit: c1c2bd29e14f4cbfffb235801e95ec7cbb7c7a55
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 1%

---

# Aktualisierung der Adobe Commerce Support-Ticketlebenszyklus-Richtlinie

Dieser Artikel enthält Informationen zur Aktualisierung der Adobe Commerce Support-Ticketlebenszyklusrichtlinien.

Die folgende Tabelle zeigt die aktualisierten Szenarien. Details zu den einzelnen Szenarien finden Sie im folgenden Abschnitt.

<table>
 <tbody>
 <tr>
 <td class="wysiwyg-text-align-center"> </td>
 <td class="wysiwyg-text-align-center"><strong>Ticketstatus</strong></td>
 <td class="wysiwyg-text-align-center"><strong>Tage bis "Gelöst"</strong></td>
 <td class="wysiwyg-text-align-center"><strong>Tage bis "geschlossen"</strong></td>
 <td class="wysiwyg-text-align-center"><strong>Benachrichtigungszeitpunkt</strong></td>
 </tr>
 <tr>
 <td class="wysiwyg-text-align-left"><strong>Ingenieur bietet Lösung</strong></td>
 <td class="wysiwyg-text-align-center">"Warten auf Ihre Antwort"</td>
 <td class="wysiwyg-text-align-center">3</td>
 <td class="wysiwyg-text-align-center">6</td>
 <td class="wysiwyg-text-align-center">Tage 3 und 6</td>
 </tr>
 <tr>
 <td class="wysiwyg-text-align-left"><strong>Auf Informationen vom Kunden warten</strong></td>
 <td class="wysiwyg-text-align-center">"Warten auf Ihre Antwort"</td>
 <td class="wysiwyg-text-align-center">Nicht zutreffend</td>
 <td class="wysiwyg-text-align-center">6</td>
 <td class="wysiwyg-text-align-center">Tage 1, 3 und 6</td>
 </tr>
 <tr>
 <td class="wysiwyg-text-align-left"><strong>Der Kunde setzt auf "Gelöst"oder fordert den Techniker auf, auf "Gelöst"festzulegen</strong></td>
 <td class="wysiwyg-text-align-center">"Gelöst"</td>
 <td class="wysiwyg-text-align-center">Sofort</td>
 <td class="wysiwyg-text-align-center">1</td>
 <td class="wysiwyg-text-align-center">Tag 1</td>
 </tr>
 </tbody>
 </table>

## Szenarien im Detail

### Wenn ein Ingenieur eine Lösung bereitstellt

1. Sobald einem Kunden eine Lösung bereitgestellt wurde, setzt der Techniker den Ticketstatus auf &quot;Warten auf Ihre Antwort&quot;.
1. Wenn der Kunde 3 Tage lang keine Antwort erhält, nachdem der Status in &quot;Warten auf Ihre Antwort&quot;geändert wurde, wird das Ticket in &quot;Gelöst&quot;verschoben und der Kunde wird benachrichtigt.
1. Wenn der Kunde 6 Tage lang keine Antwort erhält, nachdem der Status in &quot;Warten auf Ihre Antwort&quot;geändert wurde, wird das Ticket geschlossen und der Kunde wird benachrichtigt.

### Wenn von einem Kunden zusätzliche Informationen benötigt werden

1. Wenn eine Aktualisierung des Kunden erforderlich ist, setzt der Techniker das Ticket auf &quot;Warten auf Ihre Antwort&quot;.
1. An den Tagen 1 und 3 werden dem Kunden Benachrichtigungen gesendet, in denen er um Nachbearbeitung ersucht.
1. Wenn der Kunde 6 Tage lang keine Antwort erhält, nachdem der Status in &quot;Warten auf Ihre Antwort&quot;geändert wurde, wird das Ticket geschlossen und der Kunde wird benachrichtigt.

### Ticket, das von einem Kunden auf &quot;gelöst&quot;gesetzt wurde

Wenn ein Ticket von einem Kunden auf &quot;Gelöst&quot;gesetzt wird, wird es an einem Tag geschlossen und der Kunde wird benachrichtigt.

### Der Kunde weist den Support an, das Ticket zu schließen

Wenn ein Kunde den Adobe Commerce-Support anweist, das Ticket zu schließen, wird es innerhalb eines Tages geschlossen und der Kunde wird benachrichtigt.

## Verwandtes Lesen

* [Support-Ticket senden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)
* [Der Link &quot;Ticket senden&quot;wird nicht auf der Startseite des Adobe Commerce Help Center angezeigt](/help/help-center-guide/help-center/magento-help-center-user-guide.md#no-submit-link)
* [Formular für die Übermittlung von Tickets: Der Händler wird nicht in der Dropdown-Liste &quot;Organisation&quot;angezeigt](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed)
