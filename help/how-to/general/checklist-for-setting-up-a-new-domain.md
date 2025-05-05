---
title: Checkliste zum Einrichten einer neuen  [!DNL domain]
description: Dies ist eine Checkliste zum Einrichten einer neuen  [!DNL domain]  in Adobe Commerce in der Cloud-Infrastruktur.
exl-id: bfe0582d-2c6d-4814-908f-dfd8c898bef7
feature: Cache
source-git-commit: f7b246088e3580922bd3389b2992e5dd8f97ff7a
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Checkliste zum Einrichten einer neuen [!DNL domain]

In dieser Checkliste wird erläutert, wie Sie in Adobe Commerce eine neue [!DNL domain] in der Cloud-Infrastruktur einrichten. Es gilt unabhängig davon, ob Sie eine neue Domain hinzufügen oder die aktuelle ersetzen. Dies gilt auch nach dem Abrufen einer neuen Staging-Umgebung (siehe Schritt 4).

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur, [alle unterstützten Versionen](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Einrichten einer neuen Domain

### Schritt 1: Ist dies für die [!DNL Integration, Staging] oder [!DNL Production environment]?

* **[!DNL Integration]**: [!DNL Custom domains] werden nicht unterstützt. Sie müssen stattdessen diese Methode verwenden: [Mehrere Websites oder Geschäfte einrichten: Lokale Installation ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html?lang=de#add-new-domains) in unserem Benutzerhandbuch.
* **[!DNL Staging]**: Gehen Sie zu **Schritt 2**.
* **[!DNL Production]**: Gehen Sie zu **Schritt 3**.

### Schritt 2 - [!DNL Staging environment]: Sind Sie auf [!DNL Pro] oder [!DNL Starter]?

* **[!DNL Pro]**: **Senden einer Anfrage**, um die Domain zu [!DNL Fastly, Nginx] hinzuzufügen, und konfigurieren Sie die [!DNL SSL certificate] (sowie ggf. die [!DNL Sendgrid domain]). Nachdem dies konfiguriert wurde, [ Sie die  [!DNL DNS]  mit [!DNL development settings]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=de#update-dns-configuration-with-development-settings).

>[!NOTE]
>
>Sie können sich die neue [!DNL domain] selbst [!DNL Fastly], indem Sie die Konfiguration im [!DNL Admin] in **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** wie in [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html?lang=de#manage-domains) in unserem Benutzerhandbuch aktualisieren.
>
>Wenn Sie die Domain nicht hinzufügen können, kann dies einen der folgenden Gründe haben:
>
>1. Sie migrieren die Domain in die Cloud-Umgebung, die in Ihrem eigenen [!DNL Fastly]-Service konfiguriert wurde. Senden Sie in diesem Fall eine Anfrage und fordern Sie die Delegierung der Domain an.
>1. Sie migrieren die Domain von Starter zu Pro. Reichen Sie in diesem Fall ein Ersuchen um weitere Unterstützung ein.

* **[!DNL Starter]**: [!DNL Custom domains] werden in der Staging-Umgebung nicht unterstützt.

### Schritt 3 - [!DNL Production environment]: Sind Sie auf [!DNL Pro] oder [!DNL Starter]?

* **[!DNL Pro]**: **Senden einer Anfrage**, um die Domain zu [!DNL Fastly, Nginx] hinzuzufügen, und Konfigurieren der [!DNL SSL certificate] (bei Bedarf als [!DNL Sendgrid domain]). Fahren Sie nach der Konfiguration mit **Schritt 4** fort.

>[!NOTE]
>
>Sie können sich die neue [!DNL domain] selbst [!DNL Fastly], indem Sie die Konfiguration in der [!DNL Admin] in **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** **[!UICONTROL Domains]** > [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html?lang=de#manage-domains) in unserem Benutzerhandbuch aktualisieren.
>
>
>Wenn Sie die Domain nicht hinzufügen können, kann dies einen der folgenden Gründe haben:
>
>1. Sie migrieren die Domain von lokal in die Cloud-Umgebung, die in Ihrem eigenen [!DNL Fastly]-Service konfiguriert wurde. Senden Sie in diesem Fall eine Anfrage und fordern Sie die Delegierung der Domain an.
>1. Sie migrieren die Domain von Starter zu Pro. Reichen Sie in diesem Fall ein Ersuchen um weitere Unterstützung ein.

* **[!DNL Starter]**: Fügen Sie auf der Registerkarte **[!DNL Domains]** die [!DNL domain] zu Ihrem Projekt hinzu und **Sie dann eine Anfrage**, um die **[!DNL ACME Challenge Key]** für die [!DNL SSL certificate] anzugeben.

### Schritt 4: Ist der [!DNL domain] aktiv?

* **JA**: [Aktualisieren der  [!DNL DNS] -Konfiguration mit [!UICONTROL production] Einstellungen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html?lang=de#update-dns-configuration-with-production-settings).
* **NEIN**: [Aktualisieren Sie die  [!DNL DNS] -Konfiguration mit [!UICONTROL development] Einstellungen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=de#update-dns-configuration-with-development-settings).

## Verwandtes Lesen

* [Mehrere Websites oder Geschäfte einrichten: Neu hinzufügen [!DNL Domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html?lang=de#add-new-domains) in unserem Benutzerhandbuch.
* [Site aufgrund von Ursprungsverdeckung nicht zugänglich](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/production-site-not-accessible-due-to-origin-cloaking)
