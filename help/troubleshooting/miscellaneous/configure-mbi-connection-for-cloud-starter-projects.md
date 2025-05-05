---
title: Konfigurieren der Adobe Commerce Intelligence-Verbindung für bestehende Cloud Starter-Projekte
description: Dieser Artikel bietet eine Lösung für den Fall, dass Sie die Adobe Commerce Intelligence-Verbindung für ein vorhandenes Cloud-Starter-Projekt konfigurieren möchten.
feature: Commerce Intelligence
role: Developer
exl-id: 56f6ad64-729d-4e3a-93a9-da1b91bc5c1d
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '776'
ht-degree: 0%

---

# Konfigurieren der Adobe Commerce Intelligence-Verbindung für bestehende Cloud Starter-Projekte

>[!NOTE]
>
>Adobe Commerce Intelligence hieß früher Magento Business Intelligence (MBI).

Dieser Artikel bietet eine Lösung für den Fall, dass Sie die Adobe Commerce Intelligence-Verbindung für ein vorhandenes Cloud-Starter-Projekt konfigurieren möchten.

## Betroffene Produkte und Versionen

Adobe Commerce on Cloud Starter (alle Versionen)

## Problem

Sie möchten die Commerce Intelligence-Verbindung für ein vorhandenes Cloud Starter-Projekt konfigurieren.

>[!NOTE]
>
>Adobe unterstützt keine neuen Cloud Starter-Abonnements mehr. Wenn Sie jedoch über ein vorhandenes Starter-Projekt verfügen, müssen Sie die folgenden Schritte ausführen, um Ihre Verbindung zu konfigurieren.

## Lösung

Um Commerce Intelligence für Cloud-Einstiegsprojekte zu aktivieren, erstellen Sie ein Commerce Intelligence-Konto, erstellen Sie einen SSH-Schlüssel und stellen Sie schließlich eine Verbindung zu Ihrer Adobe Commerce-Datenbank her.

Führen Sie die folgenden Schritte aus:

