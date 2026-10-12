---
title: So entfernen Sie Magento Order Management (MOM)
description: In diesem Artikel wird erläutert, wie Sie das Magento Order Management-System (MOM) entfernen.
exl-id: 9b2adb30-a880-45a2-859e-be0da42bfd07
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%
---
# So entfernen Sie Magento Order Management (MOM)

1. Deaktivieren Sie die MOM-Integration, indem Sie die Schritte unter [Integration deaktivieren oder aktivieren](https://commerce-docs.github.io/oms-documentation-archive/integration/connector/#disable-or-enable-the-integration) befolgen.
1. Deaktivieren Sie das MOM-Modul, indem Sie die Schritte unter [Module deinstallieren](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html) befolgen.
1. Für die Extraktion vollständiger Bestelldaten bieten wir die API an. Weitere Informationen finden Sie im Abschnitt [Order Repository](https://commerce-docs.github.io/oms-documentation-archive/specifications/#magento.sales.order_repository) in unseren Adobe | Magento OMS-Dokumenten, die Bestellinformationen (order_repository) abdecken. Verwenden Sie den [Abschnitt Spezifikationen](https://commerce-docs.github.io/oms-documentation-archive/specifications/#services) in unseren Adobe | Magento OMS-Dokumenten, um andere APIs zum Extrahieren verschiedener Informationstypen zu verwenden.
