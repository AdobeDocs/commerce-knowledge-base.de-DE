---
title: Sicherheitsupdate für Adobe Systems Commerce verfügbar –[!DNL APSB25-08]
promoted: true
description: Übernehmen eine isolierte Patch zur Korrektur [!DNL critical, important, and moderate vulnerabilities] für Adobe Systems Commerce 2.4.8-beta1, 2.4.7-p3, 2.4.6-p8, 2.4.5-p10, 2.4.4-p11 und frühere Versionen.
feature: Compliance, Security
role: Developer
exl-id: 567e6ad2-704e-461f-a54d-75f6bd96e996
source-git-commit: d669c097767b5855c6bd747a0ab11b3520f405a0
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# Sicherheitsupdate für Adobe Systems Commerce verfügbar –[!DNL APSB25-08]

Am 11. Februar 2025 hat Adobe Systems ein regelmäßig geplantes Sicherheitsupdate für Adobe Systems Commerce und Magento Open Source veröffentlicht. Dieses Update behebt [[!DNL critical, important]und [!DNL moderate]](https://helpx.adobe.com/security/severity-ratings.html) Sicherheitslücken.Die erfolgreiche Ausnutzung dieser Sicherheitslücken kann zur Ausführung von beliebigem Code, zur Umgehung von Sicherheitsfunktionen und zur Ausweitung von Berechtigungen führen. Mehr Informationen finden Sie im [Adobe Systems Security Bulletin ([!DNL APSB25-08]) hier](https://helpx.adobe.com/security/products/magento/apsb25-08.html).

>[!NOTE]
>
>**Um sicherzustellen, dass die im obigen Sicherheitsbulletin aufgelisteten Korrekturen für [!DNL CVE-2025-24434] so schnell wie möglich angewendet werden können, hat Adobe auch einen isolierten Patch veröffentlicht, der [!DNL CVE-2025-24434] auflöst. Dadurch können Händler die Fehlerbehebung isoliert anwenden, sodass das Risiko von Verzögerungen aufgrund potenzieller Integrationsprobleme sinkt.**

**Bitte wenden Sie die neuesten Sicherheitsupdates so bald wie möglich an. Andernfalls sind Sie für diese Sicherheitsprobleme anfällig, und Adobe verfügt nur über begrenzte Mittel, um das Problem weiter zu beheben.**

>[!NOTE]
>
>Wenden Sie sich an den Support, wenn beim Anwenden des Sicherheits-Patches/isolierten Patches Probleme auftreten.

## Betroffene Produkte und Versionen

Adobe Systems Commerce in Cloud-Infrastruktur, Adobe Systems Commerce On-Premises und Magento Open Source:

* 2.4.8-beta1 und früher
* 2.4.7-p3 und früher
* 2.4.6-p8 und frühere Versionen
* 2.4.5-p10 und früher
* 2.4.4-p11 und früher

## Lösung für Adobe Commerce on Cloud, Adobe Commerce On-Premise und Magento Open Source-Software

Um die Sicherheitsanfälligkeit für die betroffenen Produkte und Versionen zu beheben, müssen Sie den [!DNL CVE-2025-24434] isolierten Patch je nach Adobe Commerce/Magento Open Source-Version anwenden.

## Details zu isolierten Patches

Verwenden Sie je nach Adobe Commerce-/Magento Open Source-Version die folgenden angehängten isolierten Patches:

### Für Version 2.4.8-beta1:

* [vuln-28982-2-4-8x-v2-composer-patch.zip](assets/vuln-28982-2-4-8x-v2-composer-patch.zip)

### Für die Versionen 2.4.7, 2.4.7-p1, 2.4.7-p2, 2.4.7-p3:

* [vuln-28982-2-4-7x-v2-composer-patch.zip](assets/vuln-28982-2-4-7x-v2-composer-patch.zip)

### Für die Versionen 2.4.6, 2.4.6-p1, 2.4.6-p2, 2.4.6-p3, 2.4.6-p4, 2.4.6-p5, 2.4.6-p6, 2.4.6-p7, 2.4.6-p8:

* [vuln-28982-2-4-6x-v2-composer-patch.zip](assets/vuln-28982-2-4-6x-v2-composer-patch.zip)

### Für die Versionen 2.4.5, 2.4.5-p1, 2.4.5-p2, 2.4.5-p3, 2.4.5-p4, 2.4.5-p5, 2.4.5-p6, 2.4.5-p7, 2.4.5-p8, 2.4.5-p9, 2.4.5-p10:

* [vuln-28982-2-4-5x-v2-composer-patch.zip](assets/vuln-28982-2-4-5x-v2-composer-patch.zip)

### Für die Versionen 2.4.4, 2.4.4-p1,, 2.4.4-p2, 2.4.4-p3, 2.4.4-p4, 2.4.4-p5, 2.4.4-p6, 2.4.4-p7, 2.4.4-p8, 2.4.4-p9, 2.4.4-p10, 2.4.4-p11:

* [vuln-28982-2-4-4x-v2-composer-patch.zip](assets/vuln-28982-2-4-4x-v2-composer-patch.zip)


## Anbringen des isolierten Pflasters

Entpacken Sie die Datei und lesen Sie Anweisungen unter [So wenden Sie einen Composer an Patch von Adobe Systems](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) in unserem Support-Knowledgebase bereitgestellt.

## Nur für Adobe Systems Commerce on Cloud-Händler - So stellen Sie fest, ob die isolierten Patches angewendet wurden

In Anbetracht der Tatsache, dass es nicht einfach zu überprüfen ist, ob das Problem behoben wurde, sollten Sie überprüfen, ob die [!DNL CVE-2025-24434] isolierte Patch erfolgreich angewendet wurde.

>[!NOTE]
>
><u>Führen Sie dazu die folgenden Schritte aus, verwenden Sie die `VULN-27015-2.4.7_COMPOSER.patch` **Datei als Beispiel**</u>:

1. [Installieren das Qualität Patches Tool](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Führen Sie den folgenden Befehl aus:<br>
   ![CVE-2024-34102-tell-if-Patch-applied-code](assets/cve-2024-34102-tell-if-patch-applied-code.png)
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

* [Adobe-Sicherheitsbulletin ([!DNL APSB25-08])](https://helpx.adobe.com/security/products/magento/apsb25-08.html)
* [Die neuesten Sicherheitsupdates, die für Adobe Systems Commerce verfügbar sind)](https://helpx.adobe.com/security/products/magento.html)