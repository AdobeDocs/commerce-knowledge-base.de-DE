---
title: Benutzerhandbuch zum Adobe Commerce Help Center
description: Erfahren Sie, wie Sie ein Support-Ticket an das Adobe Commerce Help Center senden, freigegebenen Zugriff auf Konten gewähren und in der Adobe Commerce Knowledge Base navigieren.
exl-id: 9eb4814f-c9c4-4dd0-b68a-87d712898aa5
feature: Support, Roles/Permissions, Tools and External Services, Admin Workspace, Iaas, Marketing Tools
source-git-commit: 3e773131f6f44436fc533f74474efbe8597abb5f
workflow-type: tm+mt
source-wordcount: '4988'
ht-degree: 0%

---

# Benutzerhandbuch zum Adobe Commerce Help Center

In diesem Handbuch erfahren Sie, wie Sie ein Support-Ticket an das [Adobe Commerce Help Center](https://support.magento.com/hc/en-us) senden und freigegebenen Zugriff auf die Adobe Commerce-Konten gewähren.

>[!NOTE]
>
>Der Adobe Commerce-Support wechselt vom Adobe Commerce Help Center zum Experience League. Wenn Sie darüber informiert wurden, dass Sie Zugriff haben, verwenden Sie den Experience League-Formularfluss, der [hier](#what-is-experience-support) beschrieben wird. Wenn Sie nicht benachrichtigt wurden, verwenden Sie weiterhin den [Fallfluss im Adobe Commerce Help Center](#what-is-adobe-commerce-help-center).

>[!NOTE]
>
>Der Knowledgebase-Teil des Adobe Commerce Help Center wurde in das Adobe Experience League-Portal migriert. Wenn Sie ein Support-Ticket erstellen, werden Ihnen neben anderen relevanten Adobe Commerce-Dokumentationen aus Adobe Experience League entsprechende Knowledge Base-Artikel vorgeschlagen.

**Wichtige Aktualisierung:** 8. Juli 2024

**[WAS UNTERSTÜTZT EXPERIENCE LEAGUE?](#what-is-experience-support)**

**[UNTERSTÜTZUNGSFÄLLE](#support-cases)**

* [Anmelden bei Experience League-Support](#sign-in-experience-support)
* [Support-Fall einreichen](#submit-case)

   * [Startseite von Adobe Experience League](#experience-league-start-page)
   * [Adobe Commerce-Kontoseite](#submit-case-adobe-commerce-account-page)
   * [*Bitte überprüfen Sie Ihre E-Mail-Adresse*](#verify-email-address-error)

* [Support-Fälle verfolgen](#track-support-cases)
* [Kommentare in Ihrem Fall](#comments-in-your-case)
* [Schließen Sie den Fall.](#close-case)

**[WAS IST DAS ADOBE COMMERCE-HILFEZENTRUM?](#what-is-adobe-commerce-help-center)**

**[UNTERSTÜTZUNGS-TICKETS](#support-tickets)**

* [Bei Help Center anmelden](#login)
* [Support-Ticket senden](#submit-ticket)

   * [Startseite von Help Center](#submit-ticket-help-center-start-page)
   * [Magento-Kontoseite](#submit-ticket-magento-account-page)
   * [Cloud-Konsole](#submit-ticket-magento-cloud-account-page)
   * [Informationen zum Support-Ticket](#info-in-support-ticket)
   * [Der Link &quot;Ticket senden&quot;wird nicht auf der Startseite des Adobe Commerce Help Center angezeigt](#no-submit-link)
   * [*&quot;Bitte überprüfen Sie Ihre E-Mail-Adresse&quot;*](#verify-email-address)
   * [Formular für die Übermittlung von Tickets: Der Händler wird nicht in der Dropdown-Liste &quot;Organisation&quot;angezeigt](#merchant-not-displayed)

* [Tickets verfolgen](#track-tickets)
* [Adobe Commerce P1-Hotline (Anmeldung erforderlich)](#P1-hotline)
* [Betriebsmodell für die gemeinsame Verantwortung von Adobe Commerce (Anmeldung erforderlich)](#shared-responsibility-operational-model)
* [Erläuterung der Support-Ticketfelder](#ticket-fields-explained)
* [Ticket-Status: Verarbeitung Ihrer Anfragen](#ticket-status)
* [Unterhaltung in Ihrem Ticket](#conversation-in-ticket)
* [Ticket lösen](#resolve-ticket)
* [Öffnen Sie ein Folgenachticket.](#follow-up)

**[FREIGEGEBENER ZUGRIFF: BERECHTIGUNGEN FÜR ANDERE BENUTZER FÜR DEN ZUGRIFF AUF IHR KONTO GEWÄHREN](#shared-access)**

* [Wer kann freigegebenen Zugriff gewähren?](#who-can-provide-shared-access)
* [Freigegebenen Zugriff gewähren](#provide-shared-access)
* [Freigegebenen Zugriff sperren (löschen)](#revoke-shared-access)

   * [Wie kann ich Benutzer löschen, denen der gemeinsame Zugriff über ein Cloud-Projekt gewährt wurde?](#remove-cloud-shared-access-users)

* [Zugriff auf freigegebene Konten (Konten wechseln)](#switch-accounts)
* [Fehlerbehebung bei freigegebenen Zugriffen](#troubleshooting-shared-access)

**[FAQ ZUR ABRECHNUNG FÜR ADOBE COMMERCE](#billing-faq)**

**[MAGENTO U IST JETZT TEIL VON ADOBE DIGITAL LEARNING SERVICES](#magento-u)**

>[!NOTE]
>
>Wenn Sie nicht benachrichtigt wurden, verwenden Sie weiterhin den Fallfluss [Adobe Commerce Help Center Help Center](#what-is-adobe-commerce-help-center). Wenn Sie darüber informiert wurden, dass Sie sich in der Kohorte mit Zugriff befinden, folgen Sie dem Experience League-Formularfluss, der [unter ](#what-is-experience-league-support) beschrieben wird.

## WAS UNTERSTÜTZT EXPERIENCE LEAGUE? {#what-is-experience-support}

Experience League Support ist ein Support-Portal für Adobe, über das qualifizierte Adobe Commerce-Kunden Support-Tickets einreichen und verwalten können. Dort können Sie auch Artikel zur Fehlerbehebung lesen.

## UNTERSTÜTZUNGSFÄLLE {#support-cases}

Die Support-Fallverwaltung von Adobe Experience League ermöglicht die Zusammenarbeit mit Support-Experten, um spezifische Probleme bei der Verwendung von Adobe-Produkten, einschließlich Adobe Commerce, für alle Adobe Commerce-Produkte unter Vertrag zu beheben.

## BEI EXPERIENCE LEAGUE-SUPPORT ANMELDEN {#sign-in-experience-support}

Durch die Anmeldung können Sie Fragen von Agenten zu Support-Tickets senden, aktualisieren und beantworten.

Gehen Sie wie folgt vor, um sich beim Adobe Experience League-Support anzumelden:

1. Navigieren Sie zu [experienceleague.adobe.com](https://experienceleague.adobe.com/).
1. Melden Sie sich mit Ihren Adobe-Anmeldedaten an.

![Sign-in-experience-league](assets/experience_league_sign_in.png)

### Support-Fall einreichen {#support-case}

Nach der erfolgreichen Anmeldung können Sie über die Adobe Experience League-Startseite, Ihre Adobe Commerce-Kontoseite und Ihre Adobe Commerce Cloud-Kontoseite einen Support-Fall einreichen.

* Wenn Sie der Kontoinhaber sind, führen Sie die folgenden Schritte aus.
* Wenn Sie Benutzer von Shared Access sind, müssen Sie zunächst zwischen Konten wechseln. Siehe [Zugriff auf freigegebene Konten (Wechsel der Konten)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#switch-accounts), und dann können Sie mit den folgenden Schritten fortfahren.

#### Startseite von Adobe Experience League {#experience-league-start-page}

Gehen Sie wie folgt vor, um einen neuen Support-Fall über die Startseite von Adobe Experience League einzureichen:

>[!NOTE]
>
>1. Wenn Sie mehreren Organisationen angehören, müssen Sie die entsprechende Organisation aus der Dropdown-Liste auswählen.
>1. Um einen Fall einzureichen, müssen Sie berechtigt sein, Unterstützung zu erhalten. Ist dies nicht der Fall, wird oben auf der Seite eine Leiste angezeigt, die Sie darüber informiert, dass Sie kein Benutzer mit Supportberechtigung in der Organisation sind.

1. Klicken Sie in der Kopfzeile auf **Support** . Dadurch wird die Startseite des Supports geöffnet.

   ![open-support-page](assets/click_support.png)

1. Um den Aufnahmeprozess zu starten, klicken Sie im linken Menü auf **[!UICONTROL Open Ticket]** oder auf **[!UICONTROL Get Started]** auf der Karte *[!UICONTROL Open a support ticket]*.

   ![open-support-case](assets/open_support_case.png)

1. Wählen Sie ein Produkt aus dem Dropdown-Menü aus und geben Sie einen Falltitel und eine Beschreibung ein.

   ![select_product](assets/support_case_product.png)

1. Adobe Experience League schlägt Artikel und Best Practices vor, die Ihnen bei der Lösung Ihres Problems helfen können. Wenn Sie weiterhin direkten Support benötigen, müssen Sie einige zusätzliche Informationen bereitstellen, bevor Sie Ihren Fall übermitteln.

   ![direct_support_required](assets/direct_support.png)

1. Nachdem Sie alle erforderlichen Informationen ausgefüllt haben, klicken Sie auf **[!UICONTROL Submit case]**.

Sie müssen über ein Konto sowohl auf https://account.adobe.com als auch auf https://account.magento.com verfügen, um sich bei der Experience League anzumelden und einen Support-Fall einzureichen. Sie können erst dann einen Support-Fall einreichen, wenn Sie angemeldet sind.

>[!NOTE]
>
>Wenn Sie bereits über ein Konto bei https://account.magento.com verfügen, sich aber nicht anmelden können, haben Sie sich möglicherweise nicht bei https://account.adobe.com angemeldet, was ab August 2022 erforderlich ist.
>
>So beheben Sie Folgendes:
>1. Erstellen Sie ein Konto unter https://account.adobe.com mit derselben E-Mail-Adresse auf Ihrer MAG-ID.
>1. Gehen Sie zu https://account.magento.com , um Ihre Adobe ID mit der MAG-ID zu verknüpfen.

#### Adobe Commerce-Kontoseite {#submit-case-adobe-commerce-account-page}

Gehen Sie wie folgt vor, um über Ihre Adobe Commerce-Kontoseite ein neues Support-Ticket zu senden:

1. Melden Sie sich bei Ihrem Adobe Commerce-Konto an. Siehe [Detaillierte Anweisungen](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-create.html?lang=en#create-a-commerce-account) in unserem Benutzerhandbuch.
1. Klicken Sie auf die Registerkarte **Support** .

   ![magento_account_support_tab](assets/magento_account_support_tab.png){width="800"}

1. Die Adobe Experience League-Support-Seite wird für Sie geladen.
1. Wählen Sie im linken Menü **[!UICONTROL Open Ticket]** aus.
1. Füllen Sie die Felder aus.
1. Klicken Sie auf **Senden**.

#### *Bitte überprüfen Sie den Fehler Ihrer E-Mail-Adresse* auf der Adobe Commerce-Kontoseite. {#verify-email-address-error}

Sie können kein Support-Ticket senden, wenn Sie den Fehler Ihre E-Mail-Adresse überprüfen erhalten, der dem auf der Seite [Adobe Commerce-Konto](https://account.magento.com/) unten stehenden ähnelt.

![Verify_Email_Address_Error](assets/Verify_Email_Address_Error.png)


### Support-Fälle verfolgen {#track-support-case}

Folgende Support-Fälle stehen Ihnen zur Verfügung:

* persönlich eingereicht haben.
* wurden über einen CC (CO2-Kopie) als Beobachter hinzugefügt.

#### Anzeigen von Fällen

Sie können Ihre Fälle anzeigen, indem Sie im Menü auf der linken Seite auf **[!UICONTROL My Cases]** klicken.

![view-support-cases](assets/view_support_cases.png)

#### Suchen nach Fällen

Um Fälle zu finden, geben Sie Ihre Suchabfrage in das Feld *[!UICONTROL Search]* ein und drücken Sie auf der Tastatur die Taste *enter* .

![Suchfälle](assets/search_cases.png)

#### Eskalieren Ihrer Fälle

Wenn Sie der Meinung sind, dass ein Fall weitere Aufmerksamkeit erfordert und unsere anfängliche Reaktionszeit verstrichen ist, können Sie den Fall eskalieren. Gehen Sie dazu folgendermaßen vor:

1. Klicken Sie rechts unten im Bedienfeld *[!UICONTROL Case Detail]* auf **[!UICONTROL Escalate to management]** .

   ![Eskalate-to-Management](assets/escalate_to_management.png)

1. Nach dem Klicken wird ein Popup-Formular angezeigt. Füllen Sie das Formular aus und klicken Sie dann auf **[!UICONTROL Escalate]**.

   ![confirm-escalation](assets/confirm_escalation.png)

   *Eskalationsgründe können* sein: Kommunikationsfähigkeiten von Agenten, technisches Wissen von Agenten, Warten auf Callback/Aktualisierung, Änderung der Dringlichkeit von Problemen, Lösung entsprach nicht den Erwartungen oder Zeit bis zur Lösung.

#### Hinzufügen eines Beobachters zu Supportfällen

Sie können Beobachter hinzufügen, um Fälle zu unterstützen, die von Mitgliedern Ihres Unternehmens eingereicht werden. Überwacher erhalten E-Mail-Benachrichtigungen, wenn neue Fälle gesendet oder bestehende Fälle aktualisiert werden.

1. Um einen Watcher zu einer vorhandenen Groß-/Kleinschreibung hinzuzufügen, öffnen Sie die Groß-/Kleinschreibung und klicken Sie auf das Stiftsymbol neben &quot;Watchers&quot;im Bereich &quot;Case Details&quot;auf der rechten Seite des Bildschirms.

   ![add-watchers](assets/add_watchers.png)

1. Nachdem Sie auf den Stift geklickt haben, können Sie der Liste Beobachter hinzufügen oder daraus entfernen.

   ![update-watchers](assets/update_watchers.png)

### Kommentare in Ihrem Fall {#comments-in-your-case}

Kommentare in Ihrem Fall enthalten alle Kommentare, die von Ihnen oder dem Adobe Commerce-Supportteam geschrieben wurden. Kommentare werden von der neuesten (oben) zur frühesten (unten) angezeigt.
Gehen Sie wie folgt vor, um einen Kommentar hinzuzufügen:

1. Scrollen Sie zum unteren Ende Ihres Tickets.
1. Schreiben Sie Ihren Kommentar in das Feld **[!UICONTROL Comments]** und klicken Sie auf **[!UICONTROL Add comments]**.

![add-comments](assets/add_comments.png)

### Schließen Sie den Fall. {#close-case}

Um den Fall zu schließen, klicken Sie unten rechts im Bedienfeld *[!UICONTROL Case Detail]* auf **[!UICONTROL Close case]** .

![close-case](assets/close_case.png)

>[!NOTE]
>
>Fahren Sie mit dem Formularfluss &quot;Adobe Commerce Help Center&quot;[unter](#what-is-adobe-commerce-help-center) für die Übermittlung und Verwaltung von Tickets fort, es sei denn, Sie wurden darüber informiert, dass Sie sich in der Kohorte befinden und Zugriff auf den Formularfluss &quot;Experience League Case&quot;erhalten, der [hier](#what-is-experience-league-support) beschrieben ist.

## WAS IST ADOBE COMMERCE HELP CENTER? {#what-is-adobe-commerce-help-center}

Das [Adobe Commerce Help Center](https://support.magento.com/hc/en-us) ist ein Support-Portal für Adobe Commerce, in dem qualifizierte Kunden Support-Tickets einreichen und verwalten können. Dort können Sie auch Artikel zur Fehlerbehebung lesen.

## SUPPORT-TICKETS {#support-tickets}

Das Adobe Commerce Ticketing System ermöglicht die Arbeit mit Support-Tickets, um die Probleme zu beheben, die bei der Arbeit mit Adobe Commerce auftreten - für alle Adobe Commerce-Produkte.

## BEI HELFE CENTER ANMELDEN {#login}

Durch die Anmeldung können Sie Fragen von Agenten zu Support-Tickets senden, aktualisieren und beantworten.

Gehen Sie wie folgt vor, um sich beim Adobe Commerce Help Center anzumelden:

1. Rufen Sie das Hilfezentrum unter <https://support.magento.com> auf.
1. Klicken Sie oben rechts auf **Anmelden** .

Melden Sie sich mit Ihren Magento-Kontoanmeldeinformationen an. Weitere Informationen finden Sie unter [Ihr Magento-Konto](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-create.html) in unserem Benutzerhandbuch.

### <strong>Senden eines Support-Tickets</strong> {#submit-ticket}

Nach der erfolgreichen Anmeldung können Sie ein Support-Ticket über die Startseite des Help Center, Ihre Magento-Kontoseite und Ihre Magento Cloud-Kontoseite senden.

* Wenn Sie der **Kontoinhaber** sind, führen Sie die folgenden Schritte aus.
* Wenn Sie Benutzer von &quot;**Shared Access&quot;sind, müssen Sie zuerst die Konten &quot;** [Auf das freigegebene Konto zugreifen (Konten wechseln)&quot;](#switch-accounts)&quot;wechseln. Anschließend können Sie mit den folgenden Schritten fortfahren.

#### Startseite von Help Center {#submit-ticket-help-center-start-page}

Gehen Sie wie folgt vor, um über die Startseite des Adobe Commerce Help Center ein neues Support-Ticket zu senden:

1. Wechseln Sie zu [Adobe Commerce Help Center](https://support.magento.com/hc/en-us).
1. Klicken Sie oben rechts auf **Ticket senden** .

   ![submit-a-ticket](assets/submit-a-ticket-4.png){width="800"}

1. Füllen Sie die Felder aus.
1. Klicken Sie auf **Senden**.

Sie *müssen über ein Konto sowohl auf https://account.adobe.com als auch auf https://account.magento.com verfügen und sich dann mit Ihrem Adobe Commerce-Konto beim Help Center anmelden, um ein Support-Ticket zu senden.* Bis Sie angemeldet sind, wird [die Schaltfläche **Ticket senden** nicht angezeigt](#no-submit-link).

>[!NOTE]
>
>Wenn Sie bereits über ein Konto unter https://account.magento.com verfügen, sich aber nicht anmelden können, haben Sie sich möglicherweise nicht bei https://account.adobe.com angemeldet, was ab August 2022 erforderlich ist.
>
>So beheben Sie Folgendes:
>
>1. Erstellen Sie ein Konto unter https://account.adobe.com mit derselben E-Mail-Adresse auf Ihrer MAG-ID.
>1. Gehen Sie zu https://account.magento.com , um Ihre Adobe ID mit der MAG-ID zu verknüpfen.


#### Magento-Kontoseite {#submit-ticket-magento-account-page}

Gehen Sie wie folgt vor, um über Ihre Magento-Kontoseite ein neues Support-Ticket zu senden:

1. Melden Sie sich bei Ihrem Magento-Konto an. Siehe [Detaillierte Anweisungen](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-create.html?lang=en#create-a-commerce-account) in unserem Benutzerhandbuch.
1. Klicken Sie auf die Registerkarte **Support** .

   ![magento_account_support_tab](assets/magento_account_support_tab.png){width="800"}

1. Die Startseite von Help Center wird für Sie geladen.
1. Klicken Sie oben rechts auf **Ticket senden** .
1. Füllen Sie die Felder aus.
1. Klicken Sie auf **Senden**.

#### Cloud-Konsole {#submit-ticket-magento-cloud-account-page}

Gehen Sie wie folgt vor, um über die Cloud Console ein neues Support-Ticket zu senden:

1. Melden Sie sich bei der [Cloud-Konsole](https://console.adobecommerce.com) an.
1. Wählen Sie im Benutzermenü **[!UICONTROL Support]** aus.
1. Die Seite **[!UICONTROL My Tickets]** wird geladen.
1. Klicken Sie oben rechts auf **[!UICONTROL Submit a ticket]** .
1. Füllen Sie die Felder aus.
1. Klicken Sie auf **Senden**.
1. Klicken Sie auf **[!UICONTROL Submit]**.

#### Informationen zum Support-Ticket {#info-in-support-ticket}

Die Felder, die mit einem roten Sternchen ( **\*** ) markiert sind, sind erforderlich und müssen ausgefüllt werden. Wenn Sie eines dieser Felder leer lassen, können Sie Ihr Ticket nicht senden.

Weitere Informationen finden Sie unten unter [Ticket-Felder erklärt](#ticket-fields-explained) .

### Der Link &quot;Ticket senden&quot;wird nicht auf der Startseite des Adobe Commerce Help Center angezeigt {#no-submit-link}

#### Problem

Sie greifen auf das Adobe Commerce Help Center zu und möchten eine Support-Anfrage senden, aber der Link **Ticket senden** wird nicht auf der Startseite des Help Center angezeigt.

#### Ursache

Eine der folgenden Ursachen könnte sein:

* Sie haben sich nicht beim Help Center angemeldet.
* Wenn Sie zum ersten Mal freigegebenen Zugriff verwenden, haben Sie nicht die erforderlichen Schritte ausgeführt, um sicherzustellen, dass das Adobe Commerce Help Center ordnungsgemäß über den SSO-Aufruf von Magento.com konfiguriert ist.
* Ihr Konto hat keinen Anspruch auf Adobe Commerce-Support (Sie sind beispielsweise kein zahlender Commerce-Kunde oder Open Source-Kunde).

#### Lösung

[Melden Sie sich im Hilfezentrum an](/help/help-center-guide/help-center/magento-help-center-user-guide.md#provide-shared-access).

Der Link **Ticket senden** wird nur für Kunden angezeigt, deren E-Mail mit einer gültigen Supportvereinbarung verknüpft ist.

#### Freigegebenes Zugriffskonto verwenden

Um das Konto für freigegebenen Zugriff zum Senden von Support-Tickets verwenden zu können, müssen Sie Folgendes ausführen (dies muss nur einmal durchgeführt werden):

1. Nachdem Sie den [freigegebenen Zugriff](https://support.magento.com/hc/en-us/articles/360052444712#who-can-provide-shared-access) erhalten haben, melden Sie sich bei Ihrem [Magento-Konto auf der magento.com Website](https://account.magento.com/) an.
1. Wählen Sie im Dropdown-Feld **Konten wechseln** oben rechts das freigegebene Zugriffskonto aus.
1. Klicken Sie im linken Bereich auf die Registerkarte **Support** . Dadurch wird sichergestellt, dass das Adobe Commerce Help Center über den SSO-Aufruf von Magento.com zum Adobe Commerce Help Center ordnungsgemäß konfiguriert ist.

#### Der Link **Ticket senden** wird immer noch nicht angezeigt

Wenn Sie unter der Dropdownliste **Konten wechseln** nicht über **gemeinsame Konten** verfügen, aber für einen Client arbeiten, der über eine Adobe Commerce-Lizenz verfügt, bitten Sie diesen, Ihnen den gemeinsamen Zugriff zu gewähren. Weitere Informationen finden Sie unter [Freigegebenen Zugriff auf Magento-Konto bereitstellen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#provide-shared-access).

Wenn Sie Adobe Commerce-Lizenzinhaber sind, vergewissern Sie sich bitte, dass Sie keine Rechnung mit dem Status **Ausstehende Zahlung** haben. Förderansprüche werden automatisch entsprechend dem Status der Rechnungszahlung gewährt oder widerrufen.

<span class="wysiwyg-underline">Überprüfen des Zahlungsstatus</span>:

1. Melden Sie sich bei [magento.com](https://support.magento.com/) an.
1. Klicken Sie links auf **Rechnungsverlauf** .
1. Wenn Sie **do** eine Rechnung mit dem Status **Ausstehende Zahlung** haben, wenden Sie sich an **Ihr Adobe Account Team**, um das Zahlungsproblem zu beheben.

Wir unterstützen nur Lizenzinhaber und Konten von Adobe Commerce, die über einen gemeinsamen Zugriff auf ein Konto mit einer Adobe Commerce-Lizenz verfügen. Wenn Sie Unterstützung für die Bearbeitung der Magento Open Source benötigen, nutzen Sie diese technischen Ressourcen zur Selbsthilfe:

* [Adobe Commerce Help Center](https://support.magento.com/)
* [Adobe Commerce-Entwicklerdokumentation](https://developer.adobe.com/commerce/docs/)
* [Adobe Commerce-Dokumentationsressourcen](https://experienceleague.adobe.com/docs/commerce.html)
* [Magento-Foren](https://community.magento.com/?_ga=2.99592990.1084044056.1559046120-720752292.1551793747)

Wenn Sie Probleme haben, sich bei Ihrem Konto anzumelden oder der Meinung sind, dass der Freigabezugriff ordnungsgemäß eingerichtet wurde, Sie aber trotzdem die Schaltfläche &quot;**Ticket senden**&quot; nicht sehen können, wenden Sie sich bitte per E-Mail an &quot;[Anmeldungsprobleme beim Help Center](mailto:grp-magento-helpcenterloginissues@adobe.com)&quot;. Wir werden Ihre Kontoeinstellungen und die Berechtigungen gerne überprüfen.

>[!NOTE]
>
>Wenn beim Zugriff auf Ihr Cloud-Projekt Probleme auftreten, senden Sie das Ticket für dieses Problem über die normalen Kanäle. Senden Sie keine E-Mail, wenn Sie ein Ticket senden können.

### Fehler &quot;Bitte überprüfen Sie Ihre E-Mail-Adresse&quot; auf der Magento-Kontoseite {#verify-email-address}

Sie können kein Support-Ticket senden, wenn Sie den Fehler *Bitte überprüfen Sie Ihre E-Mail-Adresse* ähnlich dem Fehler unten auf der Seite [Magento-Konto](https://account.magento.com/) erhalten.

![Verify_Email_Address_Error](assets/Verify_Email_Address_Error.png){width="800"}

Die Lösung besteht darin, Ihre E-Mail-Adresse zu validieren:

1. Melden Sie sich bei https://account.adobe.com an und fordern Sie bei Bedarf ein Kennwort an.
1. Überprüfen Sie Ihr Adobe-Konto.

>[!NOTE]
>
>Dies gilt nur für den E-Mail-Validierungslink von https://account.magento.com (Magento-Kontoseite).

### Formular für die Übermittlung von Tickets: Der Händler wird nicht in der Dropdown-Liste &quot;Organisation&quot;angezeigt {#merchant-not-displayed}

#### Problem

<span class="wysiwyg-underline">Voraussetzungen</span>: Sie verfügen über ein von einem Händler genehmigtes Konto für den gemeinsamen Zugriff.

<span class="wysiwyg-underline">Zu reproduzierende Schritte</span>:

1. Melden Sie sich über Ihr freigegebenes Konto beim Help Center an.
1. Klicken Sie auf den Link **Ticket senden** . Das Formular für die Übermittlung des Tickets wird geöffnet.
1. Erweitern Sie das Dropdown-Feld **Organisation** , um den Händler auszuwählen.

<span class="wysiwyg-underline">Erwartetes Ergebnis</span>:

Der Händler, der dem freigegebenen Konto entspricht, wird in den Optionen **Organisation** aufgeführt.

<span class="wysiwyg-underline">Tatsächliches Ergebnis</span>:

Der Händler, der dem verwendeten freigegebenen Konto entspricht, ist in den Optionen **Organisation** nicht verfügbar.

#### Lösung

Nachdem Sie vom Händler freigegebenen Zugriff erhalten haben, müssen Sie die folgenden Schritte ausführen (nur einmal):

1. Melden Sie sich bei Ihrem [Magento-Konto auf der magento.com Website](https://account.magento.com/) an.
1. Wählen Sie im Dropdown-Feld **Konten wechseln** oben rechts das freigegebene Zugriffskonto aus.
1. Klicken Sie im linken Bereich auf die Registerkarte **Support** . Dadurch wird sichergestellt, dass das Adobe Commerce Help Center über den SSO-Aufruf von Magento.com zum Adobe Commerce Help Center ordnungsgemäß konfiguriert ist.

Wenn Sie dies bereits getan haben, überprüfen Sie, ob Ihnen *gemeinsamer Zugriff von mehr als einem Händler* gewährt wurde, indem Sie auf die Registerkarte [[!UICONTROL Shared with me] in Ihrem Konto](https://account.magento.com/grantor/manage/shared/) klicken:
* Wenn nur ein [!UICONTROL Share Name] aufgelistet ist, d. h., Sie wurden nur von einem Händler bewilligt, wird *kein [!UICONTROL Organization] Dropdown-Feld* angezeigt.
* Wenn mehrere [!UICONTROL Share Names] -Berechtigungen vorhanden sind, können die Support-Berechtigungen des Händlers abgelaufen sein, da ihre Lizenz aufgrund von Zahlungsproblemen zuvor widerrufen wurde.

### Tickets verfolgen {#track-tickets}

Ihre Tickets sind die, die Sie:

* persönlich
* wurden über einen CC (CO2-Kopie) als Beobachter hinzugefügt

#### Tickets anzeigen

Um alle Tickets aufzulisten, klicken Sie auf Ihr Profilmenü (obere rechte Ecke) auf der Startseite des Help-Center und wählen Sie **Meine Tickets** aus.

![kritische Warnung bezüglich der Festplatte](assets/my-tickets-8.png){width-&quot;800&quot;}

Um zwischen Ihren Tickets und den Tickets zu wechseln, die Sie bereits aktiviert haben, klicken Sie auf den entsprechenden Tab:

* **Meine Tickets**
* **Eintrittskarten, die ich am 1. Januar habe**
* **Eintrittskarten für Organisationen** (verfügbar, wenn Ihr Konto mit mehreren Organisationen verknüpft ist)

![hc_my-tickets_tabs.png](assets/hc_my-tickets_tabs.png)

Klicken Sie zum Sortieren von Tickets auf die Spaltenüberschriften **Erstellt** oder **Letzte Aktivität** .

#### Tickets suchen

Um Tickets zu finden, geben Sie Ihre Suchabfrage in das Feld **Suchtickets** ein und drücken Sie die *Eingabetaste* auf Ihrer Tastatur. Wählen Sie [einen Status](#ticket-status) für zusätzliche Filterung.

![hc_search-tickets.png](assets/hc_search-tickets.png)

#### Tickets für Organisationen

Sie können den Support-Tickets folgen, die von den Mitgliedern Ihres Unternehmens eingereicht wurden.

Wenn Sie Ihren Organisations-Tickets folgen, gehen Sie wie folgt vor:

* Tickets können auf der Registerkarte **Unternehmenstickets** angezeigt werden.
* erhalten E-Mail-Benachrichtigungen, wenn die neuen Tickets gesendet oder die vorhandenen Tickets geändert werden

So folgen/folgen Sie den Tickets für eine Organisation:

1. Gehen Sie zur Registerkarte **Meine Tickets** > **Organisations-Tickets** .
1. Wählen Sie eine Organisation im Menü aus und klicken Sie auf **Folgen/UnFollow**.

![hc_follow-org-tickets.png](assets/hc_follow-org-tickets.png)

### Adobe Commerce P1-Hotline {#P1-hotline}

**Die Anmeldung ist erforderlich**, um auf den Artikel [Adobe Commerce P1 Hotline](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/adobe-commerce-p1-notification-hotline.html) zuzugreifen, der die P1-Hotline-Nummern für Adobe Commerce bereitstellt, wenn Sie Hilfe bei einem P1-Vorfall suchen, und erklärt, welche Informationen bereitgestellt werden sollen.

### Betriebsmodell für gemeinsame Verantwortung von Adobe Commerce {#shared-responsibility-operational-model}

Weitere Informationen finden Sie im Artikel zum Betriebsmodell für die gemeinsame Verantwortung mit Adobe Commerce [1 .
, um die Betriebsverantwortung für unser Angebot an Pro-Infrastruktur zu klären.](https://experienceleague.adobe.com/en/docs/commerce-operations/security-and-compliance/shared-responsibility#operational-responsibilities-summary)

### Erläuterung der Support-Ticketfelder {#ticket-fields-explained}

#### Betroffene URL

Link zur Umgebung, in der das Adobe Commerce-Supportteam Ihr Problem sehen kann. Starten Sie die URL mit &quot;http://&quot; oder &quot;https://&quot;.

#### Anhänge

Fügen Sie Protokolle, Screenshots, Videoaufzeichnungen oder andere Medien an, die Ihr Problem besser illustrieren könnten.

#### Backoffice-URL (nur MOM)

URL muss mit &quot;https://&quot;beginnen. Sie weist normalerweise folgendes Format auf: Handelsname +&quot;.mcom.magento.com/admin/login&quot;, Beispiel: &quot;https://luma.mcom.magento.com/admin/login&quot;.

Sie können auch den direkten Link zu Ihrem Problem setzen.

#### CC

E-Mails der Personen, denen Sie Ihr Ticket folgen möchten (z. B. *first@e.mail*).

Sie können E-Mails von Personen hinzufügen, die kein Magento-Konto oder kein Zendesk-Konto haben; diese Personen können weiterhin in Ihrem Ticket zur Unterhaltung beitragen.

So fügen Sie CC mehrere E-Mails hinzu:

>[!NOTE]
>
>Der Benutzer in CC: muss über ein vorhandenes Konto unter https://account.magento.com verfügen. Ist dies nicht der Fall, muss zunächst ein Konto unter https://account.adobe.com erstellt und mit diesem Konto bei https://account.magento.com angemeldet werden.

1. Geben Sie die E-Mail ein.
1. Drücken Sie *Leertaste* auf Ihrer Tastatur, um die eingegebene E-Mail zu speichern. Die E-Mail wird in einem grauen Rahmen angezeigt.\
   ![hc_cc_emails.png](assets/hc_cc_emails.png)
1. Geben Sie die nächste E-Mail ein.
1. Speichern Sie alle anderen E-Mails, indem Sie auf *Leerzeichen* drücken.

Löschen von E-Mails aus CC: Klicken Sie in einer gerahmten E-Mail auf **x** .

![hc_cc_emails_remove.png](assets/hc_cc_emails_remove.png)

#### Produkt

Wählen Sie den Typ des Adobe Commerce-Produkts aus, mit dem Sie arbeiten:

* Adobe Commerce: Das Feld **[!UICONTROL Implementation Type]** wird angezeigt, nachdem Sie diese Option ausgewählt haben (Einzelheiten finden Sie unten).
* Magento Order Management
* Adobe Commerce-Berichterstellung: Nicht eingeschlossen [Fortschrittliche Berichterstellung](https://experienceleague.adobe.com/docs/commerce-admin/config/general/advanced-reporting.html)
* Adobe Commerce [Zahlungsdienste](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html)
* Adobe Commerce-Dienste: Nur [Kanal-Manager](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/guide-overview.html)

#### Implementierungstyp

Dieses Feld wird nur angezeigt, nachdem Sie **[!UICONTROL Product]** = *Adobe Commerce* ausgewählt haben

Geben Sie Ihre Implementierungsmethode an:

* Cloud: Wählen Sie diese Option nur aus, wenn Sie mit Adobe Commerce on Cloud Infrastructure arbeiten.
* On-Premise: *Alle selbst gehosteten Instanzen sowie [AWS] Cloud-basiertes Hosting* (Adobe Commerce on Cloud ausgenommen)

#### Cloud-Projekt-URL

Geben Sie die URL für das Cloud Console-Projekt ein, z. B. `https://console.adobecommerce.com/<owner-user-name>/<project-ID>`.

Eine weitere Methode zum Abrufen der Projekt-URL lautet:

1. Melden Sie sich bei der [Cloud-Konsole](https://console.adobecommerce.com) an.
1. Klicken Sie auf das entsprechende Projekt.
1. Kopieren Sie die URL.

#### Kontaktgrund

Die Kontaktgründe variieren je nach Produkt. Wählen Sie aus, welcher Kontaktgrund für Ihre Symptome am besten geeignet ist. Weitere Informationen dazu, welchen Kontaktgrund Sie auswählen sollten, finden Sie im Artikel [Beschreibungen der Kontaktgründe für Support-Tickets](/help/faq/general/support-ticket-contact-reason-descriptions.md) .

#### Adobe Commerce-Umgebungs-ID

Dieses Feld wird nur angezeigt, nachdem Sie **[!UICONTROL Contact Reason]** = *Adobe Commerce Cloud Application* ausgewählt haben, gefolgt von **Adobe Commerce Application Contact Reason** = *[!DNL Live Search]*.
Gehen Sie zu **[!UICONTROL System]** > **[!UICONTROL Services]** > **[!UICONTROL Commerce Services Connector]** > **[!UICONTROL SaaS Identifier]** und geben Sie die *[!UICONTROL Data Space ID]* ein.

#### (Daten) Integrationstyp (nur Adobe Commerce Reporting)

Wählen Sie den Integrationstyp aus, den Sie in Adobe Commerce Reporting verwenden. Dies hilft unseren Ingenieuren, Ihr Problem effizienter zu lösen.

#### Beschreibung

Geben Sie einen Überblick über Ihr Problem mit so vielen Details, wie Sie für vernünftig gehalten werden.

Bitte geben Sie genaue Details, Reproduktionsschritte (mit Ausnahme der lokalen Adobe Commerce- und Cloud-Infrastruktur, in der ein separates Feld mit den [Reproduktionsschritten](#steps) vorhanden ist) und Symptome Ihres Problems oder Ihrer Anfrage an. Stellen Sie sicher, dass Sie alle betroffenen SKUs, relevanten Datenpunkte und andere relevante Links einbeziehen.

#### Umgebung (Adobe Commerce für Cloud-Infrastruktur, Adobe Commerce vor Ort, Adobe Commerce Reporting und Versand)

Wählen Sie den **Umgebungstyp** aus, bei dem das Problem auftritt:

* Entwicklung (**Integrationszweige**)
* Staging
* Produktion

Weitere Informationen zu Adobe Commerce in Cloud-Infrastrukturumgebungen finden Sie im Artikel [Pro Architecture](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html) in unserem Benutzerhandbuch.

#### Anzahl der betroffenen Bestellungen (nur MOM)

Wählen Sie den betroffenen Auftragsbereich aus.

Dies ist eine Dropdown-Liste, die nur für Order Management-Produkte gilt.

#### Einrichtung

Geben Sie die Organisation an, mit der Ihr Ticket verknüpft werden soll - falls Sie mit mehreren Organisationen arbeiten.

Dieses Feld wird angezeigt, wenn Ihr Konto mit mehr als einer Organisation verknüpft ist.

>[!WARNING]
>
>Sie müssen sicherstellen, dass Sie die richtige Organisation ausgewählt haben. Drittanbieter, die nicht mit der Organisation verbunden sind, können potenziell vertrauliche und geschützte Informationen anzeigen, wenn Sie die falsche Organisation auswählen.

>[!NOTE]
>
>Die Organisation kann geändert werden, nachdem das Ticket gesendet wurde. Führen Sie diese Schritte aus, um die Organisation zu ändern.
>
>1. Gehen Sie zur rechten Spalte des Tickets.
>1. Suchen Sie das Dropdown-Menü für verfügbare Organisationen.
>1. Wählen Sie die entsprechende Organisation aus.
>
>![Organisation-Dropdown](/help/help-center-guide/help-center/assets/change_org.png)

Darüber hinaus würde es uns dadurch möglich sein, ähnliche/duplizierte/verwandte Tickets, die für diese Organisation in der Vergangenheit eingereicht wurden, schnell miteinander zu vergleichen und Hinweise zu identifizieren, die bei der Untersuchung und Lösung des aktuellen Tickets hilfreich sein könnten.

Wenn Sie über gemeinsamen Zugriff für mehrere Organisationen verfügen, dieses Feld jedoch nicht verfügbar ist, lesen Sie den Abschnitt zum Übermittlungsformular für Tickets: Der Händler wird nicht in der Dropdown-Liste &quot;Organisation&quot;angezeigt](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#merchant-not-displayed)[

#### Name des Partners (Name des Händlers)

Für Händler: **Partnername** ist der Name der Entwicklungsorganisation (Adobe Commerce [Technologiepartner](https://partners.magento.com/portal/directory/?&amp;partner_type=6) oder [Lösungspartner](https://partners.magento.com/portal/directory/?&amp;partner_type=1)), die an der Entwicklung Ihres Adobe Commerce-Stores beteiligt ist.

Für Partner: **Name des Händlers** ist der Name Ihres Kunden.

#### Projekt-URL (nur Commerce Cloud)

Link zur [Cloud-Konsole](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html).

#### Zu reproduzierende Schritte (nur Adobe Commerce vor Ort und Adobe Commerce auf Cloud-Infrastruktur)

Geben Sie genaue schrittweise Anweisungen, um Ihr Problem zu reproduzieren, einschließlich:

* Zu replizierende Schritte
* Erwartetes Ergebnis
* Tatsächliches Ergebnis

*Empfehlung:* Angenommen, Sie schreiben diese Schritte für jemanden, der **nichts** über Adobe Commerce weiß:

* Erwähnen Sie jeden Schritt, auch wenn er einfach und offensichtlich erscheint
* Verlassen Sie sich nicht auf die Annahme, dass Ihr Leser weiß, was Sie meinen

Schreiben Sie in einfacher Sprache mit kurzen Sätzen.

#### Betreff

Schließen Sie einen kurzen Überblick über Ihr Problem ein (z. B. *Fehler 404 auf allen Seiten*).

**Vorgeschlagene Artikel:** Wenn Sie den Suchbegriff eingeben, wird eine Liste der Adobe Commerce-Dokumentationsartikel angezeigt, die möglicherweise mit Ihrem Problem in Verbindung stehen. Klicken Sie auf einen Artikel in der Liste, um ihn zu öffnen.

![hc_subject-recommended-articles.png](assets/hc_subject-suggested-articles.png)

*Empfehlung:* Beachten Sie die vorgeschlagenen Artikel sorgfältig. Sie können die Lösung enthalten, die Sie vom Adobe Commerce-Supportteam erwarten.

#### Version (nur Adobe Commerce vor Ort, Adobe Commerce über Cloud-Infrastruktur und Versand)

Bitte wählen Sie die Adobe Commerce-Version aus, für die Sie Hilfe anfordern. Alle unterstützten Versionen von Adobe Commerce sind oben aufgeführt. Ununterstützte Versionen werden unten mit Klammern aufgeführt. Wenn Sie sich in der Migration befinden, wählen Sie die neueste Version aus, um sicherzustellen, dass Sie unterstützt werden.

Um die Version Ihrer Adobe Commerce (Cloud-Infrastruktur) zu finden, scrollen Sie die Seite [Cloud-Konsole](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html) nach unten und überprüfen Sie die untere Mitte des Fensters.

![Kontaktgrund auf Adobe Commerce Cloud Application und Adobe Commerce Application Contact Reason auf Live Search eingestellt](assets/magento-env-id.png)

Wenn Sie [Elasticsearch](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/search-engine/overview.html) oder [OpenSearch](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/search-engine/aws-opensearch.html) verwenden, wählen Sie diese Option nicht aus.

Um diese Informationen zu erhalten, gehen Sie im Adobe Commerce-Admin zu &quot;**Marketing**&quot;> &quot;**Live Search**&quot;> &quot;**GraphQL Playground**&quot;, blättern Sie nach unten zur Seite und klicken Sie dann auf &quot;**HTTP-HEADERS**&quot;.

### Ticketstatus: Verarbeitung der Tickets {#ticket-status}

Ihr Ticket kann einen dieser drei Status haben.

#### **1. Öffnen Sie**

Ihr Ticket wurde nicht gelöst und wird vom Adobe Commerce-Supportteam verarbeitet. Wenn Sie alle Informationen angegeben haben, die Sie in einem bestimmten Schritt der Konversation erwarten, und der nächste Schritt vom Adobe Commerce-Support durchgeführt werden muss, hat Ihr Ticket den Status **Öffnen** .

#### **2. Warten auf Ihre Antwort**

Der Adobe Commerce-Support erwartet Informationen von Ihnen.

In Ihrer Antwort können Sie zusätzliche technische Details zu Ihrem Problem angeben, Eskalationsdetails angeben oder angeben, ob die vom Adobe Commerce-Support angebotene Lösung für Ihr Problem hilfreich war. Stellen Sie sicher, dass Sie Ihre Antworten so schnell wie möglich bereitstellen, da der Adobe Commerce-Support mit der Verarbeitung Ihres Tickets nicht fortfahren kann, während es sich im Status **Erwarten der Antwort** befindet.

Weitere Informationen zur Timing- und Benachrichtigungsrichtlinie finden Sie im Artikel Update der Adobe Commerce-Lebenszyklusrichtlinie für Support [-Unterstützung](/help/help-center-guide/help-center/magento-support-ticket-lifecycle-policy-update.md) .

#### **3. Gelöst**

Der Adobe Commerce-Support bietet eine Lösung für Ihr Problem, und Sie haben zugestimmt, dass dies hilfreich war. Du bist es, der das Ticket als **Gelöst** markiert. Wenn das Problem erneut behoben wird, können Sie das Ticket erneut öffnen und seinen Status auf **Öffnen** zurücksetzen.

### Unterhaltung in Ihrem Ticket {#conversation-in-ticket}

Die Unterhaltung in Ihrem Ticket vereint alle Kommentare, die von Ihnen oder dem Adobe Commerce-Supportteam geschrieben wurden. Kommentare werden von der neuesten (oben) zur frühesten (unten) angezeigt.

Gehen Sie wie folgt vor, um einen Kommentar zur Konversation hinzuzufügen:

1. Scrollen Sie zum unteren Ende Ihres Tickets.
1. Klicken Sie auf das Feld **Zu Konversation hinzufügen** , um mit dem Schreiben zu beginnen.

   ![hc_add-to-conversion.png](assets/hc_add-to-conversation.png)

1. Um eine Person zu Ihrem Kommentar hinzuzufügen, geben Sie die E-Mail im Feld **CC** des Kommentarfelds an.

   >[!NOTE]
   >
   >Der Benutzer in CC: muss über ein vorhandenes Konto unter https://account.magento.com verfügen. Ist dies nicht der Fall, muss zunächst ein Konto unter https://account.adobe.com erstellt und mit diesem Konto bei https://account.magento.com angemeldet werden.

   ![hc_conversion-write.png](assets/hc_conversation-write.png)

1. Nachdem Sie mit Ihrem Kommentar fertig sind, klicken Sie auf **Senden**.

### Ticket lösen {#resolve-ticket}

Um Ihr Ticket zu lösen, klicken Sie unten in Ihrem Ticket auf **Als gelöst markieren** .

### Öffnen Sie ein Folgenachticket. {#follow-up}

Durch die Eröffnung eines Folgenachweises wird sichergestellt, dass das ursprüngliche Problem mit dem Folgeticket für die Kontinuität verknüpft ist.

Um ein Follow-up-Ticket zu öffnen, klicken Sie auf den Link &quot;*Follow-up erstellen*&quot; am unteren Rand des Tickets, zu dem Sie eine Weiterverfolgung erstellen möchten.

## FREIGEGEBENER ZUGRIFF: GEWÄHREN SIE ANDEREN BENUTZERN BERECHTIGUNGEN FÜR DEN ZUGRIFF AUF IHR KONTO. {#shared-access}

Sie können anderen Adobe Commerce-Kontoinhabern eingeschränkten Zugriff auf Ihr Konto gewähren. Insbesondere können Sie mit der Funktion **Freigegebener Zugriff** Berechtigungen für vertrauenswürdige Mitarbeiter und Dienstleister bereitstellen, damit diese Ihr Hilfe-Center-Konto verwenden können, damit sie mit Ihren Support-Tickets arbeiten können.

Sie können freigegebenen Zugriff über Ihre Adobe Commerce-Kontoseite unter [https://account.magento.com](https://account.magento.com/) bereitstellen und verwalten.

### Wer kann freigegebenen Zugriff gewähren? {#who-can-provide-shared-access}

Nur der Kontoinhaber (Primärkontoinhaber) mit den entsprechenden Berechtigungen kann anderen Benutzern freigegebenen Zugriff gewähren.

Die Verwaltung von Benutzern und deren Zugriff liegt in der Verantwortung des Kunden, insbesondere im Hinblick auf den gemeinsamen Zugriff. Daher kann das Adobe Commerce-Supportteam keinen freigegebenen Zugriff auf ein Adobe Commerce-Konto für einen Kunden bereitstellen. Kunden wird empfohlen, über die [Adobe Commerce-Kontoseite](https://account.magento.com/) Benutzer mit freigegebenem Zugriff selbst hinzuzufügen.

Benutzer, denen freigegebener Zugriff gewährt wurde, können diesen Zugriff nicht an andere Benutzer übertragen oder gewähren.

### Freigegebenen Zugriff gewähren {#provide-shared-access}

Detaillierte Anweisungen zum Einrichten eines freigegebenen Kontos finden Sie im Abschnitt [Freigeben eines Commerce-Kontos](https://experienceleague.adobe.com/en/docs/commerce-admin/start/commerce-account/commerce-account-share) des Adobe Commerce-Erste-Schritte-Handbuchs.

Nachdem Sie einem neuen Benutzer freigegebenen Zugriff gewährt haben, sind die entsprechenden Informationen auf der Seite &quot;**Freigegebener Zugriff**&quot;> &quot;**Berechtigungen verwalten**&quot;Ihrer Adobe Commerce-Kontoseite verfügbar.

![magento-account-shared-manage-permissions](assets/magento_account_shared_manage_permissions.png)

### Freigegebenen Zugriff sperren (löschen) {#revoke-shared-access}

1. Melden Sie sich bei Ihrem Adobe Commerce-Konto unter [https://account.magento.com](https://account.magento.com/) an.
1. Wählen Sie im Bereich auf der linken Seite unter &quot;Freigegebener Zugriff&quot;die Option **Berechtigungen verwalten**.
1. Suchen Sie den Benutzer, von dem der freigegebene Zugriff widerrufen werden soll, und klicken Sie in der Zeile des Benutzers auf ![Symbol &quot;Entfernen&quot;](assets/remove_icon.png){width="25"} ( Spalte **Aktionen** ).
1. Klicken Sie auf **Benutzer löschen** , um den Zugriff zu widerrufen, oder auf X in der oberen Ecke, um die Sperrung abzubrechen.

   ![Revoke_shared_access](assets/revoke_shared_access.png){width="800"}

   Sie können den freigegebenen Zugriff auch über das Menü **Bearbeiten** widerrufen:

1. Melden Sie sich bei Ihrem Adobe Commerce-Konto unter [https://account.magento.com](https://account.magento.com/) an.
1. Wählen Sie im Bereich auf der linken Seite unter &quot;Freigegebener Zugriff&quot;die Option **Berechtigungen verwalten**.
1. Suchen Sie den Benutzer, von dem der freigegebene Zugriff widerrufen werden soll, und klicken Sie in der Zeile des Benutzers auf **Bearbeiten** (**Aktionen** -Spalte).
1. Klicken Sie unten auf der Seite auf **Diesen Benutzer löschen** .
1. Klicken Sie im Bestätigungs-Popup auf **Benutzer löschen** , um den Zugriff zu sperren, oder auf X in der oberen Ecke, um die Sperrung abzubrechen.

### Wie kann ich Benutzer löschen, denen der gemeinsame Zugriff über ein Cloud-Projekt gewährt wurde? {#remove-cloud-shared-access-users}

<u>Betroffene Produkte und Versionen</u>

* Adobe Commerce Cloud (alle Versionen)

<u>Ursache</u>

Wenn Sie ein Adobe Commerce Cloud-Projekt durchgeführt haben/hatten und einen Benutzer zum Projekt hinzugefügt hatten, erhalten diese automatisch freigegebenen Zugriff auf die MAGE-ID des Projekteigentümers. Dies wird normalerweise in der Spalte **[!UICONTROL Share Name]** angezeigt, in der *Freigegebener Cloud-Zugriff von MAG[XYZ]* angezeigt wird.

Wenn der DELETE-Link fehlt, bedeutet dies, dass der Freigegebene Zugriff automatisch über Commerce Cloud gewährt wurde.

<u>Lösung</u>

Es ist nicht möglich, die Liste der Benutzer mit freigegebenem Zugriff mit dem Freigabenamen &quot;*Cloud Shared Access&quot;von MAG[XYZ]*&quot;zu löschen, wenn der freigegebene Zugriff nicht auf dieser Seite hinzugefügt/bereitgestellt wurde. Diese werden zu Informations-/Auditzwecken aufbewahrt.

Nachdem Sie die Berechtigungen für diese Benutzer mit gemeinsamem Zugriff widerrufen haben, haben sie diesen Zugriff jedoch nicht mehr.

1. Melden Sie sich bei Ihrem Adobe Commerce-Konto unter [https://account.magento.com](https://account.magento.com/) an.
1. Wählen Sie im Bedienfeld auf der linken Seite unter *[!UICONTROL Shared Access]* die Option **[!UICONTROL Manage Permissions]**.
1. Suchen Sie den Benutzer, von dem der freigegebene Zugriff widerrufen werden soll, und klicken Sie in der Zeile des Benutzers (*[!UICONTROL Actions]* -Spalte) auf **[!UICONTROL Edit]** .
1. Deaktivieren Sie alle Ressourcen unter &quot;*[!UICONTROL Grant Account Permissions]*&quot;.

![grant-account-permissions-image](assets/help-center-user-guide-grant-account-permissions-image.png){width="800"}

Weitere Informationen finden Sie in der Dokumentation [Verwalten des Benutzerzugriffs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#manage-users-from-the-project-web-interface) im Handbuch zu Commerce on Cloud Infrastructure.

### Zugriff auf freigegebene Konten (Konten wechseln) {#switch-accounts}

Gehen Sie wie folgt vor, um den für Sie freigegebenen Zugriff zu verwenden:

1. Melden Sie sich bei Ihrem Adobe Commerce-Konto unter [https://account.magento.com](https://account.magento.com/) an.
1. Klicken Sie auf das Menü **Konten wechseln** und wählen Sie ein Konto aus.

   ![magento-account-shared-switch](assets/magento_account_shared_switch.png){width="800"}

Informationen dazu, welches Konto Sie derzeit verwenden (Ihr eigenes natives Konto oder freigegebener Zugriff), finden Sie im Menü **Konten wechseln** : Es zeigt das aktive Konto an.

### Fehlerbehebung bei freigegebenen Zugriffen {#troubleshooting-shared-access}

Lesen Sie diesbezüglich auch den Artikel [Fehlerbehebung bei Problemen mit freigegebenen Zugriffen](/help/troubleshooting/miscellaneous/shared-access-troubleshooting.md) in unserer Support-Wissensdatenbank.

## FAQ ZUR ABRECHNUNG FÜR ADOBE COMMERCE {#billing-faq}

Händler bezahlen unsere Dienstleistungen in der Regel mit einer Kreditkarten-Transaktion (CC). Diese [FAQ zur Rechnungsstellung für Adobe Commerce](/help/faq/general/billing-faq-for-adobe-commerce.md) ist eine Ressource, die Ihnen bei der Zahlung Ihrer Rechnung hilft.

## MAGENTO U IST JETZT TEIL VON ADOBE DIGITAL LERNDIENSTLEISTUNGEN {#magento-u}

Magento U hat mit [Adobe Digital Learning Services (ADLS)](https://learning.adobe.com/) zusammengeführt.

