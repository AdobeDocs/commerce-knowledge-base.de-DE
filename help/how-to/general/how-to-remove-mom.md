---
title: So entfernen Sie Magento Order Management (MOM)
description: In diesem Artikel wird erläutert, wie Sie das Magento Order Management-System (MOM) entfernen.
exl-id: 9b2adb30-a880-45a2-859e-be0da42bfd07
source-git-commit: 77f41d6034f985794e5c5b89cc007a69858683b9
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 0%

---

# So entfernen Sie Magento Order Management (MOM)

1. Deaktivieren Sie die MOM-Integration, indem Sie die Schritte unter [Integration deaktivieren oder aktivieren](https://commerce-docs.github.io/oms-documentation-archive/integration/connector/#disable-or-enable-the-integration) befolgen.
1. Deaktivieren Sie das MOM-Modul, indem Sie die Schritte unter [Module deinstallieren](/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html) befolgen.
1. Für die Extraktion vollständiger Bestelldaten bieten wir die API an. Weitere Informationen finden Sie im [Bestellen-Repository](https://commerce-docs.github.io/oms-documentation-archive/specifications/#magento.sales.order_repository) auf unserer Adobe | Magento OMS-Dokumente, die Bestellinformationen abdecken (order_repository). Verwenden Sie den [Abschnitt Spezifikationen](https://commerce-docs.github.io/oms-documentation-archive/specifications/#services) in unserem Adobe | Magento von OMS-Dokumenten zur Verwendung anderer APIs zum Extrahieren verschiedener Informationstypen.
