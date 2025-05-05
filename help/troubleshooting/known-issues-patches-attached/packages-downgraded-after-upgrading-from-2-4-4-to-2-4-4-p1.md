---
title: Nach dem Upgrade von 2.4.4 auf 2.4.4-p1 heruntergestufte Pakete
description: Dieser Artikel bietet einen Hotfix für das Problem, wenn Händler in Version 2.4.4 den Befehl „composer update“ ausführen und dann die unten aufgeführten Pakete (Module) auf ihre früheren Versionen heruntergestuft werden, die nicht mit Version 2.4.4 kompatibel sind und nur mit Version 2.4.5 und höher verwendet werden sollen.
exl-id: 4ebdbcd7-6905-4647-b071-1e4413455f38
feature: Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 0%

---

# Nach dem Upgrade von 2.4.4 auf 2.4.4-p1 heruntergestufte Pakete

Dieser Artikel enthält einen Hotfix für das Problem, dass Händler mit Version 2.4.4 den Befehl `composer update` ausführen und dann die unten aufgeführten Pakete (Module) auf ihre früheren Versionen heruntergestuft werden, die nicht mit Version 2.4.4 kompatibel sind und nur mit Version 2.4.5 und höher verwendet werden sollen.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.4.4
* Adobe Commerce On-Premises 2.4.4
* Magento Open Source 2.4.4

## Problem

Es gibt zwei Szenarien, wie dieses Problem auftreten kann und wie es reproduziert werden kann:

### Szenario 1

<u>Schritte zur Reproduktion</u>:

Beim Upgrade von 2.4.4 auf 2.4.4-p1 gibt es eine Reihe von Paketen (Modulen), die mit ähnlicher Ausgabe heruntergestuft werden:

```text
Downgrading magento/module-adobe-ims (2.1.4 => 2.1.3)
Downgrading magento/module-adobe-ims-api (2.1.2 => 2.1.1)
Downgrading magento/module-adobe-stock-admin-ui (1.3.2 => 1.3.1)
Downgrading magento/module-adobe-stock-client-api (2.1.2 => 2.1.1)
Downgrading magento/module-adobe-stock-image (1.3.3 => 1.3.2)
Downgrading magento/module-adobe-stock-image-admin-ui (1.3.3 => 1.3.2)
Downgrading magento/module-banner-page-builder (2.2.3 => 2.2.2)
Downgrading magento/module-inventory (1.2.3 => 1.2.2)
Downgrading magento/module-inventory-admin-ui (1.2.3 => 1.2.2-p1)
Downgrading magento/module-inventory-advanced-checkout (1.2.2 => 1.2.1)
Downgrading magento/module-inventory-api (1.2.3 => 1.2.2-p1)
Downgrading magento/module-inventory-bundle-product (1.2.2 => 1.2.1)
Downgrading magento/module-inventory-catalog-api (1.3.3 => 1.3.2)
Downgrading magento/module-inventory-configurable-product-admin-ui (1.2.3 => 1.2.2-p1)
Downgrading magento/module-inventory-configurable-product-frontend-ui (1.0.3 => 1.0.2)
Downgrading magento/module-inventory-import-export (1.2.3 => 1.2.2)
Downgrading magento/module-inventory-in-store-pickup-admin-ui (1.1.2 => 1.1.1)
Downgrading magento/module-inventory-in-store-pickup-frontend (1.1.3 => 1.1.2)
Downgrading magento/module-inventory-in-store-pickup-graph-ql (1.1.2 => 1.1.1)
Downgrading magento/module-inventory-in-store-pickup-sales-admin-ui (1.1.3 => 1.1.2-p1)
Downgrading magento/module-inventory-in-store-pickup-shipping (1.1.2 => 1.1.1)
Downgrading magento/module-inventory-low-quantity-notification (1.2.2 => 1.2.1)
Downgrading magento/module-inventory-low-quantity-notification-api (1.2.2 => 1.2.1-p1)
Downgrading magento/module-inventory-requisition-list (1.2.3 => 1.2.2)
Downgrading magento/module-inventory-sales-admin-ui (1.2.3 => 1.2.2)
Downgrading magento/module-inventory-sales-api (1.2.2 => 1.2.1)
Downgrading magento/module-inventory-shipping-admin-ui (1.2.3 => 1.2.2-p1)
Downgrading magento/module-inventory-source-selection-api (1.4.2 => 1.4.1-p1)
Downgrading magento/module-inventory-wishlist (1.0.2 => 1.0.1)
Downgrading magento/module-page-builder (2.2.3 => 2.2.2)
Downgrading magento/module-re-captcha-checkout-sales-rule (1.1.1 => 1.1.0)
Downgrading magento/module-re-captcha-customer (1.1.3 => 1.1.2)
Downgrading magento/module-re-captcha-frontend-ui (1.1.3 => 1.1.2)
Downgrading magento/module-staging-page-builder (2.2.3 => 2.2.2)
Downgrading magento/module-two-factor-auth (1.1.4 => 1.1.3)
Removing magento/module-admin-adobe-ims (100.4.0)
```

