---
title: Fehler wegen zu wenig Arbeitsspeicher während der Installation oder Aktualisierung
description: In diesem Artikel wird über Lösungen für den Fehler wegen zu wenig Arbeitsspeicher bei der Installation/Aktualisierung von lokalen Adobe Commerce- und lokalen Magento Open Source-Produkten gesprochen.
exl-id: c0ed8228-9357-4a3b-a102-1119386ea52a
feature: Install, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%
---
# Fehler wegen zu wenig Arbeitsspeicher während der Installation oder Aktualisierung

In diesem Artikel wird über Lösungen für den Fehler wegen zu wenig Arbeitsspeicher bei der Installation/Aktualisierung von lokalen Adobe Commerce- und lokalen Magento Open Source-Produkten gesprochen.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premises 2.3.x
* Magento Open Source On-Premises 2.3.x

## Problem

Beim Installieren oder Aktualisieren der Adobe Commerce- oder Magento Open Source-Anwendung oder von Komponenten wie Erweiterungen, Designs oder Sprachpaketen mithilfe des Websetup-Assistenten wird ein Fehler ähnlich dem folgenden angezeigt:

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

Wir empfehlen Ihnen [PHP 2 GB Speicher zuzuweisen](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/prerequisites/php-settings) in unserer Entwicklerdokumentation, um sicherzustellen, dass Ihre Installation oder Aktualisierung erfolgreich ist.

Wenn Sie dies bereits getan haben, erstellen Sie eine Auslagerungsdatei auf Ihrem Computer. Ein Linux-Rechner verwendet *Swap-Speicherplatz* wenn er mehr Speicherressourcen benötigt und der RAM voll ist. Der Auslagerungsspeicher wird für inaktive Seiten im Speicher verwendet.

Im Folgenden finden Sie nur Vorschläge. Möglicherweise sind weitere Optionen verfügbar. Wenden Sie sich an einen Netzwerkadministrator oder eine andere sachkundige Ressource, bevor Sie fortfahren. Sie müssen die Befehle ausführen, um eine Auslagerungsdatei als Benutzer mit `root` Berechtigungen zu erstellen.

### Datei auf Ubuntu austauschen {#swap-file-on-ubuntu}

Verwenden Sie den Befehl `fallocate` wie in den folgenden Referenzen erläutert:

* [Hinzufügen von Swap auf Ubuntu 14.04 (DigitalOcean)](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04)
* [Hinzufügen von Auslagerungsspeicher auf Ubuntu 16.04 (DigitalOcean)](https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-16-04)
* [SwapFAQ (help.ubuntu.com)](https://help.ubuntu.com/community/SwapFaq)

### Datei auf CentOS austauschen {#swap-file-on-centos}

Verwenden Sie den Befehl `mkswap` wie in den folgenden Referenzen erläutert:

* [So fügen Sie einen Swap auf CentOS 6 (DigitalOcean) hinzu](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-centos-6)
* [So fügen Sie einen Swap auf CentOS 7 (DigitalOcean) hinzu](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-centos-7)
* [Auslagern von Speicherplatz (RedHat-Kundenportal)](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Storage_Administration_Guide/ch-swapspace.html)
