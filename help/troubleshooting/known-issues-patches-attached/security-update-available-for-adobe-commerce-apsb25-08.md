---
title: Sicherheitsupdate für Adobe Commerce verfügbar - [!DNL APSB25-08]
promoted: true
description: Wenden Sie einen isolierten Patch an, um  [!DNL critical, important, and moderate vulnerabilities]  für Adobe Commerce 2.4.8-beta1, 2.4.7-p3, 2.4.6-p8, 2.4.5-p10, 2.4.4-p11 und frühere Versionen zu beheben.
feature: Compliance, Security
role: Developer
exl-id: 567e6ad2-704e-461f-a54d-75f6bd96e996
source-git-commit: aba9548c0b5a06ffd0cddce630e53e5664bb9aac
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---

# Sicherheitsupdate für Adobe Commerce verfügbar - [!DNL APSB25-08]

Am 11. Februar 2025 veröffentlichte Adobe ein regelmäßig geplantes Sicherheits-Update für Adobe Commerce und Magento Open Source. Dieses Update behebt [[!DNL critical, important] und  [!DNL moderate]](https://helpx.adobe.com/security/severity-ratings.html) Schwachstellen. Die erfolgreiche Ausnutzung dieser Sicherheitslücken kann zur Ausführung von beliebigem Code, zur Umgehung von Sicherheitsfunktionen und zur Ausweitung von Berechtigungen führen. Weitere Informationen finden Sie im [Adobe-Sicherheitsbulletin ([!DNL APSB25-08]) hier](https://helpx.adobe.com/security/products/magento/apsb25-08.html).

>[!NOTE]
>
>**Um sicherzustellen, dass die im obigen Sicherheitsbulletin aufgelisteten Korrekturen für [!DNL CVE-2025-24434] so schnell wie möglich angewendet werden können, hat Adobe auch einen isolierten Patch veröffentlicht, der [!DNL CVE-2025-24434] auflöst. Dadurch können Händler die Fehlerbehebung isoliert anwenden, sodass das Risiko von Verzögerungen aufgrund potenzieller Integrationsprobleme sinkt.**

**Bitte wenden Sie die neuesten Sicherheitsupdates so bald wie möglich an. Andernfalls sind Sie für diese Sicherheitsprobleme anfällig, und Adobe verfügt nur über begrenzte Mittel, um das Problem weiter zu beheben.**

>[!NOTE]
>
>Wenden Sie sich an den Support, wenn beim Anwenden des Sicherheits-Patches/isolierten Patches Probleme auftreten.

## Betroffene Produkte und Versionen

Adobe Commerce on Cloud Infrastructure, Adobe Commerce On-Premise und Magento Open Source:

* 2.4.8-Beta1 und früher
* 2.4.7-P3 und früher
* 2.4.6-P8 und früher
* 2.4.5-P10 und früher
* 2.4.4-P11 und früher

## Lösung für Adobe Commerce on Cloud, Adobe Commerce On-Premise und Magento Open Source-Software

>[!NOTE]
>
>Dieses Problem wird durch die [neueste Aktualisierung der Cloud-Patches“ ](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/release-notes/cloud-patches#latest). Der Versuch, den isolierten Patch anzuwenden, wenn die Fehlerbehebung bereits im Update der Cloud-Patches vorhanden ist, kann zu Installationsfehlern führen.

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

Entpacken Sie die Datei und [ Sie in unserer Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html)Wissensdatenbank die Anleitung „So wenden Sie einen von Adobe bereitgestellten Composer-Patch an“.

## Nur für Adobe Commerce on Cloud-Händler - Ermitteln, ob die isolierten Patches angewendet wurden

Da es nicht einfach möglich ist, zu überprüfen, ob das Problem behoben wurde, sollten Sie überprüfen, ob der [!DNL CVE-2025-24434] isolierte Patch erfolgreich angewendet wurde.

>[!NOTE]
>
><u>Sie können dies tun, indem Sie die folgenden Schritte ausführen und dabei die Datei `VULN-27015-2.4.7_COMPOSER.patch` **als Beispiel**</u> verwenden:

1. [Installieren Sie das Quality Patches Tool](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
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

* [Adobe-Sicherheitsbulletin ([!DNL APSB25-08])](https://helpx.adobe.com/security/products/magento/apsb25-08.html)
* [Die neuesten für Adobe Commerce verfügbaren Sicherheits-Updates](https://helpx.adobe.com/security/products/magento.html)