1. Erstellen Sie Ihr Adobe Commerce Intelligence-Konto:

   * Navigieren Sie zu [accounts.magento.com/customer/account/login](https://account.magento.com/customer/account/login).
   * Navigieren Sie zu **[!UICONTROL My Account]** > **[!UICONTROL My MBI Instances]**.
   * Klicken Sie auf die **[!UICONTROL Create Instance]**. Wenn diese Schaltfläche nicht angezeigt wird, wenden Sie sich an Ihren Customer Success Manager oder technischen Kundenberater.
   * Wählen Sie Ihr Cloud Starter-Abonnement. Wenn Sie nur über ein Cloud Starter-Abonnement verfügen, wird dies automatisch ausgewählt.
   * Klicken Sie auf **[!UICONTROL Continue]**.
   * Geben Sie Ihre Daten ein, um Ihr Konto zu erstellen.

   ![MBI-Konto erstellen](/help/troubleshooting/miscellaneous/assets/create_mbi_account.png)

   * Wechseln Sie zu Ihrem Posteingang und überprüfen Sie die E-Mail-Adresse.

   ![E-Mail-Adresse überprüfen](/help/troubleshooting/miscellaneous/assets/verify_email_address_mbi.png)

   * Erstellen Sie ein Kennwort.

   ![Kennwort erstellen](/help/troubleshooting/miscellaneous/assets/create_password_mbi.png)

   * Nach der Erstellung Ihres Kontos haben Sie die Möglichkeit, Benutzer zu Ihrem neuen Konto hinzuzufügen. Technische Administratoren können jetzt hinzugefügt werden, um die folgenden Schritte auszuführen.

   ![Benutzer hinzufügen](/help/troubleshooting/miscellaneous/assets/add_users_mbi.png)

1. Geben Sie Informationen über Ihren Store ein, um Ihre Voreinstellungen festzulegen.

   ![Store-Informationen hinzufügen](/help/troubleshooting/miscellaneous/assets/add_store_info_mbi.png)

   Es gibt einige Informationen, die Sie sammeln müssen, bevor Sie Ihre Datenbank für den dritten Schritt im Onboarding-Fluss verbinden können. Sie füllen die *[!UICONTROL Connect your database]* Seite in Schritt 9 aus.

1. Erstellen Sie einen dedizierten Commerce Intelligence-Benutzer.

   * Erstellen Sie einen neuen Benutzer auf [account.adobe.com](https://account.adobe.com/).
   * Wechseln Sie zu [https://accounts.magento.com/customer/account/](https://accounts.magento.com/customer/account/), um Ihr Adobe Commerce-Konto zu generieren.
   * Warum ein neuer Benutzer? Adobe Commerce Intelligence benötigt einen Benutzer, der zum Projekt hinzugefügt wird, um kontinuierlich neue Daten abzurufen, die an das Commerce Intelligence Data Warehouse des Kontos übertragen werden sollen. Dieser Benutzer dient als diese Verbindung. Das Hinzufügen dieses Benutzers zum Projekt erfolgt in Schritt 4.
   * Ein dedizierter Commerce Intelligence-Benutzer soll verhindern, dass der hinzugefügte Benutzer versehentlich deaktiviert oder gelöscht wird, und die Commerce Intelligence-Verbindung beenden.

1. Fügen Sie den neu erstellten Benutzer der primären Umgebung des Projekts als *Mitwirkender“*.

   ![Benutzer als Mitwirkender hinzufügen](/help/troubleshooting/miscellaneous/assets/contributor_user_mbi.png)

1. Commerce Intelligence SSH-Schlüssel abrufen.

   * Navigieren Sie zur Seite **[!UICONTROL Connect your database]** der Benutzeroberfläche &quot;Commerce Intelligence einrichten“ und scrollen Sie nach unten zu **[!UICONTROL Encryption settings]**.
   * Wählen Sie **[!UICONTROL Encryption Type]** für das Feld **[!UICONTROL SSH Tunnel]** aus.
   * Aus dem Dropdown-Menü können Sie den bereitgestellten öffentlichen Magento BI Essentials-Schlüssel kopieren und einfügen.

   ![Verschlüsselungseinstellungen](/help/troubleshooting/miscellaneous/assets/encryption_type_mbi.png)

1. Fügen Sie Ihren neuen öffentlichen Magento BI Essentials-Schlüssel zu dem in Schritt 5 erstellten Commerce Intelligence-Benutzer hinzu.

   * Navigieren Sie zu [accounts.magento.com/customer/account/login](https://account.magento.com/customer/account/login). Melden Sie sich mit Ihren Kontoanmeldeinformationen für den neu erstellten Commerce Intelligence-Benutzer an. Wechseln Sie dann zur Registerkarte **[!UICONTROL Account Settings]** .
   * Scrollen Sie auf der Seite nach unten und erweitern Sie die Dropdown-Liste für SSH-Schlüssel. Klicken Sie dann auf **[!UICONTROL Add a public key]**.

   ![Öffentlichen Schlüssel hinzufügen](/help/troubleshooting/miscellaneous/assets/add_public_key_mbi.png)

   * Fügen Sie den öffentlichen Magento MBI Essentials SSH-Schlüssel von oben hinzu.

   ![Öffentlichen SSH-Schlüssel hinzufügen](/help/troubleshooting/miscellaneous/assets/add_ssh_key_mbi.png)

1. Geben Sie Business Intelligence Essentials-[!DNL MySQL] an.

   * Aktualisieren Sie Ihre `.magento/services.yaml`.

   ```
   mysql:
    type: mysql:10.0
    disk: 2048
    configuration:
        schemas:
            - main
        endpoints:
            mysql:
                default_schema: main
                privileges:
                    main: admin
            mbi:
                default_schema: main
                privileges:
                    main: ro
   ```

   * Aktualisieren Sie Ihre `.magento.app.yaml`.

   ```
   relationships:
            database: "mysql:mysql"
            mbi: "mysql:mbi"
            redis: "redis:redis"
   ```

1. Erhalten Sie Informationen zum Verbinden Ihrer -Datenbank mit Commerce Intelligence.

   Führen Sie `echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 --decode | json_pp` aus, um Informationen zum Verbinden Ihrer Datenbank zu erhalten.

   Sie sollten Informationen ähnlich der folgenden erhalten:

   ```
   "mbi" : [
              {
                 "scheme" : "mysql",
                 "rel" : "mbi",
                 "cluster" : "vfbfui4vmfez6-master-7rqtwti",
                 "query" : {
                    "is_master" : true
                 },
                 "ip" : "169.254.169.143",
                 "path" : "main",
                 "host" : "mbi.internal",
                 "hostname" : "3m7xizydbomhnulyglx2ku4wpq.mysql.service._.magentosite.cloud",
                 "username" : "mbi",
                 "service" : "mysql",
                 "port" : 3306,
                 "password" : "[password]"
              }
           ],
   ```

1. Adobe Commerce-Datenbank verbinden.

   ![Adobe Commerce-Datenbank verbinden](/help/troubleshooting/miscellaneous/assets/connect_magento_database_mbi.png)

   *Eingänge*:

   * Integrationsname: [Wählen Sie einen Namen für Ihre Integration.]
   * Host: `mbi.internal`
   * Port: 3306
   * Benutzername: mbi
   * Kennwort: [Eingabekennwort in der Ausgabe von Schritt 8 angegeben.]
   * Datenbankname: main
   * Tabellenpräfixe: [Lassen Sie das Feld leer, wenn keine Tabellenpräfixe vorhanden sind]

1. [!UICONTROL Timezone Settings] festlegen.

   ![Zeitzoneneinstellungen](/help/troubleshooting/miscellaneous/assets/timezone_settings_mbi.png)

   *Eingänge*

   * Datenbank: Zeitzone: UTC
   * Gewünschte Zeitzone: [Wählen Sie die Zeitzone aus, in der Ihre Daten angezeigt werden sollen.]

1. Abrufen von Informationen zu Ihren Verschlüsselungseinstellungen.

   * Die Projekt-Benutzeroberfläche bietet eine SSH-Zugriffszeichenfolge. Diese Zeichenfolge kann verwendet werden, um die Informationen zu sammeln, die für die Remote-Adresse und den Benutzernamen beim Einrichten der **[!UICONTROL Encryption settings]** benötigt werden. Wählen Sie **[!UICONTROL SSH]** aus, um Ihren Benutzernamen und Ihre Remote-Adresse anzuzeigen. Die Textzeichenfolge vor *@* ist Ihr Benutzername und die Textzeichenfolge nach *@* ist Ihre Remote-Adresse.

   ![Zugriff auf den Site-Master](/help/troubleshooting/miscellaneous/assets/access_site_mbi.png)

1. Eingabeinformationen für Ihre [!UICONTROL Encryption Settings].

   ![Verschlüsselungseinstellungen](/help/troubleshooting/miscellaneous/assets/encryption_type_mbi.png)

   *Eingänge*

   * Verschlüsselungstyp: SSH-Tunnel
   * Remote-Adresse: ssh.us-3.magento.cloud
   * Benutzername: vfbfui4vmfez6-master-7rqtwti—mymagento
   * Port: 22

1. Klicken Sie auf **[!UICONTROL Save Integration]**.
1. Sie haben jetzt erfolgreich eine Verbindung zu Ihrem Commerce Intelligence Essentials-Konto hergestellt.
1. Wenn Sie Adobe Commerce Intelligence Pro-Kunde sind, wenden Sie sich an Ihren Customer Success Manager oder technischen Kundenberater, um die nächsten Schritte zu koordinieren.

## Verwandtes Lesen

[Best Practices zum Ändern von Datenbanktabellen](https://experienceleague.adobe.com/de/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook
