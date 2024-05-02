---
title: Adobe Commerce Recommendations für PHP-Schwachstellen
description: Am 3. September hat das Multi-State Information Sharing and Analysis Center (MS-ISAC) einen Warnhinweis bezüglich mehrerer Verwundbarkeiten herausgegeben, die die beliebige Codeausführung ermöglichen könnten, und eine Empfehlung, dass alle Websites, die PHP verwenden, auf die neueste PHP-Version ASAP aktualisieren sollten ([vollständiger Warnhinweis ist hier verfügbar](https://www.cisecurity.org/advisory/multiple-vulnerabilities-in-php-could-allow-for-arbitrary-code-execution_2019-087/)).
exl-id: 0bc7caab-0b89-463a-a7f2-a7c92df9f84e
feature: Compliance, Recommendations
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 0%

---

# Adobe Commerce Recommendations für PHP-Schwachstellen

Am 3. September hat das Multi-State Information Sharing and Analysis Center (MS-ISAC) eine Warnung bezüglich mehrerer Verwundbarkeiten herausgegeben, die eine beliebige Codeausführung ermöglichen könnten, und eine Empfehlung, dass alle Websites, die PHP verwenden, auf die neueste PHP-Version ASAP aktualisiert werden sollten ([Den vollständigen Warnhinweis finden Sie hier .](https://www.cisecurity.org/advisory/multiple-vulnerabilities-in-php-could-allow-for-arbitrary-code-execution_2019-087/)).

>[!WARNING]
>
>Beachten Sie bei Adobe Commerce zur Cloud-Infrastruktur, dass Service-Upgrades nicht ohne 48-Stunden-Benachrichtigung an unser Infrastrukturteam in die Produktionsumgebung gesendet werden können. Dies ist erforderlich, da wir sicherstellen müssen, dass wir über einen Infrastruktur-Support-Mitarbeiter verfügen, der Ihre Konfiguration innerhalb eines gewünschten Zeitraums mit minimalen Ausfallzeiten in Ihrer Produktionsumgebung aktualisiert. 48 Stunden vor dem Zeitpunkt, zu dem Ihre Änderungen in der Produktion sein müssen [Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) Geben Sie die erforderliche Dienstaktualisierung an und geben Sie den Zeitpunkt an, zu dem die Aktualisierung beginnen soll.

Weitere Informationen zu den Auswirkungen und Schritten für Adobe Commerce-Sites:

**Auf unserem Cloud-Produkt gehosteter Adobe Commerce**

Wenn Sie Adobe Commerce in der Cloud-Infrastruktur verwenden, wenden Sie sich an Ihr Technologieteam, um Adobe Commerce ab einem beliebigen Zeitpunkt neu bereitzustellen\*, um die Vorteile der Aktualisierung nutzen zu können. Wir empfehlen Merchants, diese Neuimplementierung bis zum 30. September abzuschließen, um PCI-Compliance-Probleme zu vermeiden, die aufgrund dieser Schwachstellen am Ende des Monats auftreten können.

Weitere Hinweise zur erneuten Bereitstellung Ihrer Cloud-Site für diese Aktualisierung:

* Wenn Ihre Website noch PHP Version 7.0 verwendet, müssen Sie zuerst auf eine unterstützte PHP-Version aktualisieren, bevor Sie sie erneut bereitstellen, um diese Sicherheitsaktualisierungen nutzen zu können.
* Für 2.1.x/2.2.x finden Sie weitere Informationen zum Aktualisieren von PHP. [here](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html).

\* *Frühere Versionen dieses Artikels und unsere Nachrichten haben den 19. September, aber unsere Teams haben ihre Arbeit schon früher abgeschlossen.*

**Adobe Commerce auf allen anderen Hosting-Lösungen**

Da Adobe Commerce auf PHP angewiesen ist, empfehlen wir allen Merchants, die Adobe Commerce verwenden, die erforderlichen Updates für PHP mit ihrem Hosting-Provider zu überprüfen. Wir empfehlen den Händlern außerdem, diese Überprüfung und alle Aktualisierungen bis zum 30. September abzuschließen, um PCI-Compliance-Probleme zu vermeiden, die aufgrund dieser Schwachstellen am Ende des Monats auftreten können.

Beachten Sie einige zusätzliche Details zu Adobe Commerce zu anderen Hosting-Lösungen:

* Adobe Commerce-Versionen 2.0 oder 1.x, die PHP-Versionen vor 7.1 oder höher verwenden, haben keinen offiziellen PHP-Patch verfügbar. Es wird empfohlen, PHP auf eine unterstützte PHP-Version zu aktualisieren.

Gemäß dem Warnhinweis werden für diese Schwachstelle folgende Patches empfohlen:

* PHP 7.1: [https://www.php.net/ChangeLog-7.php\#7.1.32](https://www.php.net/ChangeLog-7.php#7.1.32)
* PHP 7.2: [https://www.php.net/ChangeLog-7.php\#7.2.22](https://www.php.net/ChangeLog-7.php#7.2.22)
* PHP 7.3: [https://www.php.net/ChangeLog-7.php\#7.3.9](https://www.php.net/ChangeLog-7.php#7.3.9)

Wenn Sie weitere Informationen über PHP und aktuelle Versionen wünschen, können Sie [PHP-Website](https://www.php.net/). Wenn Sie Fragen haben oder weitere Informationen zu Best Practices für die Sicherheit wünschen, besuchen Sie bitte unsere [Handbuch mit Best Practices für die Sicherheit](https://www.adobe.com/content/dam/cc/en/security/pdfs/Adobe-Magento-Commerce-Best-Practices-Guide.pdf).