<u>Erwartete Ergebnisse</u>:

Das Upgrade von Version 2.4.4 auf 2.4.4-p1 führt zu den richtigen Paketen (Modulen) für Version 2.4.4-p1.

<u>Tatsächliche Ergebnisse</u>:

Während des Upgrades von Version 2.4.4 auf 2.4.4-p1 werden die Versionen dieser Pakete (Module) heruntergestuft. Diese Meldungen können jedoch ignoriert werden und die Funktionalität wird nicht beeinträchtigt.

### Szenario 2

<u>Schritte zur Reproduktion</u>:

Wenn Händler für Version 2.4.4 den Befehl `composer update` ausführen, werden dieselben Pakete (Module), die oben unter **Szenario 1) aufgeführt sind,** auf ihre neueren Versionen aktualisiert, die nur mit Version 2.4.5 kompatibel sind und nicht mit Version 2.4.4 verwendet werden sollen.

<u>Erwartete Ergebnisse</u>:

Das Upgrade von Version 2.4.4 auf 2.4.4-p1 führt zu den richtigen Paketen (Modulen) für Version 2.4.4-p1.

<u>Tatsächliche Ergebnisse</u>:

Pakete (Module) werden nach dem Upgrade von Version 2.4.4 auf 2.4.4-p1 heruntergestuft.

## Lösung 1: Patch

Der Patch ist diesem Artikel beigefügt. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link: [Download ACPLTSRV-2017-fix.sh.zip](assets/ACPLTSRV-2017-fix.sh.zip)

## Kompatible Adobe Commerce- und Magento Open Source-Versionen:

Der Patch wurde erstellt für:

* Adobe Commerce auf Cloud-Infrastruktur 2.4.4
* Adobe Commerce On-Premises 2.4.4
* Magento Open Source 2.4.4

>[!NOTE]
>
>Der Patch ist mit keiner anderen Adobe Commerce- und Magento Open Source-Version kompatibel.

## Anwenden des Patches

Verwenden Sie das angehängte Bash-Skript {0[&#128279;](assets/ACPLTSRV-2017-fix.sh.zip)ACPLTSRV-2017-fix.sh.zip} als Problemumgehung.

**Genaue Anweisungen zur Verwendung des Skripts:**

### Adobe Commerce auf Cloud-Infrastruktur:

1. Laden Sie die Bash-Skriptdatei `ACPLTSRV-2017-fix.sh` zum lokalen Auschecken Ihrer Cloud-Codebasis herunter.
1. Führen Sie die Bash-Skriptdatei `ACPLTSRV-2017-fix.sh` aus, um die Composer-Dateien lokal zu ändern.
1. Fügen Sie die geänderten Composer-Dateien hinzu und übertragen Sie sie in Ihr Git-Repository.

### On Adobe Commerce oder Magento Open Source On-Premise:

1. Platzieren Sie die Bash-Skript-`ACPLTSRV-2017-fix.sh` im `root`-Ordner Ihrer Adobe Commerce/Magento Open Source 2.4.4-Installation (im selben Ordner wie die `composer.json`).
1. Führen Sie das Bash-Skript mit einem `apply`-Argument aus, um die betroffenen Pakete (Module) auf ihre Version 2.4.4 zu sperren:

   ```bash
   sh ACPLTSRV-2017-fix.sh apply
   ```

1. Führen Sie Composer aktualisiert aus, um die gesperrten Pakete (Module) zu installieren.
1. Sobald Sie bereit sind, auf 2.4.5 oder 2.4.4-p1 zu aktualisieren, führen Sie das Skript mit einem `rollback` Argument aus:

   ```bash
   sh ACPLTSRV-2017-fix.sh rollback
   ```

   Das Überspringen dieses Schritts führt zu Upgrade-Fehlern aufgrund widersprüchlicher Paket- (Modul-)Anforderungen.
1. Nach Abschluss der oben genannten Schritte können Sie mit dem Upgrade beginnen.

## Problemumgehen 2

Die zweite Problemumgehung besteht darin, den `composer update`-Befehl nicht ohne Argumente auszuführen.
