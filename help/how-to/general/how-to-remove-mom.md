---
title: Entfernen von Magento Order Managements (MOM)
description: In diesem Artikel wird erläutert, wie Sie das Magento Order Management-System (MOM) entfernen.
exl-id: 9b2adb30-a880-45a2-859e-be0da42bfd07
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 0%

---

# Entfernen von Magento Order Managements (MOM)

1. Deaktivieren Sie die MOM-Integration, indem Sie die Schritte unter [Deaktivieren oder Aktivieren der Integration](/docs/commerce-admin/systems/integrations/mcom.html#disable-or-enable-the-integration) ausführen.
1. Deaktivieren Sie das MOM-Modul, indem Sie die Schritte unter [Module deinstallieren](/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html) ausführen.
1. Zum Extrahieren von vollständigen Bestelldaten bieten wir die API an. Weitere Informationen finden Sie unter [Repository bestellen](https://omsdocs.magento.com/specifications/#magento.sales.order_repository) in unserer Adobe | Magento OMS-Dokumente, die Bestellinformationen (order_repository) abdecken. Verwenden Sie den Abschnitt [Spezifikationen](https://omsdocs.magento.com/specifications/#services) in unserer Adobe. | Magento OMS Docs verwenden, um andere APIs zur Extraktion verschiedener Informationstypen zu verwenden.
