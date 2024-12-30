---
title: Benutzer kann nicht zum Adobe Commerce-Cloud-Projekt hinzugefügt werden
description: Dieser Artikel bietet eine Lösung für den Fall, dass Sie keine Benutzenden zu einem Adobe Commerce-Cloud-Projekt hinzufügen können.
exl-id: 59940916-bf92-4e89-a6f9-bca87c54125c
feature: Cloud, Paas
role: Developer
source-git-commit: af74d944553c34da2ac8343695bca49f971bc4e5
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# Benutzer kann nicht zum Adobe Commerce-Cloud-Projekt hinzugefügt werden

Dieser Artikel bietet eine Lösung für den Fall, dass Sie versuchen, eine Benutzerin bzw. einen Benutzer zu einem Cloud-Projekt hinzuzufügen, dies jedoch fehlschlägt, mit dem Fehler: *Benutzerin bzw. Benutzer XXX ist nicht vorhanden*.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur, [alle unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problem

Dieser Artikel bietet eine Lösung für den Fall, dass Sie keine Benutzenden zu einem Adobe Commerce-Cloud-Projekt hinzufügen können.

## Ursache

Dies ist das erwartete Verhalten. Das Benutzerkonto sollte zunächst unter https://accounts.magento.cloud erstellt und mit dem Adobe-SSO verknüpft werden, damit es als Benutzer zum Projekt hinzugefügt werden kann.

## Lösung

1. Bitten Sie den Benutzer, sich bei seinem Konto unter https://accounts.magento.cloud anzumelden (er muss sich bereits unter dieser E-Mail-Adresse für ein Konto unter adobe.com registriert haben). Das Erstellen/Besitzen eines Kontos unter https://account.adobe.com bedeutet nicht automatisch, dass der Benutzer über ein Konto unter https://accounts.magento.cloud verfügen würde)
Hinweis: Wenn der/die Benutzende vor August 2022 ein Konto auf account.magento.com oder accounts.magento.cloud hatte, hatte er/sie möglicherweise kein Konto bei/auf adobe.com, es sei denn, er/sie hatte es im August 2022 oder später erstellt. Wenn der/die Benutzende ein Adobe-Konto hat und sich nicht anmelden kann, [eine Support-Anfrage senden](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) unter https://experienceleague.adobe.com/home#support und geben Sie die Details an (Problemgrund = User Management).
1. Der Benutzer sollte dann zu https://accounts.magento.cloud gehen.
1. Sobald dies geschehen ist, sollten Sie den Benutzer zum Projekt hinzufügen können. Anweisungen hierzu finden Sie unter [Hinzufügen von Benutzern und Verwalten des Zugriffs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#add-users-and-manage-access) in unserem Handbuch zu Commerce in Cloud-Infrastrukturen.

## Verwandtes Lesen:

* [Verwalten des Benutzerzugriffs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) finden Sie in unserem Handbuch zu Commerce in Cloud-Infrastrukturen .
* [Anmeldung beim Adobe Commerce Support- oder Cloud-Konto nicht möglich](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-to-log-in-to-support-or-cloud-project.html)
