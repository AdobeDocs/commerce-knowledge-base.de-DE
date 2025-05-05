---
title: Fehler „Maximale Anzahl von Cookies wurde überschritten“ in Adobe Commerce
description: Erfahren Sie, wie Sie das Adobe Commerce-Problem beheben können, bei dem ein Fehler auftritt, der angibt, dass die maximale Anzahl von Cookies überschritten würde.
feature: Deploy, Support, Upgrade, Tools and External Services
role: Admin, Developer
source-git-commit: 44e167c801bbcd313f74c9fc51f9cde9473ef96f
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# *Maximale Anzahl von Cookies würde überschritten* Fehler in Adobe Commerce

Dieser Artikel enthält Patches zur Behebung des Fehlers *Maximale Anzahl von Cookies würde überschritten* in Adobe Commerce.

## Betroffene Produkte und Versionen

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7, mit einem der folgenden Patches:

* MDVA-12304 Patch angewendet mit dem [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/release-notes)
* [APSB25-08 isolierter Sicherheitspatch](/help/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-08.md)
* [Cloud-Patches für  [!DNL Commerce] .1.4](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/release-notes/cloud-patches)

## Problem

Probleme im Zusammenhang mit Cookies in Adobe Commerce führen dazu, dass der folgende Fehler in den Fehlerprotokollen angezeigt wird:

*report.WARNING: Das Cookie kann nicht gesendet werden. Maximale Anzahl an Cookies wird überschritten.*

### Ursache

Das Problem tritt auf, weil die maximale Anzahl der zulässigen Cookies auf *50“* ist.

## Lösung

1. Entfernen Sie das MDVA-12304-Patch, wenn Sie es mit dem [!DNL Quality Patches Tool (QPT)] angewendet haben.

   * Entfernen Sie für Adobe Commerce in der Cloud-Infrastruktur den Patch von `.magento.env.yaml`.
   * Führen Sie bei lokalen Adobe Commerce-Installationen den folgenden Befehl aus, um den Patch rückgängig zu machen:

     `vendor/bin/magento/quality-patches revert MDVA-12304`

1. Wenden Sie die angehängten Patches entsprechend Ihrer Adobe Commerce-Version an:

   * Wenden Sie für die Versionen 2.4.4-p12, 2.4.5-p11, 2.4.6-p9 und 2.4.7-p4 den [ACSD-64710-Patch](assets/acsd-64710_2.4.5-p11.patch.zip) an.

   * Wenden Sie für die Versionen 2.4.4-p13, 2.4.5-p12, 2.4.6-p10, 2.4.7-p5 und 2.4.8 den [ACSD-65562-Patch](assets/acsd-65562_2.4.5-p12.patch.zip) an.

### Verwandtes Lesen

* [Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/upgrade-guide/patches/apply) im Adobe Commerce-Upgrade-Handbuch
* [Best Practices für die skalierte Verteilung von Adobe Commerce-Patches](https://experienceleague.adobe.com/de/docs/commerce-operations/implementation-playbook/best-practices/maintenance/patching-at-scale) im Adobe Commerce-Implementierungs-Playbook
* [Versionshinweise für Commerce Cloud Tools Suite](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/release-notes/cloud-tools-suite) im Handbuch zu Commerce on Cloud.
