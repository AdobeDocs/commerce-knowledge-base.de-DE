---
title: Gesperrte (ausgegraute) Felder in Commerce Admin
description: Dieser Artikel bietet eine Lösung für den Fall, dass Sie Felder in Commerce Admin nicht ändern können.
exl-id: 5fe0967a-4241-440b-bb0d-429fa5644bbc
feature: Admin Workspace
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# Gesperrte (ausgegraute) Felder in Commerce Admin

Dieser Artikel bietet eine Lösung für Fälle, in denen gesperrte (ausgegraute) Felder in Commerce Admin nicht geändert werden können.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premises 2.3.x, 2.4.x
* Adobe Commerce auf Cloud-Infrastruktur 2.3.x, 2.4.x

## Problem

Nachdem Sie eine Änderung an Ihrer Konfiguration in `app/etc/env.php` oder `app/etc/config.php` gespeichert haben, können Sie die Einstellung in Admin nicht mehr ändern.

<u>Schritte zur Reproduktion</u>:

Hinweis: Dies ist ein Beispiel. Das Problem kann sich auf alle gespeicherten Konfigurationen auswirken.

1. Der Händler speichert seine Anmeldeinformationen für die Versandmethoden mit dem folgenden Befehl im Terminal: `./vendor/bin/ece-tools config:dump`. Dadurch werden die Anmeldeinformationen in der `app/etc/env.php` gespeichert.
1. Der Händler versucht dann später, die Anmeldeinformationen zu ändern.

<u>Erwartete Ergebnisse</u>:

Der Händler kann die Werte in den Admin-Feldeinstellungen festlegen und speichern.

<u>Tatsächliche Ergebnisse</u>:

Die Felder in Admin sind gesperrt oder die Werte können geändert werden, werden aber nicht im Admin gespeichert.

## Ursache

Wenn die Konfiguration in `env.php` oder `config.php` gespeichert wird, können Sie die Einstellung in Admin nicht ändern. Um die Bearbeitung der Einstellung zu ermöglichen, müssen Sie die Konfiguration aus `env.php` oder `config.php` entfernen.

## Lösung

Stellen Sie sicher, dass die Konfiguration nicht in `app/etc/env.php` oder `app/etc/config.php` gespeichert wurde. Wenn es gespeichert wurde, führen Sie die folgenden Schritte aus:

* `config.php` - Entfernen Sie die Einstellung und stellen Sie sie dann erneut bereit.
* `env.php` - Direkt auf dem Server ändern, Einstellung entfernen und `bin/magento app:config:import` ausführen.

## Verwandtes Lesen

* [Exportieren Sie die Konfiguration](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configuration-management/export-configuration) in unserer Entwicklerdokumentation.
* [Festlegen von Konfigurationswerten](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configuration-management/set-configuration-values) in unserer Entwicklerdokumentation.
* [Adobe Commerce auf Cloud-Infrastruktur: Reduzieren Sie Bereitstellungsausfälle mit der Konfigurationsverwaltung](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) in unserer Support-Wissensdatenbank.
