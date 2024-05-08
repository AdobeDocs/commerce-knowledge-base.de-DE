---
title: Checkliste für die Einrichtung einer neuen [!DNL domain]
description: Dies ist eine Checkliste, wie eine neue [!DNL domain] in Adobe Commerce über die Cloud-Infrastruktur.
exl-id: bfe0582d-2c6d-4814-908f-dfd8c898bef7
feature: Cache
source-git-commit: 625ed2c7ab79f7bca9a979903e97c44c875e607c
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# Checkliste für die Einrichtung einer neuen [!DNL domain]

Dies ist eine Checkliste, wie eine neue [!DNL domain] in Adobe Commerce über die Cloud-Infrastruktur. Sie gilt unabhängig davon, ob Sie einfach versuchen, eine neue Domäne hinzuzufügen oder die aktuelle Domäne durch eine neue zu ersetzen.

## Betroffene Produkte und Versionen

Adobe Commerce zur Cloud-Infrastruktur, [alle unterstützten Versionen](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Einrichten einer neuen Domäne

### Schritt 1: Ist dies für die [!DNL Integration, Staging]oder [!DNL Production environment]?

* **[!DNL Integration]**: [!DNL Custom domains] werden nicht unterstützt. Sie müssen stattdessen diese Methode verwenden: [Mehrere Websites oder Stores einrichten: Lokale Installation konfigurieren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) in unserem Benutzerhandbuch.
* **[!DNL Staging]**: Gehen Sie zu **Schritt 2**.
* **[!DNL Production]**: Gehen Sie zu **Schritt 3**.

### 2. Schritt - [!DNL Staging environment]: sind Sie auf [!DNL Pro] oder [!DNL Starter]?

* **[!DNL Pro]**: **Anfrage senden** , um die Domäne zu [!DNL Fastly, Nginx]und konfigurieren Sie die [!DNL SSL certificate] sowie [!DNL Sendgrid domain], falls erforderlich). Sobald dies konfiguriert wurde, [aktualisieren [!DNL DNS] Konfiguration mit [!DNL development settings]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings).

>[!NOTE]
>
>Sie können die neue [!DNL domain] nach [!DNL Fastly] selbst durch Aktualisierung der Konfiguration im [!DNL Admin] in **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** wie in [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains) in unserem Benutzerhandbuch.
>
>Wenn Sie die Domäne nicht hinzufügen können, kann dies auf einen der folgenden Gründe zurückzuführen sein:
>
>1. Sie migrieren die Domäne in die Cloud-Umgebung, die in Ihrer eigenen konfiguriert wurde. [!DNL Fastly] -Dienst. Senden Sie in diesem Fall eine Anfrage und beantragen Sie die Zuweisung der Domäne.
>1. Sie migrieren die Domäne von Starter zu Pro. Senden Sie in diesem Fall einen Antrag auf weitere Unterstützung.

* **[!DNL Starter]**: [!DNL Custom domains] werden in der Staging-Umgebung nicht unterstützt.

### 3. Schritt - [!DNL Production environment]: sind Sie auf [!DNL Pro] oder [!DNL Starter]?

* **[!DNL Pro]**: **Anfrage senden** , um die Domäne zu [!DNL Fastly, Nginx]und konfigurieren Sie die [!DNL SSL certificate] (als [!DNL Sendgrid domain], falls erforderlich). Sobald dies konfiguriert wurde, fahren Sie mit **Schritt 4**.

>[!NOTE]
>
>Sie können die neue [!DNL domain] nach [!DNL Fastly] selbst durch Aktualisierung der Konfiguration im [!DNL Admin] in **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains) in unserem Benutzerhandbuch.
>
>
>Wenn Sie die Domäne nicht hinzufügen können, kann dies auf einen der folgenden Gründe zurückzuführen sein:
>
>1. Sie migrieren die Domäne von der lokalen in die Cloud-Umgebung, die in Ihrer eigenen konfiguriert wurde. [!DNL Fastly] -Dienst. Senden Sie in diesem Fall eine Anfrage und beantragen Sie die Zuweisung der Domäne.
>1. Sie migrieren die Domäne von Starter zu Pro. Senden Sie in diesem Fall einen Antrag auf weitere Unterstützung.

* **[!DNL Starter]**: Fügen Sie die [!DNL domain] zu Ihrem Projekt in **[!DNL Domains]** tab, dann **Anfrage senden** die **[!DNL ACME Challenge Key]** für die [!DNL SSL certificate].

### Schritt 4: Ist die [!DNL domain] live?

* **JA**: [Aktualisieren Sie die [!DNL DNS] Konfiguration mit [!UICONTROL production] settings](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html#update-dns-configuration-with-production-settings).
* **NO**: [Aktualisieren Sie die [!DNL DNS] Konfiguration mit [!UICONTROL development] settings](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings).

## Verwandtes Lesen

* [Mehrere Websites oder Stores einrichten: Neu hinzufügen [!DNL Domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) in unserem Benutzerhandbuch.
