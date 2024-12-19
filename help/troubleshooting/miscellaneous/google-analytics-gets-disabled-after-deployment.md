---
title: Google Analytics werden nach der Bereitstellung deaktiviert
description: In diesem Abschnitt wird eine Lösung für ein typisches Problem beschrieben, das bei der Bereitstellung von Google Analytics auftreten kann.
exl-id: ecf6a277-2dfa-45cf-b86f-9a27f39017f4
feature: Build, Deploy, Variables
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# Google Analytics werden nach der Bereitstellung deaktiviert

In diesem Abschnitt wird eine Lösung für ein typisches Problem beschrieben, das bei der Bereitstellung von Google Analytics auftreten kann.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur, alle Versionen

## Problem

Wenn Sie Ihren Code umgebungsübergreifend bereitstellen, überprüfen die Build- und Bereitstellungsskripte, ob die `master/production/staging`-Verzweigung bereitgestellt wird, damit die Google Analytics aktiviert bleiben. Beim Bereitstellen von Entwicklungs- (oder untergeordneten) Verzweigungen von Master- in Entwicklungsumgebungen (Integration) deaktiviert das Bereitstellungsskript Google Analytics.

## Ursache

Mit dieser Funktion soll sichergestellt werden, dass Entwicklerdaten und -interaktionen nicht an Google Analytics gesendet oder von ihnen verfolgt werden.

## Lösung

Wenn Sie möchten, dass Google Analytics immer aktiviert sind, legen Sie die `ENABLE_GOOGLE_ANALYTICS = true` der Bereitstellungsvariablen fest, wie unter [Bereitstellungsvariablen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#enable_google_analytics) in unserer Entwicklerdokumentation beschrieben.

>[!NOTE]
>
>Wir sind uns bewusst, dass dieser Artikel immer noch branchenübliche Softwarebegriffe enthalten kann, die manche als rassistisch, sexistisch oder repressiv empfinden und die den Leser verletzen, traumatisieren oder unwillkommen machen können. Adobe arbeitet daran, diese Begriffe aus unserem Code, unserer Dokumentation und unseren Benutzererlebnissen zu entfernen.
