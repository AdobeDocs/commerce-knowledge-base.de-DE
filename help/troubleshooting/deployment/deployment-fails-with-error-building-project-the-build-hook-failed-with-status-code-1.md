---
title: 'Die Bereitstellung schlägt fehl mit „Fehler beim Erstellen des Projekts: Der Build-Hook ist mit Status-Code 1 fehlgeschlagen“'
description: 'In diesem Artikel werden die Ursachen und Lösungen für das Problem mit der Adobe Commerce-Cloud-Infrastruktur behandelt, bei dem die Build-Phase des Bereitstellungsprozesses fehlschlägt, und die Fehlermeldung wird wie folgt zusammengefasst: *„Fehler beim Erstellen des Projekts: Der Build-Hook ist mit Status-Code 1 fehlgeschlagen“*.'
exl-id: add1cdac-dbcb-4c55-8bc2-c1f27e24aadb
feature: Build, Deploy
role: Developer
source-git-commit: 6a880a57c6cafb34fa51706f7bab1e23310bcef7
workflow-type: tm+mt
source-wordcount: '745'
ht-degree: 0%

---

# Die Bereitstellung schlägt fehl mit „Fehler beim Erstellen des Projekts: Der Build-Hook ist mit Status-Code 1 fehlgeschlagen“

In diesem Artikel werden die Ursachen und Lösungen für das Problem mit der Adobe Commerce-Cloud-Infrastruktur behandelt, bei dem die Build-Phase des Bereitstellungsprozesses fehlschlägt, und die Fehlermeldung wird wie folgt zusammengefasst: *„Fehler beim Erstellen des Projekts: Der Build-Hook ist mit Status-Code 1 fehlgeschlagen“*.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur, alle Versionen

## Problem

<u>Schritte zur Reproduktion</u>:

Führen Sie den Trigger der Bereitstellung manuell aus oder indem Sie eine Zusammenführung, einen Push oder eine Synchronisierung Ihrer Umgebung durchführen.

<u>Erwartetes Ergebnis</u>:

Bereitstellung wurde erfolgreich abgeschlossen.

<u>Tatsächliches </u>:

1. Die Erstellungsphase schlägt fehl und der gesamte Bereitstellungsprozess bleibt stecken.
1. Im Bereitstellungsfehlerprotokoll endet die Fehlermeldung mit: *„Fehler beim Erstellen des Projekts: Der Build-Hook ist mit Status-Code 1 fehlgeschlagen. Build &quot;.* abgebrochen

## Ursache

Es gibt mehrere Gründe, warum die Erstellung einer Umgebung fehlschlägt. Normalerweise wird im Bereitstellungsprotokoll eine lange Fehlermeldung angezeigt, in der der erste Teil den Grund genauer beschreiben würde und die Schlussfolgerung *wäre: „Fehler beim Erstellen des Projekts: Der Build-Hook ist mit Status-Code 1 fehlgeschlagen. Build &quot;.* abgebrochen

Wenn Sie sich den ersten problemspezifischen Teil genauer ansehen, können Sie das Problem identifizieren. Im Folgenden finden Sie die gebräuchlichsten und im nächsten Abschnitt finden Sie Lösungen für sie:

* Es ist kein Speicherplatz verfügbar.
* Falsche Konfiguration der ECE-Tools.
* Der Patch, den Sie anwenden möchten, ist nicht mit Ihrer Adobe Commerce-Version kompatibel oder steht in Konflikt mit anderen angewendeten Patches oder Ihren Anpassungen.
* Probleme mit benutzerdefinierten Code-Modulen verhindern eine erfolgreiche Erstellung.

## Lösung

* Stellen Sie sicher, dass ausreichend Speicherplatz vorhanden ist. Informationen zum Überprüfen des verfügbaren Speicherplatzes finden Sie im Artikel [Überprüfen des Festplattenspeichers in der Cloud-Umgebung mithilfe von CLI](/help/how-to/general/check-disk-space-on-cloud-environment-using-cli.md) . Sie können die Protokollordner bereinigen und/oder den Festplattenspeicher erhöhen.
* Stellen Sie sicher, dass ECE-Tools korrekt konfiguriert sind.
* Überprüfen Sie, ob das Problem durch das Patch verursacht wird. Lösen Sie den Konflikt oder wenden Sie sich an den [Adobe Commerce-Support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). Einzelheiten siehe unten.
* Überprüfen Sie, ob das Problem durch die benutzerdefinierte Erweiterung verursacht wird. Lösen Sie den Konflikt oder wenden Sie sich an die Entwickler der Erweiterung, um die Lösung zu erhalten.

