---
title: Sicherheitsupdate für Adobe Commerce verfügbar - [!DNL APSB24-73]
promoted: true
description: Wenden Sie einen isolierten Patch an,  [!DNL critical, important, and moderate vulnerabilities]  für Adobe Commerce 2.4.7-p2-, 2.4.6-p7-, 2.4.5-p9-, 2.4.4-p10- und frühere Versionsinstanzen, die nur das Modul ausführen [!DNL B2B]  zu beheben.
feature: Compliance, Security
role: Developer
exl-id: abfde531-6894-4406-a201-e0daa4378afe
source-git-commit: a84c3d296deb49d419be78f454696177a974d923
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Sicherheitsupdate für Adobe Commerce verfügbar - [!DNL APSB24-73]

Am 8. Oktober 2024 veröffentlichte Adobe ein regelmäßig geplantes Sicherheits-Update für Adobe Commerce und [!DNL Adobe Commerce Webhooks Plugin].
Dieses Update behebt [[!DNL critical, important] und  [!DNL moderate]](https://helpx.adobe.com/security/severity-ratings.html) Schwachstellen. Eine erfolgreiche Ausnutzung kann zur Ausführung von beliebigem Code, zum Lesen beliebiger Dateisysteme, zur Umgehung von Sicherheitsfunktionen und zur Erweiterung von Berechtigungen führen. Das Bulletin ist [Adobe-Sicherheitsbulletin ([!DNL APSB24-73])](https://helpx.adobe.com/security/products/magento/apsb24-73.html).

>[!NOTE]
>
>**[!DNL CVE-2024-45115], das im obigen Sicherheitsbulletin aufgeführt ist, gilt nur bei Verwendung des [!DNL B2B].** Um sicherzustellen, dass die Behebung dieser Sicherheitslücke so schnell wie möglich angewendet werden kann, hat Adobe auch einen isolierten Patch veröffentlicht, der [!DNL CVE-2024-45115] behebt.

**Bitte wenden Sie die neuesten Sicherheitsupdates so bald wie möglich an. Wenn Sie dies nicht tun, sind Sie anfällig für diese Sicherheitsprobleme, und Adobe hat nur begrenzte Mittel, um Abhilfe zu schaffen.**

>[!NOTE]
>
>Wenden Sie sich an den Support, wenn beim Anwenden des Sicherheits-Patches/isolierten Patches Probleme auftreten.

## Betroffene Produkte und Versionen

Adobe Commerce on Cloud und Adobe Commerce On-Premise:

* 2.4.7-P2 und früher
* 2.4.6-P7 und früher
* 2.4.5-P9 und früher
* 2.4.4-P10 und früher

B2B:

* 1.4.2-p2 und früher
* 1.3.5-P7 und früher
* 1.3.4-p9 und früher
* 1.3.3-P10 und früher


## Lösung für Adobe Commerce on Cloud und lokale Adobe Commerce-Software

Um die Sicherheitsanfälligkeit für die betroffenen Produkte und Versionen zu beheben, müssen Sie den [!DNL CVE-2024-45115] isolierten Patch anwenden.

## Details zu isolierten Patches

Verwenden Sie das folgende beigefügte isolierte Pflaster:

[vuln-26510-composer-patch.zip](assets/vuln-26510-composer-patch.zip)

## Anbringen des isolierten Pflasters

Entpacken Sie die Datei und [ Sie in unserer Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html)Wissensdatenbank die Anleitung „So wenden Sie einen Composer-Patch von Adobe an“.

## Nur für Adobe Commerce on Cloud-Händler - Ermitteln, ob die isolierten Patches angewendet wurden

Da es nicht einfach möglich ist, zu überprüfen, ob das Problem behoben wurde, sollten Sie überprüfen, ob der [!DNL CVE-2024-45115] isolierte Patch erfolgreich angewendet wurde.

<u>Sie können dies tun, indem Sie die folgenden Schritte ausführen und dabei die Datei `VULN-27015-2.4.7_COMPOSER.patch` **als Beispiel**</u> verwenden:

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

* [Adobe-Sicherheitsbulletin ([!DNL APSB24-73])](https://helpx.adobe.com/security/products/magento/apsb24-73.html)
