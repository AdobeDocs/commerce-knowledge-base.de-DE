---
title: '"Bereitstellung schlägt mit "Fehler beim Erstellen des Projekts: Der Build-Hook ist mit Status-Code 1 fehlgeschlagen"'
description: '"In diesem Artikel werden die Ursachen und Lösungen für die Adobe Commerce im Zusammenhang mit Cloud-Infrastrukturproblemen erläutert, bei denen die Build-Phase des Implementierungsprozesses fehlschlägt, und die Fehlermeldung wird wie folgt zusammengefasst: *"Fehler beim Erstellen des Projekts: Der Build-Erweiterungspunkt ist mit Status-Code 1 fehlgeschlagen"*."'
exl-id: add1cdac-dbcb-4c55-8bc2-c1f27e24aadb
feature: Build, Deploy
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '750'
ht-degree: 0%

---

# Die Bereitstellung schlägt mit &quot;Fehler beim Erstellen des Projekts: Der Build-Hook ist mit Status-Code 1 fehlgeschlagen.

In diesem Artikel werden die Ursachen und Lösungen für die Adobe Commerce zum Problem der Cloud-Infrastruktur erläutert, bei dem die Build-Phase des Implementierungsprozesses fehlschlägt und die Fehlermeldung mit &quot;*&quot;Fehlererstellungsprojekt: Der Build-Erweiterungspunkt schlägt mit Status-Code 1 fehl&quot;*.

## Betroffene Produkte und Versionen

* Adobe Commerce in der Cloud-Infrastruktur, alle Versionen

## Problem

<u>Zu reproduzierende Schritte</u>:

Führen Sie einen manuellen Trigger der Bereitstellung durch oder führen Sie eine Zusammenführung, Push-Benachrichtigung oder Synchronisation der Umgebung durch.

<u>Erwartetes Ergebnis</u>:

Die Implementierung wurde erfolgreich abgeschlossen.

<u>Tatsächliches Ergebnis</u>:

1. Die Bauphase schlägt fehl, und der gesamte Implementierungsprozess wird blockiert.
1. Im Fehlerprotokoll der Bereitstellung endet die Fehlermeldung mit: *&quot;Fehler beim Erstellen des Projekts: Der Build-Hook ist mit Status-Code 1 fehlgeschlagen. Build abgebrochen&quot;.*

## Ursache

Es gibt mehrere Gründe, warum die Umgebungserstellung fehlschlägt. Normalerweise wird im Bereitstellungsprotokoll eine lange Fehlermeldung angezeigt, in der der erste Teil genauer auf den Grund verweist und der Schluss *&quot;Fehler beim Erstellen des Projekts: Der Build-Hook ist mit Status-Code 1 fehlgeschlagen. Build abgebrochen&quot;.*

Wenn Sie sich näher mit dem ersten problemspezifischen Teil befassen, können Sie das Problem erkennen. Im Folgenden finden Sie die häufigsten Lösungen, und im nächsten Abschnitt finden Sie Lösungen für diese:

* Es ist kein Speicherplatz verfügbar.
* Falsche ECE-Tools-Konfiguration.
* Der Patch, den Sie anwenden möchten, ist nicht mit Ihrer Adobe Commerce-Version kompatibel oder steht in Konflikt mit anderen angewendeten Patches oder Ihren Anpassungen.
* Probleme mit benutzerdefiniertem Modulcode verhindern die erfolgreiche Erstellung.

## Lösung

* Stellen Sie sicher, dass genügend Speicher vorhanden ist. Informationen zum Überprüfen des verfügbaren Speicherplatzes finden Sie im Artikel [Überprüfen des Festplattenspeichers in der Cloud-Umgebung mithilfe von CLI](/help/how-to/general/check-disk-space-on-cloud-environment-using-cli.md) . Sie können erwägen, die Protokollverzeichnisse zu bereinigen und/oder den Speicherplatz zu erhöhen.
* Stellen Sie sicher, dass die ECE-Tools korrekt konfiguriert sind.
* Überprüfen Sie, ob der Patch das Problem verursacht. Beheben Sie den Konflikt oder kontaktieren Sie den [Adobe Commerce-Support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). Weitere Informationen finden Sie unten.
* Überprüfen Sie, ob das Problem von der benutzerdefinierten Erweiterung verursacht wird. Lösen Sie den Konflikt oder kontaktieren Sie die Entwickler der Erweiterung für die Lösung.

