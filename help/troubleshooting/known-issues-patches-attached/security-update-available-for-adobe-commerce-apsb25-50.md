---
title: Sicherheitsupdate für Adobe Commerce verfügbar - [!DNL APSB25-50]
promoted: true
description: Wenden Sie einen isolierten Patch an, um  [!DNL critical and important vulnerabilities]  für Adobe Commerce 2.4.8, 2.4.7-p5, 2.4.6-p10, 2.4.5-p12, 2.4.4-p13 und frühere Versionen zu beheben.
feature: Compliance, Security
role: Developer
source-git-commit: 9df7dee77bec7ffe4323f21e44d555338a0b1934
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---

# Sicherheitsupdate für Adobe Commerce verfügbar - [!DNL APSB25-50]

Am 10. Juni 2025 veröffentlichte Adobe ein regelmäßig geplantes Sicherheits-Update für Adobe Commerce und Magento Open Source. Dieses Update behebt [[!DNL critical] und [!DNL important]](https://helpx.adobe.com/de/security/severity-ratings.html) Schwachstellen. Die erfolgreiche Ausnutzung dieser Sicherheitslücken kann zur Umgehung von Sicherheitsfunktionen, zur Berechtigungseskalation und zur Ausführung von beliebigem Code führen.

Weitere Informationen finden Sie im [Adobe-Sicherheitsbulletin ([!DNL APSB25-50]) hier](https://helpx.adobe.com/security/products/magento/apsb25-50.html).

>[!NOTE]
>
>**Um sicherzustellen, dass die im obigen Sicherheitsbulletin aufgeführten Korrekturen für [!DNL CVE-2025-47110] so schnell wie möglich angewendet werden können, hat Adobe auch einen isolierten Patch veröffentlicht, der [!DNL CVE-2025-47110] auflöst. Dadurch können Händler die Fehlerbehebung isoliert anwenden, sodass das Risiko von Verzögerungen aufgrund potenzieller Integrationsprobleme sinkt.**

**Bitte wenden Sie die neuesten Sicherheitsupdates so bald wie möglich an. Andernfalls sind Sie für diese Sicherheitsprobleme anfällig, und Adobe verfügt nur über begrenzte Mittel, um das Problem weiter zu beheben.**

Weitere Informationen über [unseren isolierten Patch-Bereitstellungsprozess finden Sie hier.](https://business.adobe.com/blog/introducing-enhanced-security-patch-deployment-and-communications-in-adobe-commerce)

>[!NOTE]
>
>Für Kunden von Adobe Commerce on Managed Services kann Ihr Customer Success Engineer zusätzliche Anleitungen zum Anwenden des Patches bereitstellen.

>[!NOTE]
>
>Wenden Sie sich an den Support, wenn beim Anwenden des Sicherheits-Patches/isolierten Patches Probleme auftreten.

Zur Erinnerung: Die [ Sicherheitsaktualisierungen für Adobe Commerce finden Sie hier.](https://helpx.adobe.com/de/security/products/magento.html)

## Betroffene Produkte und Versionen

Adobe Commerce (alle Bereitstellungsmethoden):

* 2,4,8
* 2.4.7-P5 und früher
* 2.4.6-P10 und früher
* 2.4.5-P12 und früher
* 2.4.4-P13 und früher

## Probleme

### I. CVE-2025-47110: Speichern von XSS über Server-seitige Template-Injection in Adobe Commerce 2.4.7-p4

<u>Betroffene Produkte und </u>:

Adobe Commerce (alle Bereitstellungsmethoden):

* 2,4,8
* 2.4.7-P5 und früher
* 2.4.6-P10 und früher
* 2.4.5-P12 und früher
* 2.4.4-P13 und früher

<u>Lösung</u>:

Für Adobe Commerce-Versionen:

* 2,4,8
* 2.4.7, 2.4.7-p1, 2.4.7-p2, 2.4.7-p3, 2.4.7-p4, 2.4.7-p5
* 2.4.6, 2.4.6-p1, 2.4.6-p2, 2.4.6-p3, 2.4.6-p4, 2.4.6-p5, 2.4.6-p6, 2.4.6-p7, 2.4.6-p8, 2.4.6-p10
* 2.4.5, 2.4.5-p1, 2.4.5-p2, 2.4.5-p3, 2.4.5-p4, 2.4.5-p5, 2.4.5-p6, 2.4.5-p7, 2.4.5-p8, 2.4.5-p9, 2.4.5-p10, 2.4.5-p11, 2.4.5-p12
* 2.4.4, 2.4.4-p1, 2.4.4-p2, 2.4.4-p3, 2.4.4-p4, 2.4.4-p5, 2.4.4-p6, 2.4.4-p7, 2.4.4-p8, 2.4.4-p9, 2.4.4-p10, 2.4.4-p11, 2.4.4-p12, 2.4.4-p13

**Wenden Sie den folgenden isolierten Patch an oder aktualisieren Sie auf den neuesten Sicherheits-Patch.**

* **[VULN-31609_2.4.x.patch](assets/VULN-31609_2.4.X_patch.zip)**

### II. VULN-31547: XSS in marketplace.magento.com dargestellt + 1-Klick-ATO-Problem mit Auswirkungen auf IMS-Instanzen

<u>Betroffene Produkte und </u>:

Adobe Commerce (alle Bereitstellungsmethoden):

* 2,4,8

<u>Lösung</u>:

Für Adobe Commerce-Versionen:

* 2,4,8

**Wenden Sie den folgenden isolierten Patch an oder aktualisieren Sie auf den neuesten Sicherheits-Patch.**

* **[VULN-31547_2.4.8.patch](assets/VULN-31547_2.4.8_patch.zip)**

## Anbringen des isolierten Pflasters

Entpacken Sie die Datei und [ Sie in unserer Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html?lang=de)Wissensdatenbank die Anleitung „So wenden Sie einen von Adobe bereitgestellten Composer-Patch an“.

## Nur für Adobe Commerce on Cloud-Händler - Ermitteln, ob die isolierten Patches angewendet wurden

Da es nicht einfach möglich ist, zu überprüfen, ob das Problem behoben wurde, sollten Sie überprüfen, ob der [!DNL CVE-2025-47110] isolierte Patch erfolgreich angewendet wurde.

>[!NOTE]
>
><u>Sie können dies tun, indem Sie die folgenden Schritte ausführen und dabei die Datei `VULN-27015-2.4.7_COMPOSER.patch` **als Beispiel**</u> verwenden:

1. [Installieren Sie das Quality Patches Tool](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de).
1. Führen Sie den folgenden Befehl aus:<br>
   ![CVE-2024-34102-tell-if-patch-applied-code](assets/cve-2024-34102-tell-if-patch-applied-code.png)
1. Es sollte eine ähnliche Ausgabe angezeigt werden, bei der VULN-27015 den Status *Angewendet* zurückgibt:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/VULN-27015-2.4.7_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```

<!-- For Step 2:
     ```bash
    vendor/bin/magento-patches -n status |grep "27015\|Status"
     ```
-->

## Sicherheits-Updates

Für Adobe Commerce verfügbare Sicherheitsupdates:

* [Adobe-Sicherheitsbulletin ([!DNL APSB25-50])](https://helpx.adobe.com/security/products/magento/apsb25-50.html)
* [Die neuesten für Adobe Commerce verfügbaren Sicherheits-Updates](https://helpx.adobe.com/de/security/products/magento.html)
