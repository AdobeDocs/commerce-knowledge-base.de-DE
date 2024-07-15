---
title: "Bekanntes Problem mit Adobe Commerce 2.4.0: Integrationstests schlagen fehl"
description: Dieser Artikel enthält einen Patch für das Adobe Commerce 2.4.0-Problem, bei dem Integrationstests fehlschlagen, weil die Deklaration von "Dotdigitalgroup\Email\Test\Integration\Model\Sync\Importer\ImporterFailedTest::setUp()"nicht mit PHPUnit 9 kompatibel ist, das für 2.4.0 verwendet wird.
exl-id: 8e0ca2da-81d9-4561-a009-593240f46e41
feature: Integration
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Bekanntes Problem mit Adobe Commerce 2.4.0: Integrationstests schlagen fehl

Dieser Artikel enthält einen Patch für das Adobe Commerce 2.4.0-Problem, bei dem Integrationstests fehlschlagen, weil die Deklaration von `Dotdigitalgroup\Email\Test\Integration\Model\Sync\Importer\ImporterFailedTest::setUp()` nicht mit PHPUnit 9 kompatibel ist, das für 2.4.0 verwendet wird.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.4.0
* Adobe Commerce vor Ort 2.4.0

## Problem

<u>Zu reproduzierende Schritte</u>

Führen Sie Integrationstests für 2.4.0 durch.

<u>Erwartetes Ergebnis</u>

Tests werden bestanden.

<u>Tatsächliches Ergebnis</u>

*PHP Schwerwiegender Fehler: Deklaration von Dotdigitalgroup\\Email\\Test\\Integration\\Model\\Sync\\Importer\\ImporterFailedTest::setUp() muss mit PHPUnit\\Framework\\TestCase::setUp(): void in /var/www/vendor/dotmailer/dotmailer-magento2-extension/Test/Integration/Model/Sync/Importer/ImporterFailedTest.php in Zeile 36* kompatibel sein.

## Lösung

Wenden Sie den in diesem Artikel bereitgestellten Patch an.

## Patch

Der Patch ist an diesen Artikel angehängt. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link:

[BUNDLE-2684-composer.patch](assets/BUNDLE-2684-composer.patch.zip)

### Kompatible Adobe Commerce-Versionen:

Der Patch wurde für erstellt:

* Adobe Commerce auf Cloud-Infrastruktur 2.4.0
* Adobe Commerce vor Ort 2.4.0

## Anwenden des Pflasters

Anweisungen finden Sie unter [Anwenden eines von Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) bereitgestellten Composer-Patches in unserer Support-Wissensdatenbank.

## Attached Files
