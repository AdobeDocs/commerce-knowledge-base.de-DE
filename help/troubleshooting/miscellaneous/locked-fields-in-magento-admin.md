---
title: Gesperrte Felder in Commerce Admin
description: Dieser Artikel bietet eine Lösung für Fälle, in denen Sie keine Felder in Commerce Admin ändern können.
exl-id: 5fe0967a-4241-440b-bb0d-429fa5644bbc
feature: Admin Workspace
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# Gesperrte Felder in Commerce Admin

Dieser Artikel bietet eine Lösung für Fälle, in denen Sie keine Felder in Commerce Admin ändern können.

## Betroffene Produkte und Versionen

* Adobe Commerce lokal 2.3.x, 2.4.x
* Adobe Commerce auf Cloud-Infrastruktur 2.3.x, 2.4.x

## Problem

Nachdem Sie eine Änderung an Ihrer Konfiguration in `app/etc/env.php` oder `app/etc/config.php`festgelegt ist, können Sie die Einstellung in Admin nicht ändern.

<u>Zu reproduzierende Schritte</u>:

Hinweis: Dies ist ein Beispiel. Das Problem kann sich auf alle gespeicherten Konfigurationen auswirken.

1. Der Händler speichert die Anmeldeinformationen seiner Versandmethoden mit dem folgenden Befehl im Terminal: `./vendor/bin/ece-tools config:dump`. Dadurch werden die Anmeldeinformationen im `app/etc/env.php` -Datei.
1. Der Händler versucht dann, die Anmeldedaten später zu ändern.

<u>Erwartete Ergebnisse</u>:

Der Händler kann die Werte in den Admin-Feldeinstellungen festlegen und speichern.

<u>Tatsächliche Ergebnisse</u>:

Die Felder im Admin sind gesperrt oder die Werte können geändert werden, werden aber nicht in Admin gespeichert.

## Ursache

Wenn die Konfiguration in gespeichert wird `env.php` oder `config.php`festgelegt ist, können Sie die Einstellung in Admin nicht ändern. Um die Bearbeitung der Einstellung zu ermöglichen, müssen Sie die Konfiguration aus `env.php` oder `config.php`.

## Lösung

Stellen Sie sicher, dass die Konfiguration nicht in gespeichert wurde. `app/etc/env.php` oder `app/etc/config.php`. Wenn es gespeichert wurde, führen Sie die folgenden Schritte aus:

* `config.php` - Entfernen Sie die Einstellung und stellen Sie sie dann erneut bereit.
* `env.php` - Ändern Sie diese Einstellung direkt auf dem Server und entfernen Sie die Einstellung, und führen Sie dann `bin/magento app:config:import`.

## Verwandte Informationen

* [Konfiguration exportieren](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-config-mgmt-export.html#sensitive-or-system-specific-settings) in unserer Entwicklerdokumentation.
* [Konfigurationswerte festlegen](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-config-mgmt-set.html#config-cli-config-set) in unserer Entwicklerdokumentation.
* [Adobe Commerce über Cloud-Infrastruktur: Reduzieren Sie Bereitstellungsausfälle mit Configuration Management](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) in unserer Wissensdatenbank.
