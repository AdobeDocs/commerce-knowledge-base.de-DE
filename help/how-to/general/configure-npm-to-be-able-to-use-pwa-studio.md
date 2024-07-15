---
title: Konfigurieren von NPM für die Verwendung von PWA Studio
description: '"[Progressive Web Apps (PWA) Studio](https://magento.github.io/pwa-studio/) ist ein neues Projekt, das für Adobe Commerce in der Cloud-Infrastruktur 2.3.x oder höher verfügbar ist. Um PWA Studio verwenden und installieren zu können, müssen Sie die NPM Package Manager-Version auf 5.x oder höher setzen, um Unterstützung für Node.js 8.x zu erhalten. Dies geschieht im Abschnitt "hooks:build"der Konfigurationsdatei ".magento.app.yaml".'
exl-id: 3854fc94-e8ad-45d8-bf3e-73462364220d
source-git-commit: 37ac9cca1f876a48092467aa38f2f2f013c83dd9
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Konfigurieren von NPM für die Verwendung von PWA Studio

[Progressive Web Apps (PWA) Studio](https://magento.github.io/pwa-studio/) ist ein neues Projekt, das für Adobe Commerce in der Cloud-Infrastruktur 2.3.x oder höher verfügbar ist. Um PWA Studio verwenden und installieren zu können, müssen Sie die NPM Package Manager-Version auf 5.x oder höher setzen, um Unterstützung für Node.js 8.x zu erhalten. Dies geschieht im Abschnitt `hooks:build` der Konfigurationsdatei `.magento.app.yaml` .

## Umwelt und Technologien

* Adobe Commerce auf Cloud-Infrastruktur 2.3.X
* PWA für Adobe Commerce

## Festlegen der NPM-Version: Schritte

Um die benötigte NPM-Version festzulegen, geben Sie sie in der Konfigurationsdatei `.magento.app.yaml` an. Führen Sie die folgenden Schritte aus:

1. Suchen Sie in Ihrer lokalen Entwicklungsumgebung die Konfigurationsdatei `.magento.app.yaml` .
1. Öffnen Sie die Datei zur Bearbeitung mit Ihrem Texteditor oder Ihrer IDE.
1. Legen Sie die erforderliche Version im Abschnitt `hooks:build` fest. Im folgenden Beispiel ist die Konfiguration so eingestellt, dass NPM v9.5.0 installiert wird, die derzeit höchste verfügbare Version (4. Februar 2019):

   ```yaml
   hooks:
       build: |
           unset NPM_CONFIG_PREFIX
           curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.8/install.sh | bash
           export NVM_DIR="$HOME/.nvm"
           [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
           nvm install 9.5.0
   ```

   >[!NOTE]
   >
   >Wenn Sie Node.JS in Ihrer Anwendung und nicht nur im Build ausführen möchten, fügen Sie die folgenden Befehle hinzu, um Ihren Build-Hook zu ändern:
   > 
   ```
   > echo 'unset NPM_CONFIG_PREFIX' >> .environment
   > echo 'export NO_UPDATE_NOTIFIER=1' >> .environment
   > echo 'export NVM_DIR="$MAGENTO_CLOUD_DIR/.nvm"' >> .environment
   > echo '[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"' >> .environment
   > ```

1. Speichern Sie die Änderungen in der Datei.
1. Git pushen Sie die bearbeitete Datei in Ihre [Integrationsumgebung](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md).

Die Änderungen treten in Kraft, nachdem Sie Git die aktualisierte YAML-Datei in die Umgebung gepusht haben.

## Verwandte Dokumentation

* [Anwendungskonfiguration: hooks](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/hooks-property.html) in unserem Adobe Commerce on Cloud Infrastructure Guide.
