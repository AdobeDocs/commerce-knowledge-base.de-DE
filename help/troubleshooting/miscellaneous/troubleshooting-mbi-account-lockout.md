---
title: Fehlerbehebung für die Sperrung von Adobe Commerce Intelligence-Konten
description: Dieser Artikel bietet Lösungen für die Sperrung von Adobe Commerce Intelligence-Konten. Zunächst müssen wir feststellen, ob es sich um einen Fehler, einen vorübergehenden Fehler oder etwas Anderes handelt. Die folgenden Schritte helfen Ihnen, so schnell wie möglich in Ihr Konto zurückzukehren.
exl-id: 85968257-ba4b-4cfb-a4fa-497b4c5b5aea
feature: Cache, Commerce Intelligence, Console
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%

---

# Fehlerbehebung für die Sperrung von Adobe Commerce Intelligence-Konten

<!--
BOB: Is this in TOC?
-->

Dieser Artikel bietet Lösungen für die Sperrung von Commerce Intelligence-Konten. Zunächst müssen wir feststellen, ob es sich um einen Fehler, einen vorübergehenden Fehler oder etwas Anderes handelt. Die folgenden Schritte helfen Ihnen, so schnell wie möglich in Ihr Konto zurückzukehren.

## Überprüfen Sie die korrekte E-Mail-Adresse.

Überprüfen Sie Ihre E-Mail-Adresse, um sicherzustellen, dass die E-Mail-Adresse, die Sie für die Anmeldung verwenden möchten, mit einem vorhandenen Commerce Intelligence-Konto verknüpft ist. Möglicherweise müssen Sie einen Kundenbetreuer bitten, zu bestätigen, dass die E-Mail-Adresse keine Tippfehler enthält.

Sobald Sie bestätigt haben, dass die E-Mail-Adresse korrekt ist, versuchen Sie, sich erneut mit [diesem Link](https://dashboard.rjmetrics.com/v2/session/create#/) anzumelden.

## Zurücksetzen des Kennworts versuchen

Wenn Sie überprüft haben, ob Sie die richtige E-Mail verwenden, versuchen Sie, Ihr Kennwort zurückzusetzen. Sie können die Funktion &quot;**Vergessen&quot;verwenden?** Link auf der Anmeldeseite aus dem vorherigen Abschnitt, um eine E-Mail zum Zurücksetzen des Kennworts Trigger.

Wenn Sie die E-Mail zuerst nicht sehen, achten Sie darauf, in Ihren Junk-E-Mail-Ordner zu schauen. Manchmal lassen sich auch gut gemeinte E-Mails mit Junk verwechseln. **Beachten Sie, dass die temporären Zugriffs-Links in diesen E-Mails nur einmal funktionieren!**

Wenn Sie noch ausgesperrt sind, stellen Sie sicher, dass Ihre E-Mail-Adresse korrekt ist und verwenden Sie den richtigen Link aus der E-Mail zum Zurücksetzen. Es wird empfohlen, den folgenden **auszuprobieren, bevor Sie einen weiteren Reset anfordern und versuchen, sich erneut anzumelden:**

* Löschen Sie den Cache, die Cookies und die gespeicherten Kennwörter Ihres Browsers
* Deaktivieren Sie vorübergehend jede Software, die Werbung blockiert

## Dokumentieren von Fehlern und Wenden Sie sich an die Support-Abteilung.

>[!NOTE]
>
>Dieser Schritt ist nicht immer erforderlich, aber durch eine proaktive Fertigstellung kann die Zeit reduziert werden, die mit einem Support-Antrag verbracht wird.

Wenn Sie immer noch nicht auf Ihr Konto zugreifen können, empfehlen wir Ihnen, nach Fehlern zu suchen und ein Ticket an unser Supportteam zu senden. Wie kannst du das machen? Indem Sie die Entwicklertools Ihres Browsers öffnen und einen Screenshot aller Fehler machen, die in der Konsole oder im Site-Log-Fenster angezeigt werden. Auf der folgenden GIF öffne ich die Entwicklertools für Google Chrome:

![Öffnen der Entwicklertools von Chrome.](assets/Opening_Chrome_dev_tools.gif)

Im obigen Beispiel haben wir die am häufigsten verwendete Methode (**Rechtsklick** > **Inspect**) zum Öffnen der Konsole verwendet. Wenn Ihr Browser nicht über diese Methode verfügt oder Sie Hilfe benötigen, verwenden Sie die folgenden Dokumentationslinks für den verwendeten Webbrowser:

<table>
<tbody>
<tr>
<td><a href="https://www.technipages.com/mac-os-x-enable-web-inspector-in-safari">Safari</a></td>
<td><a href="https://developer.mozilla.org/en-US/docs/Tools/Web_Console/Opening_the_Web_Console">Firefox</a></td>
<td><a href="https://developers.google.com/web/tools/chrome-devtools/?hl=en">Chrome</a></td>
<td><a href="https://www.opera.com/dragonfly/documentation/">Opera</a></td>
<td><a href="https://msdn.microsoft.com/en-us/library/gg589512(v=vs.85).aspx#OpeningTools">Internet Explorer</a></td>
</tr>
</tbody>
</table>

In einigen Browsern wird beim Öffnen der Entwickler-Tools möglicherweise nicht automatisch die Konsole angezeigt. Der Code der Site wird möglicherweise zuerst angezeigt. Wenn dies bei Ihnen eintritt, klicken Sie im Entwicklerfenster auf die Option Konsole und erstellen Sie Screenshots von dort angezeigten Fehlern.

Senden Sie ein Ticket mit den **Fehler-Screenshots** und der E-Mail-Adresse Ihres **Commerce Intelligence-Kontos** an unser Supportteam.

## Siehst du keine Fehler, oder bist du einfach verloren?

Mach dir keine Sorgen! Melden Sie ein neues Support-Ticket an (geben Sie die E-Mail-Adresse Ihres Commerce Intelligence-Kontos ein) und wir werden Sie so bald wie möglich wieder in Ihr Konto eintragen.

## Verwandte Themen in unserer Support-Wissensdatenbank:

* [Hinzufügen eines neuen Benutzers und Festlegen von Berechtigungen](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/administrator/user-mgmt/user-management.html)
* [Wie kann ich meine E-Mail-Adresse oder mein Passwort aktualisieren?](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/administrator/user-mgmt/create-user.html)
* [Wie setze ich mein Kennwort zurück?](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/administrator/user-mgmt/reset-password.html)
