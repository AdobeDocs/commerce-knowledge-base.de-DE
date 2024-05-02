---
title: "B2B: Unternehmen können nicht auf Profilseiten auf der Storefront zugreifen"
description: Dieser Artikel enthält einen Patch für das bekannte B2B-Problem in Adobe Commerce 2.2.4, das sich auf registrierte Unternehmen bezieht, die Fehler auf ihren Kontoseiten im Storefront erhalten.
exl-id: 5f0d81a2-e0a1-487b-8a4f-28b8cb704e32
feature: B2B, Companies
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---

# B2B: Unternehmen können nicht auf Profilseiten auf der Storefront zugreifen

Dieser Artikel enthält einen Patch für das bekannte B2B-Problem in Adobe Commerce 2.2.4, das sich auf registrierte Unternehmen bezieht, die Fehler auf ihren Kontoseiten im Storefront erhalten.

## Problem

Kunden (Unternehmen) können erfolgreich ein Unternehmenskonto auf der Site erstellen, aber die *&quot;Keine solche Entität mit customerId = &quot;* und *&quot;Sie haben noch kein Firmenkonto&quot;* Fehlermeldungen. Sie können auch *&quot;500 Interner Server-Fehler&quot;* beim Versuch, auf die Seite &quot;Unternehmensprofil&quot;zuzugreifen.

## Patch

Um das Archiv mit einem Patch herunterzuladen, klicken Sie auf den folgenden Link:

[MDVA-9013\_EE\_2.2.2\_composer.patch herunterladen](assets/MDVA-9013_EE_2.2.2_composer.patch.zip)

### Kompatible Adobe Commerce-Versionen

Der Patch wurde für erstellt:

* Adobe Commerce vor Ort 2.2.2

Der Patch ist auch mit den folgenden Adobe Commerce-Versionen und -Editionen kompatibel (löst das Problem jedoch möglicherweise nicht):

* Adobe Commerce für Cloud-Infrastruktur von 2.2.0 bis 2.2.4
* Adobe Commerce vor Ort von 2.2.0 bis 2.2.1 und von 2.2.3 bis 2.2.4

## Anwenden des Pflasters

Siehe [Anwenden eines von Adobe bereitgestellten Composer-Patches](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) für Anweisungen.
