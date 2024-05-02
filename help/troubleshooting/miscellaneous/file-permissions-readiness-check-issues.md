---
title: Probleme bei der Überprüfung der Dateiberechtigungen
description: '''Dieser Artikel enthält eine Fehlerbehebung für Probleme bei der Vorbereitung auf Dateiberechtigungen. Verzeichnisse im Adobe Commerce-Dateisystem müssen vom Webserver-Benutzer und gegebenenfalls vom Adobe Commerce-Dateisysteminhaber schreibbar sein. Wenn Ihre Berechtigungen nicht richtig festgelegt sind, wird im Web-Einrichtungs-Assistenten ein Fehler ähnlich dem folgenden angezeigt:"'
exl-id: 252e6e7d-5269-44ce-b3ce-6fc2ea6a1c5c
feature: Roles/Permissions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# Probleme bei der Überprüfung der Dateiberechtigungen

Dieser Artikel enthält eine Fehlerbehebung für Probleme bei der Kompatibilitätsprüfung für Dateiberechtigungen. Verzeichnisse im Adobe Commerce-Dateisystem müssen vom Webserver-Benutzer und gegebenenfalls vom Adobe Commerce-Dateisysteminhaber schreibbar sein. Ein Fehler ähnlich dem folgenden wird im Web-Einrichtungs-Assistenten angezeigt, wenn Ihre Berechtigungen nicht ordnungsgemäß festgelegt sind:

![install_rc_file-perms.png](assets/install_rc_file-perms.png)

Die Art und Weise, wie Sie das Problem beheben, hängt davon ab, ob Sie über eine Ein- oder Zweibenutzer-Einrichtung verfügen:

* *Ein Benutzer* bedeutet, dass Sie sich beim Adobe Commerce-Server als derselbe Benutzer anmelden, der auch den Webserver ausführt. Diese Art der Einrichtung ist in freigegebenen Hosting-Umgebungen üblich.
* *Zwei Benutzer* bedeutet, dass *cannot* als Webserver-Benutzer anmelden oder zu ihm wechseln. Normalerweise melden Sie sich als ein Benutzer an und führen den Webserver als einen anderen Benutzer aus. Dies ist typisch für privates Hosting oder wenn Sie über einen eigenen Server verfügen.

## Auflösung für einen Benutzer

Wenn Sie Zugriff auf die Befehlszeile haben, geben Sie den folgenden Befehl ein, vorausgesetzt Adobe Commerce ist in installiert. `/var/www/html/magento2`:

```bash
$ cd /var/www/html/magento2 && find var vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var vendor pub/static pub/media app/etc -type d -exec chmod g+w {} + && chmod u+x bin/magento
```

Wenn Sie keinen Befehlszeilenzugriff haben, verwenden Sie einen FTP-Client oder eine von Ihrem Hosting-Provider bereitgestellte Datei-Manager-Anwendung, um Berechtigungen festzulegen.

## Auflösung von zwei Benutzern

Wenn Sie optional alle Befehle in einer Zeile eingeben möchten, geben Sie Folgendes ein (vorausgesetzt, Adobe Commerce ist in installiert) `/var/www/html/magento2` und der Webserver-Gruppenname `apache`:

```bash
$ cd /var/www/html/magento2 && find var vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && chown -R :apache . && chmod u+x bin/magento
```

Wenn die Systemberechtigungen für die Ereignisdatei falsch festgelegt sind und vom Adobe Commerce-Dateisysteminhaber nicht geändert werden können, können Sie den Befehl als Benutzer mit `root` -Berechtigungen:

```bash
$ cd /var/www/html/magento2 && sudo find var vendor
  pub/static pub/media app/etc -type f -exec chmod g+w {} + && sudo find
  var vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + &&
  sudo chown -R :apache . && sudo chmod u+x bin/magento
```
