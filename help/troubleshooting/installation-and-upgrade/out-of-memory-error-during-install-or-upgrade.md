---
title: Fehler wegen zu wenig Speicher während der Installation oder Aktualisierung
description: In diesem Artikel werden Lösungen für den Fehler bei der Installation/Aktualisierung von Adobe Commerce vor Ort und Magento Open Source vor Ort beschrieben.
exl-id: c0ed8228-9357-4a3b-a102-1119386ea52a
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Fehler wegen zu wenig Speicher während der Installation oder Aktualisierung

In diesem Artikel werden Lösungen für den Fehler bei der Installation/Aktualisierung von Adobe Commerce vor Ort und Magento Open Source vor Ort beschrieben.

## Betroffene Produkte und Versionen

* Adobe Commerce vor Ort 2.3.x
* Magento Open Source vor Ort 2.3.x

## Problem

Beim Installieren oder Aktualisieren der Adobe Commerce- oder Magento Open Source-Anwendung oder von Komponenten wie Erweiterungen, Designs oder Sprachpaketen mit dem Web-Setup-Assistenten wird ein Fehler ähnlich dem folgenden angezeigt:

```bash
Could not complete update {"components":[
{"name":"magento/module-bundle-sample-data","version":"100.1.0"}
]} successfully: proc_open(): fork failed - Cannot allocate memory
```

Der Fehler

```bash
proc_open(): fork failed - Cannot allocate memory
```

kann auch in der Befehlszeile angezeigt werden.

## Lösung {#solution}

Wir empfehlen Ihnen in unserer Entwicklerdokumentation [2 GB Arbeitsspeicher für PHP](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/php-settings) zuzuweisen, um sicherzustellen, dass Ihre Installation oder Aktualisierung erfolgreich ist.

Wenn Sie dies bereits getan haben, erstellen Sie eine Swap-Datei auf Ihrem Computer. Ein Linux-Computer verwendet *Swap-Speicherplatz* , wenn er mehr Speicherressourcen benötigt und der RAM voll ist. Der Austauschraum wird für inaktive Seiten im Speicher verwendet.

Im Folgenden werden nur Vorschläge beschrieben. Es können weitere Optionen verfügbar sein. Wenden Sie sich an einen Netzwerkadministrator oder eine andere sachkundige Ressource, bevor Sie fortfahren. Sie müssen die Befehle ausführen, um eine Swap-Datei als Benutzer mit `root` -Berechtigungen zu erstellen.

### Datei tauschen auf Ubuntu {#swap-file-on-ubuntu}

Verwenden Sie den Befehl `fallocate` , wie in den folgenden Verweisen beschrieben:

* [So fügen Sie Swap auf Ubuntu 14.04 (DigitalOcean) hinzu](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04)
* [Hinzufügen von Swap-Speicherplatz auf Ubuntu 16.04 (DigitalOcean)](https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-16-04)
* [SwapFAQ (help.ubuntu.com)](https://help.ubuntu.com/community/SwapFaq)

### Dateiaustausch auf CentOS {#swap-file-on-centos}

Verwenden Sie den Befehl `mkswap` , wie in den folgenden Verweisen beschrieben:

* [Hinzufügen von Swap auf CentOS 6 (DigitalOcean)](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-centos-6)
* [Hinzufügen von Swap auf CentOS 7 (DigitalOcean)](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-centos-7)
* [Swap Space (RedHat-Kundenportal)](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Storage_Administration_Guide/ch-swapspace.html)
