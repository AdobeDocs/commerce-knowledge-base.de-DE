---
title: Schwachstellen in Adobe Commerce Recommendations for PHP
description: Am 3. September hat das Multi-State Information Sharing and Analysis Center (MS-ISAC) einen Warnhinweis bezüglich mehrerer Sicherheitslücken herausgegeben, die die Ausführung von beliebigem Code ermöglichen könnten, und eine Empfehlung, dass alle Websites, die PHP verwenden, so schnell wie möglich auf die neueste PHP-Version aktualisieren sollten ([vollständiger Warnhinweis ist hier verfügbar](https://www.cisecurity.org/advisory/multiple-vulnerabilities-in-php-could-allow-for-arbitrary-code-execution_2019-087/).
exl-id: 0bc7caab-0b89-463a-a7f2-a7c92df9f84e
feature: Compliance, Recommendations
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 0%

---

# Schwachstellen in Adobe Commerce Recommendations for PHP

Am 3. September hat das Multi-State Information Sharing and Analysis Center (MS-ISAC) einen Warnhinweis bezüglich mehrerer Sicherheitslücken herausgegeben, die eine beliebige Codeausführung ermöglichen könnten, und eine Empfehlung, dass alle Websites, die PHP verwenden, so schnell wie möglich auf die neueste PHP-Version aktualisieren sollten ([vollständige Warnung ist hier verfügbar](https://www.cisecurity.org/advisory/multiple-vulnerabilities-in-php-could-allow-for-arbitrary-code-execution_2019-087/)).

>[!WARNING]
>
>Beachten Sie bei Adobe Commerce auf Cloud-Infrastrukturen, dass Service-Upgrades nicht ohne Vorankündigung an unser Infrastrukturteam innerhalb von 48 Geschäftsstunden in die Produktionsumgebung verschoben werden können. Dies ist erforderlich, da wir sicherstellen müssen, dass wir einen Support-Techniker für die Infrastruktur zur Verfügung haben, der Ihre Konfiguration innerhalb eines gewünschten Zeitraums mit minimalen Ausfallzeiten in Ihrer Produktionsumgebung aktualisiert. 48 Stunden vor dem Zeitpunkt, zu dem Ihre Änderungen in der Produktion vorgenommen werden müssen ([&#x200B; ein Support-Ticket &#x200B;](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)), wobei das erforderliche Service-Upgrade detailliert angegeben und der Zeitpunkt angegeben wird, zu dem das Upgrade gestartet werden soll.

Informationen zu Auswirkungen und Schritten für Adobe Commerce Sites finden Sie weiter:

**Adobe Commerce gehostet auf unserem Cloud-Produkt**

Wenn Sie Adobe Commerce in der Cloud-Infrastruktur verwenden, wenden Sie sich bitte an Ihr Technologie-Team, um Adobe Commerce jederzeit neu bereitzustellen, um das Update nutzen zu können.\* Wir empfehlen Händlern, diese erneute Bereitstellung bis zum 30. September abzuschließen, um Probleme mit der PCI-Compliance zu vermeiden, die infolge dieser Sicherheitslücken am Ende des Monats in Kraft treten könnten.

Zusätzliche Hinweise zur erneuten Bereitstellung der Cloud-Site für dieses Update:

* Wenn Ihre Site weiterhin PHP Version 7.0 verwendet, müssen Sie zuerst auf eine unterstützte PHP Version aktualisieren, bevor Sie erneut bereitstellen, um diese Sicherheitsaktualisierungen nutzen zu können.
* Für 2.1.x/2.2.x finden Sie weitere Informationen zum Upgrade von PHP [hier](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html?lang=de).

\* *Frühere Versionen dieses Artikels und unserer Nachricht haben am 19. September begonnen, aber unsere Teams haben ihre Arbeit vor dem Zeitplan beendet.*

**Adobe Commerce auf allen anderen Hosting-Lösungen**

Da Adobe Commerce auf PHP angewiesen ist, empfehlen wir allen Händlern, die Adobe Commerce verwenden, die notwendigen PHP-Updates zusammen mit ihrem Hosting-Anbieter zu überprüfen. Wir empfehlen außerdem, dass Händler diese Überprüfung und alle Aktualisierungen bis zum 30. September abschließen, um Probleme mit der PCI-Compliance zu vermeiden, die infolge dieser Sicherheitslücken am Ende des Monats in Kraft treten könnten.

Bitte beachten Sie einige zusätzliche Informationen für Adobe Commerce zu anderen Hosting-Lösungen:

* Adobe Commerce-Versionen 2.0 oder 1.x, die PHP-Versionen vor 7.1 oder höher verwenden, haben keinen offiziellen PHP-Patch zur Verfügung. Der empfohlene Pfad besteht darin, PHP auf eine unterstützte PHP-Version zu aktualisieren.

Gemäß dem Warnhinweis sollten für diese Sicherheitslücke folgende Patches empfohlen werden:

* PHP 7.1: [https://www.php.net/ChangeLog-7.php\#7.1.32](https://www.php.net/ChangeLog-7.php#7.1.32)
* PHP 7.2: [https://www.php.net/ChangeLog-7.php\#7.2.22](https://www.php.net/ChangeLog-7.php#7.2.22)
* PHP 7.3: [https://www.php.net/ChangeLog-7.php\#7.3.9](https://www.php.net/ChangeLog-7.php#7.3.9)

Wenn Sie weitere Informationen zu PHP und aktuellen Versionen wünschen, besuchen Sie [PHP&#39;s Site](https://www.php.net/). Wenn Sie Fragen haben oder weitere Informationen zu Best Practices für die Sicherheit wünschen, lesen Sie bitte unser [Handbuch zu Best Practices für die Sicherheit](https://www.adobe.com/content/dam/cc/en/security/pdfs/Adobe-Magento-Commerce-Best-Practices-Guide.pdf).
