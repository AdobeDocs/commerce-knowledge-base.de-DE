---
title: Konfigurieren von NPM für die Verwendung von PWA Studio
description: '[Progressive Web Apps (PWA) Studio](https://magento.github.io/pwa-studio/) ist ein neues Projekt, das für Adobe Commerce unter Cloud-Infrastrukturen 2.3.x oder höher verfügbar ist. Um PWA Studio verwenden und installieren zu können, müssen Sie die NPM-Paketmanager-Version auf 5.x oder höher festlegen, um Unterstützung für Node.js 8.x zu erhalten. Dies geschieht im Abschnitt „hooks:build“ der Konfigurationsdatei ".magento.app.yaml“.'
exl-id: 3854fc94-e8ad-45d8-bf3e-73462364220d
source-git-commit: 139c2836ba36686357c7a5458a36550c7b1273c1
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Konfigurieren von NPM für die Verwendung von PWA Studio

[Progressive Web Apps (PWA) Studio](https://magento.github.io/pwa-studio/) ist ein neues Projekt, das für Adobe Commerce unter Cloud-Infrastrukturen 2.3.x oder höher verfügbar ist. Um PWA Studio verwenden und installieren zu können, müssen Sie die NPM-Paketmanager-Version auf 5.x oder höher festlegen, um Unterstützung für Node.js 8.x zu erhalten. Dies geschieht im Abschnitt `hooks:build` der `.magento.app.yaml`-Konfigurationsdatei.

## Umwelt und Technologien

* Adobe Commerce auf Cloud-Infrastruktur 2.3.x
* PWA für Adobe Commerce

## NPM-Version festlegen: Schritte

Um die erforderliche NPM-Version festzulegen, geben Sie sie in der `.magento.app.yaml`-Konfigurationsdatei an. Führen Sie die folgenden Schritte aus:

1. Suchen Sie in Ihrer lokalen Entwicklungsumgebung die `.magento.app.yaml`.
1. Öffnen Sie die Datei zur Bearbeitung mit dem Nur-Text-Editor oder der IDE.
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
   >Wenn Sie Node.js in Ihrer Anwendung und nicht nur in Ihrem Build ausführen möchten, fügen Sie die folgenden Befehle hinzu, um Ihren Build-Hook zu ändern:
   > 
   ```
   > echo 'unset NPM_CONFIG_PREFIX' >> .environment
   > echo 'export NO_UPDATE_NOTIFIER=1' >> .environment
   > echo 'export NVM_DIR="$MAGENTO_CLOUD_DIR/.nvm"' >> .environment
   > echo '[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"' >> .environment
   > ```

1. Speichert Änderungen in der Datei.
1. Git überträgt die bearbeitete Datei in Ihre [Integrationsumgebung](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27242).

Die Änderungen treten in Kraft, nachdem Sie die aktualisierte YAML-Datei per Git in die Umgebung übertragen haben.

## Verwandte Dokumentation

* [Anwendungskonfiguration: Erweiterungspunkte](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/hooks-property.html) in unserem Handbuch zu Adobe Commerce in Cloud-Infrastrukturen.