Die folgenden Absätze bieten einige weitere Details.

### Logs bereinigen und/oder Platz vergrößern

Für die Bereinigung zu berücksichtigende Verzeichnisse:

* `var/log`
* `var/report`
* `var/debug/`
* `var`

Weitere Informationen zur Erhöhung des Festplattenspeichers, wenn Sie sich in der Adobe Commerce-Planarchitektur für Cloud-Infrastruktur-Starter befinden, finden Sie unter [Erhöhen des Festplattenspeichers für die Integrationsumgebung in Cloud](/help/how-to/general/increase-disk-space-for-integration-environment-on-cloud.md). Dieselbe Anleitung kann für die Erhöhung des Speicherplatzes von Adobe Commerce in der Cloud Infrastructure Pro Plan-Architekturintegrationsumgebung verwendet werden. Für Pro Production/Staging müssen Sie ein Ticket an den [Adobe Commerce-Support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) senden und mehr Speicherplatz anfordern. Aber es wird von Platform überwacht. In der Regel müssen Sie dies jedoch nicht in der Staging-/Produktions-Architektur von Pro behandeln, da Adobe Commerce diese Parameter für Sie überwacht und Sie benachrichtigt und/oder gemäß dem Vertrag Maßnahmen ergreift.

### Sicherstellen, dass ECE-Tools korrekt konfiguriert sind

1. Stellen Sie sicher, dass Build-Hooks in der Datei &quot;`magento.app.yaml`&quot;ordnungsgemäß definiert sind. Wenn Sie Adobe Commerce 2.2.X verwenden, sollten Sie Hooks wie folgt erstellen:

   ```yaml
   # We run build hooks before your application has been packaged.
   build: |
       php ./vendor/bin/ece-tools build
   # We run deploy hook after your application has been deployed and started.
   deploy: |
       php ./vendor/bin/ece-tools deploy
   ```

   Verwenden Sie den Artikel [Aktualisieren auf ece-tools](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/install-package) als Referenz.

1. Stellen Sie sicher, dass das ECE-Tools-Paket in der Datei `composer.lock` vorhanden ist, indem Sie den folgenden Befehl ausführen:    <pre><code class="language-bash">grep &#39;<code class="language-yaml">&quot;name&quot;: &quot;magento/ece-tools&quot;</code>&#39; composer.lock</code></pre>    Wenn sie angegeben werden, würde die Antwort wie im folgenden Beispiel aussehen:    ```bash    "name": "magento/ece-tools",    "version": "2002.0.20",    ```

Weitere Informationen finden Sie im Artikel [Aktualisierung auf ece-tools](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/install-package) .

### Wird das Problem durch den Patch verursacht?

Wenn es der angewendete Patch ist, der die erfolgreiche Erstellung der Umgebung verhindert, wird im Bereitstellungsprotokoll Folgendes angezeigt:

```bash
%patch_name%.composer.patch
[2019-02-19 18:12:59] CRITICAL:
....
[2019-02-19 18:12:59] CRITICAL: Command git apply --check --reverse /app/m2-hotfixes/%patch_name%.composer.patch returned code 1
...
W:
W: Command git apply --check --reverse /app/m2-hotfixes/%patch_name%.composer.patch returned code 1
W:
W:
W: build
...
E: Error building project: The build hook failed with status code 1. Aborted build.
```

Diese Fehlermeldungen bedeuten, dass der Patch, den Sie anwenden möchten, entweder für eine andere Adobe Commerce-Version erstellt wurde oder Konflikte mit Ihren Anpassungen oder zuvor angewendeten Patches aufweist. Versuchen Sie, den Konflikt zu lösen, oder kontaktieren Sie den [Adobe Commerce-Support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Wird das Problem durch die Erweiterung verursacht?

Wenn es die benutzerdefinierte Erweiterung ist, die die erfolgreiche Erstellung der Umgebung verhindert, werden die im Bereitstellungsprotokoll erwähnten Namen des benutzerdefinierten Moduls(s) sowie der von diesem Modul verursachte Konflikt angezeigt. Lösen Sie den Konflikt oder kontaktieren Sie die Entwickler der Erweiterung für die Lösung.

### Vergewissern Sie sich, dass die Änderungen angewendet werden

Übernehmen Sie Ihre Änderungen und übertragen Sie sie. Dadurch wird die Bereitstellung automatisch Trigger.
