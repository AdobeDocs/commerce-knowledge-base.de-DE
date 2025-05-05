---
title: Fehlerbehebung für Adobe Commerce Intelligence-Kontosperrung
description: Dieser Artikel enthält Lösungen für die Adobe Commerce Intelligence-Kontosperrung. Zuerst müssen wir feststellen, ob es sich um einen Defekt, eine vorübergehende Störung oder etwas Anderes handelt. Die folgenden Schritte helfen Ihnen, Ihr Konto so schnell wie möglich wieder zu aktivieren.
exl-id: 85968257-ba4b-4cfb-a4fa-497b4c5b5aea
feature: Cache, Commerce Intelligence, Console
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%

---

# Fehlerbehebung für Adobe Commerce Intelligence-Kontosperrung

<!--
BOB: Is this in TOC?
-->

Dieser Artikel enthält Lösungen für die Commerce Intelligence-Kontosperrung. Zuerst müssen wir feststellen, ob es sich um einen Defekt, eine vorübergehende Störung oder etwas Anderes handelt. Die folgenden Schritte helfen Ihnen, Ihr Konto so schnell wie möglich wieder zu aktivieren.

## Überprüfen Sie, ob Ihre E-Mail-Adresse korrekt ist

Überprüfen Sie Ihre E-Mail-Adresse, um sicherzustellen, dass die E-Mail-Adresse, die Sie für die Anmeldung verwenden möchten, mit einem bestehenden Commerce Intelligence-Konto verknüpft ist. Möglicherweise müssen Sie einen Konto-Administrator bitten, zu bestätigen, dass die E-Mail-Adresse keine Tippfehler enthält.

Nachdem Sie sich vergewissert haben, dass die E-Mail-Adresse korrekt ist, versuchen Sie, sich erneut über [diesen Link](https://dashboard.rjmetrics.com/v2/session/create#/) anzumelden.

## Zurücksetzen des Kennworts versuchen

Wenn Sie überprüft haben, dass Sie die richtige E-Mail verwenden, versuchen Sie, Ihr Kennwort zurückzusetzen. Sie können die Datei &quot;**?** Link auf der Anmeldeseite aus dem vorherigen Abschnitt, um eine E-Mail zum Zurücksetzen des Kennworts Trigger.

Wenn die E-Mail zunächst nicht angezeigt wird, schauen Sie unbedingt in Ihren Junk-E-Mail-Ordner. Manchmal werden sogar gut gemeinte E-Mails mit Junk verwechselt. **Beachten Sie, dass die temporären Zugriffs-Links in diesen E-Mails nur einmal in Ordnung sind!**

Wenn Sie immer noch gesperrt sind, stellen Sie sicher, dass Ihre E-Mail-Adresse korrekt ist und Sie den richtigen Link aus der Zurücksetzen-E-Mail verwenden. Wir empfehlen, Folgendes auszuprobieren **bevor Sie ein weiteres Zurücksetzen anfordern und erneut versuchen, sich anzumelden:**

* Löschen Sie den Cache, die Cookies und die gespeicherten Kennwörter Ihres Browsers
* Deaktivieren Sie vorübergehend jegliche Werbeblocker-Software

## Dokumentieren Sie etwaige Fehler und wenden Sie sich an den Support

>[!NOTE]
>
>Dieser Schritt ist nicht immer erforderlich. Ein proaktiver Abschluss dieses Schritts könnte jedoch den Zeitaufwand für das Hin- und Herbewegen einer Support-Anfrage reduzieren.

Wenn Sie immer noch nicht auf Ihr Konto zugreifen können, empfehlen wir, nach Fehlern zu suchen und ein Ticket an unser Support-Team zu senden. Wie kannst du das machen? Öffnen Sie dazu die Entwickler-Tools Ihres Browsers und machen Sie einen Screenshot aller Fehler, die in der Konsole oder im Site-Protokollfenster angezeigt werden. Auf der folgenden GIF öffne ich die Entwickler-Tools für Google Chrome:

![Öffnen der Entwicklertools von Chrome.](assets/Opening_Chrome_dev_tools.gif)

Im obigen Beispiel haben wir die gängigste Methode (**Rechtsklick** > **Inspect**) zum Öffnen der Konsole verwendet. Wenn Ihr Browser diese Methode nicht hat oder Sie Hilfe benötigen, verwenden Sie die folgenden Dokumentations-Links für den verwendeten Webbrowser:

<table>
<tbody>
<tr>
<td><a href="https://www.technipages.com/mac-os-x-enable-web-inspector-in-safari">Safari</a></td>
<td><a href="https://developer.mozilla.org/en-US/docs/Tools/Web_Console/Opening_the_Web_Console">Firefox</a></td>
<td><a href="https://developers.google.com/web/tools/chrome-devtools/?hl=en">Chrome</a></td>
<td><a href="https://www.opera.com/dragonfly/documentation/">Oper</a></td>
<td><a href="https://msdn.microsoft.com/en-us/library/gg589512(v=vs.85).aspx#OpeningTools">Internet Explorer</a></td>
</tr>
</tbody>
</table>

In einigen Browsern wird beim Öffnen der Entwickler-Tools die Konsole möglicherweise nicht automatisch angezeigt, sondern der Code der Site wird möglicherweise zuerst angezeigt. Wenn dies bei Ihnen der Fall ist, klicken Sie auf die Option Konsole im Entwicklerfenster und machen Sie Screenshots der dort angezeigten Fehler.

Reichen Sie ein Ticket mit den **Fehler-Screenshots** und der E-Mail-Adresse Ihres **Commerce Intelligence-Kontos an unser Support-Team**.

## Sehen Sie keine Fehler oder sind Sie verloren?

Keine Sorge! Erstellen Sie ein neues Support-Ticket (geben Sie unbedingt die E-Mail-Adresse Ihres Commerce Intelligence-Kontos an). Wir werden Ihnen so schnell wie möglich antworten.

## Verwandte Themen in unserer Support-Wissensdatenbank:

* [Hinzufügen eines neuen Benutzers und Festlegen von Berechtigungen](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/administrator/user-mgmt/user-management.html?lang=de)
* [Wie aktualisiere ich meine E-Mail-Adresse oder mein Passwort?](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/administrator/user-mgmt/create-user.html?lang=de)
* [Wie setze ich mein Passwort zurück?](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/administrator/user-mgmt/reset-password.html?lang=de)
