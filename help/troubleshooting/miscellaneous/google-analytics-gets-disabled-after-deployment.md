---
title: Google Analytics werden nach der Implementierung deaktiviert
description: In diesem Thema wird eine Lösung für ein typisches Problem besprochen, das bei der Implementierung mit Google Analytics auftreten könnte.
exl-id: ecf6a277-2dfa-45cf-b86f-9a27f39017f4
feature: Build, Deploy, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# Google Analytics werden nach der Implementierung deaktiviert

In diesem Thema wird eine Lösung für ein typisches Problem besprochen, das bei der Implementierung mit Google Analytics auftreten könnte.

## Betroffene Produkte und Versionen

* Adobe Commerce in der Cloud-Infrastruktur, alle Versionen

## Problem

Bei der Bereitstellung Ihres Codes in allen Umgebungen überprüfen die Build- und Bereitstellungsskripte die `master/production/staging` -Verzweigung bereitgestellt, um die Aktivierung von Google Analytics zu gewährleisten. Bei der Bereitstellung von (oder untergeordneten) Zweigen des Master in Entwicklungsumgebungen (Integration) deaktiviert das Bereitstellungsskript Google Analytics.

## Ursache

Diese Funktion soll sicherstellen, dass Entwicklerdaten und -interaktionen nicht an Google Analytics gesendet oder von diesen nachverfolgt werden.

## Lösung

Wenn Sie möchten, dass Google Analytics immer aktiviert sind, legen Sie die Bereitstellungsvariable fest. `ENABLE_GOOGLE_ANALYTICS = true`, wie unter [Bereitstellen von Variablen](https://devdocs.magento.com/guides/v2.3/cloud/env/variables-deploy.html#enable_google_analytics) in unserer Entwicklerdokumentation.

>[!NOTE]
>
>Wir wissen, dass dieser Artikel immer noch branchenübliche Softwarebegriffe enthalten kann, die einige rassistisch, sexistisch oder unterdrückend finden und die den Leser verletzen, traumatisiert oder unerwünscht machen können. Adobe arbeitet daran, diese Begriffe aus unserem Code, unserer Dokumentation und unseren Benutzererlebnissen zu entfernen.
