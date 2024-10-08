---
title: Sicherheitsupdate für Adobe Commerce - [!DNL APSB24-73]
promoted: true
description: Wenden Sie einen isolierten Patch an, um [!DNL critical, important, and moderate vulnerabilities] für Adobe Commerce 2.4.7-p3, 2.4.6-p8, 2.4.5-p10, 2.4.4-p11 und frühere Versionsinstanzen zu beheben, die nur das [!DNL B2B] Modul ausführen.
feature: Compliance, Security
role: Developer
source-git-commit: 181316dc0bd42feae0a857ff52edd80dbfd492ad
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# Sicherheitsupdate für Adobe Commerce - [!DNL APSB24-73]

Am 08. Oktober 2024 veröffentlichte Adobe ein regelmäßig geplantes Sicherheitsupdate für Adobe Commerce, Magento Open Source und [!DNL Adobe Commerce Webhooks Plugin].
Durch diese Aktualisierung werden [[!DNL critical, important]- und  [!DNL moderate]](https://helpx.adobe.com/security/severity-ratings.html)-Schwachstellen behoben. Eine erfolgreiche Nutzung könnte zu einer willkürlichen Codeausführung, beliebigem Lesen des Dateisystems, Umgehung von Sicherheitsfunktionen und Berechtigungseskalierung führen. Das Bulletin ist [Adobe-Sicherheitsbulletin ([!DNL APSB24-73])](https://helpx.adobe.com/security/products/magento/apsb24-73.html).

>[!NOTE]
>
>**[!DNL CVE-2024-45115], aufgeführt im Sicherheitsbulletin oben, ist nur bei Verwendung des Moduls [!DNL B2B] anwendbar.** Um sicherzustellen, dass die Behebung für diese Verwundbarkeit so schnell wie möglich angewendet werden kann, hat Adobe auch einen Isolated Patch veröffentlicht, der [!DNL CVE-2024-45115] löst.

**Bitte wenden Sie so bald wie möglich die neuesten Sicherheitsupdates an. Wenn Sie dies nicht tun, sind Sie anfällig für diese Sicherheitsprobleme, und Adobe verfügt über begrenzte Mittel zur Behebung von Problemen.**

>[!NOTE]
>
>Wenden Sie sich an Support Services , wenn Probleme beim Anwenden des Sicherheits-Patches/isolierten Patches auftreten.

## Betroffene Produkte und Versionen

Adobe Commerce on Cloud, Adobe Commerce vor Ort und Magento Open Source:

* 2.4.7-p3 und früher
* 2.4.6-p8 und früher
* 2.4.5-p10 und früher
* 2.4.4-p11 und früher

## Lösung für Adobe Commerce auf Cloud, lokal verfügbare Adobe Commerce-Software und Magento Open Source

Um die Verwundbarkeit für die betroffenen Produkte und Versionen zu beheben, müssen Sie den [!DNL CVE-2024-45115] Isolated Patch anwenden.

## Details zum isolierten Patch

Verwenden Sie das folgende angehängte Isolated Patch:

[vuln-25610-composer-patch.zip](assets/vuln-25610-composer-patch.zip)

## Anwenden des isolierten Pflasters

Entpacken Sie die Datei und finden Sie Anweisungen unter [Anwenden eines von Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) bereitgestellten Composer-Patches in unserer Support-Wissensdatenbank.

## Nur für Adobe Commerce on Cloud-Merchants - Ermitteln, ob die isolierten Patches angewendet wurden

Angenommen, es ist nicht einfach zu überprüfen, ob das Problem gepatcht wurde, sollten Sie überprüfen, ob der [!DNL CVE-2024-45115] Isolated Patch erfolgreich angewendet wurde.

<u>Führen Sie dazu die folgenden Schritte aus, indem Sie die Datei `VULN-27015-2.4.7_COMPOSER.patch` **als Beispiel**</u> verwenden:

1. [Installieren Sie das Tool &quot;Qualitätsmuster&quot;](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Führen Sie den Befehl aus:<br>
   ![cve-2024-34102-tell-if-patch-apply-code](assets/cve-2024-34102-tell-if-patch-applied-code.png)
1. Sie sollten die Ausgabe ähnlich der folgenden sehen, bei der VULN-27015 den Status *Angewandt* zurückgibt:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/VULN-27015-2.4.7_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```

<!-- For Step 2:
     ```bash
    vendor/bin/magento-patches -n status |grep "27015\|Status"
     ```
-->

## Sicherheitsaktualisierungen

Für Adobe Commerce verfügbare Sicherheitsupdates:

* [Adobe-Sicherheitsbulletin ([!DNL APSB24-73])](https://helpx.adobe.com/security/products/magento/apsb24-73.html)
