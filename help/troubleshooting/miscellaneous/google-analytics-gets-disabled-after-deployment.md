---
title: Google Analytics wird nach der Bereitstellung deaktiviert
description: In diesem Abschnitt wird eine Lösung für ein typisches Problem beschrieben, das bei der Bereitstellung von Google Analytics auftreten kann.
exl-id: ecf6a277-2dfa-45cf-b86f-9a27f39017f4
feature: Build, Deploy, Variables
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
subfeature_v2:
  - id: adedf3b3-e153-47a3-ae73-b5d65067b544
    internal-label: Build system
  - id: 2191e157-828a-5358-ad69-ebcaa8402915
    internal-label: Variables
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%
---
# Google Analytics wird nach der Bereitstellung deaktiviert

In diesem Abschnitt wird eine Lösung für ein typisches Problem beschrieben, das bei der Bereitstellung von Google Analytics auftreten kann.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur, alle Versionen

## Problem

Wenn Sie Ihren Code umgebungsübergreifend bereitstellen, überprüfen die Build- und Bereitstellungsskripte, ob die `master/production/staging`-Verzweigung bereitgestellt wird, damit Google Analytics aktiviert bleibt. Beim Bereitstellen von Entwicklungs- (oder untergeordneten) Verzweigungen des Masters in Entwicklungsumgebungen (Integration) deaktiviert das Bereitstellungsskript Google Analytics.

## Ursache

Mit dieser Funktion soll sichergestellt werden, dass Entwicklerdaten und -interaktionen nicht an Google Analytics gesendet oder von verfolgt werden.

## Lösung

Wenn Sie möchten, dass Google Analytics immer aktiviert ist, legen Sie die `ENABLE_GOOGLE_ANALYTICS = true` der Bereitstellungsvariablen fest, wie unter [Variablen bereitstellen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#enable_google_analytics) in unserer Entwicklerdokumentation beschrieben.

>[!NOTE]
>
>Wir sind uns bewusst, dass dieser Artikel immer noch branchenübliche Softwarebegriffe enthalten kann, die manche als rassistisch, sexistisch oder repressiv empfinden und die den Leser verletzen, traumatisieren oder unwillkommen machen können. Adobe arbeitet daran, diese Begriffe aus unserem Code, unserer Dokumentation und unseren Benutzererlebnissen zu entfernen.
