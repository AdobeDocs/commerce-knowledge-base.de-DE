---
title: Probleme bei der Prüfung der Bereitschaft für Dateiberechtigungen
description: 'Dieser Artikel enthält eine Fehlerbehebung für Probleme bei der Prüfung der Bereitschaft für Dateiberechtigungen. Verzeichnisse im Adobe Commerce-Dateisystem müssen vom Webserverbenutzer und gegebenenfalls vom Eigentümer des Adobe Commerce-Dateisystems beschreibbar sein. Wenn Ihre Berechtigungen nicht ordnungsgemäß festgelegt sind, wird im Websetup-Assistenten ein Fehler ähnlich dem folgenden angezeigt:'
exl-id: 252e6e7d-5269-44ce-b3ce-6fc2ea6a1c5c
feature: Roles/Permissions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# Probleme bei der Prüfung der Bereitschaft für Dateiberechtigungen

Dieser Artikel enthält eine Fehlerbehebung für Probleme bei der Prüfung der Bereitschaft für Dateiberechtigungen. Verzeichnisse im Adobe Commerce-Dateisystem müssen vom Webserverbenutzer und gegebenenfalls vom Eigentümer des Adobe Commerce-Dateisystems beschreibbar sein. Wenn Ihre Berechtigungen nicht ordnungsgemäß festgelegt sind, wird im Websetup-Assistenten ein Fehler ähnlich dem folgenden angezeigt:

![install_rc_file-perms.png](assets/install_rc_file-perms.png)

Die Art und Weise, wie Sie das Problem beheben, hängt davon ab, ob Sie ein Setup mit einem oder zwei Benutzern haben:

* *Ein Benutzer* bedeutet, dass Sie sich beim Adobe Commerce-Server als derselbe Benutzer anmelden, der auch den Webserver ausführt. Diese Art der Einrichtung ist in freigegebenen Hosting-Umgebungen üblich.
* *Zwei Benutzer* bedeutet, dass *sich normalerweise nicht als* anmelden oder zu diesem wechseln können. Normalerweise melden Sie sich als ein Benutzer an und führen den Webserver als einen anderen Benutzer aus. Dies ist typisch für privates Hosting oder wenn Sie über einen eigenen Server verfügen.

## Auflösung für einen Benutzer

Wenn Sie über Befehlszeilenzugriff verfügen, geben Sie den folgenden Befehl ein, vorausgesetzt, Adobe Commerce ist in `/var/www/html/magento2` installiert:

```bash
$ cd /var/www/html/magento2 && find var vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var vendor pub/static pub/media app/etc -type d -exec chmod g+w {} + && chmod u+x bin/magento
```

Wenn Sie keinen Befehlszeilenzugriff haben, verwenden Sie einen FTP-Client oder eine Datei-Manager-Anwendung, die von Ihrem Hosting-Anbieter bereitgestellt wird, um die Berechtigungen festzulegen.

## Zwei-Benutzer-Auflösung

Um optional alle Befehle in einer Zeile einzugeben, geben Sie Folgendes ein, vorausgesetzt, Adobe Commerce ist in `/var/www/html/magento2` installiert und der Name der Webserver-Gruppe ist `apache`:

```bash
$ cd /var/www/html/magento2 && find var vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && chown -R :apache . && chmod u+x bin/magento
```

Falls die Berechtigungen für das Dateisystem des Ereignisses nicht ordnungsgemäß festgelegt sind und vom Eigentümer des Adobe Commerce-Dateisystems nicht geändert werden können, können Sie den Befehl als Benutzer mit `root` Berechtigungen eingeben:

```bash
$ cd /var/www/html/magento2 && sudo find var vendor
  pub/static pub/media app/etc -type f -exec chmod g+w {} + && sudo find
  var vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + &&
  sudo chown -R :apache . && sudo chmod u+x bin/magento
```