Die folgenden Absätze enthalten einige weitere Details.

### Protokolle bereinigen und/oder Speicherplatz vergrößern

Verzeichnisse, die für die Bereinigung berücksichtigt werden sollen:

* `var/log`
* `var/report`
* `var/debug/`
* `var`

Weitere Informationen zum Erhöhen des Festplattenspeichers in der Starterplanarchitektur für Adobe Commerce in Cloud-Infrastrukturen finden Sie unter [Erhöhen des Festplattenspeichers für die Integrationsumgebung in Cloud](/help/how-to/general/increase-disk-space-for-integration-environment-on-cloud.md). Die gleichen Anweisungen können für die Erhöhung des Speicherplatzes von Adobe Commerce in der Cloud Infrastructure Pro Plan Architecture Integration Umgebung verwendet werden. Für Pro Produktion/Staging müssen Sie ein Ticket beim [Adobe Commerce Support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) einreichen und mehr Speicherplatz anfordern. Sie wird jedoch von Platform überwacht. In der Regel müssen Sie sich jedoch nicht mit dieser Aufgabe in der Staging-/Produktionsumgebung der Pro-Architektur befassen, da Adobe Commerce diese Parameter für Sie überwacht und Sie benachrichtigt und/oder vertragsgemäß Maßnahmen ergreift.

### Stellen Sie sicher, dass ECE-Tools korrekt konfiguriert sind

1. Stellen Sie sicher, dass Build-Hooks ordnungsgemäß in der `magento.app.yaml`-Datei definiert sind. Wenn Sie Adobe Commerce 2.2.x verwenden, sollten die Builderhooks wie folgt definiert werden:

   ```yaml
   # We run build hooks before your application has been packaged.
   build: |
       php ./vendor/bin/ece-tools build
   # We run deploy hook after your application has been deployed and started.
   deploy: |
       php ./vendor/bin/ece-tools deploy
   ```

   Verwenden Sie den [Upgrade auf ECE-Tools](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/install-package)-Artikel als Referenz.

1. Stellen Sie sicher, dass das Paket „ECE-tools“ in der `composer.lock`-Datei vorhanden ist, indem Sie den folgenden Befehl ausführen:

   ```bash
   grep '"name": "magento/ece-tools"' composer.lock
   ```

   Wenn sie angegeben werden, würde die Antwort wie im folgenden Beispiel aussehen:

   ```bash
   "name": "magento/ece-tools", "version": "2002.0.20",
   ```

Siehe den Artikel [Upgrade auf ECE-](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/install-package)) als Referenz.

### Verursacht der Patch das Problem?

Wenn es der angewendete Patch ist, der verhindert, dass die Umgebung erfolgreich erstellt wird, wird im Bereitstellungsprotokoll etwas Ähnliches angezeigt:

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

Diese Fehlermeldungen bedeuten, dass der Patch, den Sie anwenden möchten, entweder für eine andere Adobe Commerce-Version erstellt wurde oder mit Ihren Anpassungen oder zuvor angewendeten Patches in Konflikt steht. Versuchen Sie, den Konflikt zu lösen, oder wenden Sie sich an den [Adobe Commerce-Support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Verursacht die Erweiterung das Problem?

Wenn es die benutzerdefinierte Erweiterung ist, die den erfolgreichen Build der Umgebung verhindert, werden der/die im Bereitstellungsprotokoll erwähnte(n) benutzerdefinierte(n) Modulname(n) sowie der durch dieses Modul verursachte spezifische Konflikt angezeigt. Lösen Sie den Konflikt oder wenden Sie sich an die Entwickler der Erweiterung, um die Lösung zu erhalten.

### Sicherstellen, dass Änderungen angewendet werden

Übertragen und übertragen Sie Ihre Änderungen. Dadurch wird die Bereitstellung automatisch Trigger.
