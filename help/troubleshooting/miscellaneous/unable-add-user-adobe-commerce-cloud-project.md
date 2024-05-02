---
title: Benutzer kann nicht zum Adobe Commerce Cloud-Projekt hinzugefügt werden
description: Dieser Artikel bietet eine Lösung für den Fall, dass Sie einen Benutzer nicht zu einem Adobe Commerce-Cloud-Projekt hinzufügen können.
exl-id: 59940916-bf92-4e89-a6f9-bca87c54125c
feature: Cloud, Paas
role: Developer
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# Benutzer kann nicht zum Adobe Commerce Cloud-Projekt hinzugefügt werden

Dieser Artikel bietet eine Lösung für den Fall, dass Sie versuchen, einen Benutzer zu einem Cloud-Projekt hinzuzufügen. Er schlägt jedoch mit einem Fehler fehl: *Benutzer XXX ist nicht vorhanden*.

## Betroffene Produkte und Versionen

* Adobe Commerce zur Cloud-Infrastruktur, [alle unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problem

Dieser Artikel bietet eine Lösung für den Fall, dass Sie einen Benutzer nicht zu einem Adobe Commerce-Cloud-Projekt hinzufügen können.

## Ursache

Dies ist das erwartete Verhalten. Das Benutzerkonto sollte zunächst unter https://accounts.magento.cloud erstellt und mit seiner Adobe SSO verknüpft werden, damit es als Benutzer zum Projekt hinzugefügt werden kann.

## Lösung

1. Bitten Sie den Benutzer, sich unter https://accounts.magento.cloud bei seinem Konto anzumelden (er muss sich unter dieser E-Mail-Adresse bereits für ein Konto unter adobe.com registriert haben). Das Erstellen/Verwenden eines Kontos unter https://account.adobe.com bedeutet nicht automatisch, dass der Benutzer ein Konto unter https://accounts.magento.cloud haben würde. Hinweis: Wenn der Benutzer vor August 2022 über ein Konto unter account.magento.com oder accounts.magento.cloud verfügte, hatte er möglicherweise kein Konto mit/auf adobe.com, es sei denn, er hätte es im August 2022 oder höher erstellt. Wenn der Benutzer über ein Adobe-Konto verfügt und sich nicht anmelden kann, senden Sie bitte eine E-Mail an [Grp-Magento-HelpCenterLoginIssues@adobe.com](mailto:Grp-Magento-HelpCenterLoginIssues@adobe.com) mit den Details.
1. Der Benutzer sollte dann zu https://accounts.magento.cloud gehen.
1. Danach sollten Sie den Benutzer zum Projekt hinzufügen können. Eine Anleitung finden Sie unter [Benutzer hinzufügen und Zugriff verwalten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#add-users-and-manage-access) in unserem Commerce on Cloud Infrastructure Guide.

## Verwandtes Lesen:

* [Verwalten des Benutzerzugriffs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) in unserem Commerce on Cloud Infrastructure Guide.
* [Anmeldung beim Adobe Commerce-Support- oder Cloud-Konto nicht möglich](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-to-log-in-to-support-or-cloud-project.html)
