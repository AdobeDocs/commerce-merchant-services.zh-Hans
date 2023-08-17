---
title: Inventory management源传输
description: “配置库存，用于 [!DNL Store Fulfillment solution] Adobe Commerce Inventory management。 设置新库存并将库存从默认库存中转移，以便您可以将其分配给为启用“商店履行”解决方案所需的商店提货功能而配置的来源。”
role: Admin
level: Intermediate
feature: Shipping/Delivery, Inventory, Configuration
exl-id: 669d4dce-4cac-4bde-acc5-26c70a51f7f1
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---


# Inventory management源传输

此 [!DNL Store Fulfillment] 解决方案使用本机Adobe Commerce Inventory management。 默认情况下， [!DNL Commerce] 配置将所有Web库存分配给默认库存，该库存不能分配其他来源。 由于网站只能分配单个库存，因此商家必须配置新库存，并可以选择将其默认来源库存转移到分配给相应范围的来源。 然后，可以将源分配给新库存。

>[!IMPORTANT]
>
>商家必须维护组和捆绑产品类型中包含的所有产品的默认来源。 这些产品需要满足库存物料的最低数量阈值的库存数量，并且库存状态为 [!UICONTROL In Stock].

这些配置更改可帮助您完成三件事：

1. [将库存转移到来源](https://docs.magento.com/user-guide/catalog/inventory-bulk-transfer-inventory.html) 将库存从默认库存/来源移至新库存/来源。

1. [批量分配源](https://docs.magento.com/user-guide/catalog/inventory-bulk-assign-sources.html) 为所有产品添加新源。

1. [完成产品属性的批量更新](https://docs.magento.com/user-guide/stores/bulk-product-attribute-update.html) 添加 `Allow Store Pickup` 和 `Allow Home Delivery` 属性到现有产品。 安装解决方案时，属性具有最佳值 *默认* 值。 但是，在完成批量更新内容过程之前，这些属性不会应用于现有产品。

库存从所选源（零售商店库位或电子商务仓库）中扣除。 用作电子商务仓库的来源必须分配给与商店取货地点相同的库存，并在零售地点之前排定优先次序。 有关其他信息，请参阅 [设置库存来源的优先级](https://docs.magento.com/user-guide/catalog/inventory-stock-priority.html).

有关管理库存、库存和来源的详细信息，请参阅Adobe Commerce用户文档：

- [管理库存](https://docs.magento.com/user-guide/catalog/inventory-management.html)

- [管理库存数量](https://docs.magento.com/user-guide/catalog/inventory-manage-inventory-quantities.html)

- [管理库存](https://docs.magento.com/user-guide/catalog/inventory-stock.html)

- [管理源](https://docs.magento.com/user-guide/catalog/inventory-sources.html)

- [设置库存来源的优先级](https://docs.magento.com/user-guide/catalog/inventory-stock-priority.html)

- [产品属性的批量更新](https://docs.magento.com/user-guide/stores/bulk-product-attribute-update.html)


>[!IMPORTANT]
>
>更改库存和库存源的配置也会对集成系统产生下游影响。 确保您了解对清单配置的更改如何影响这些系统。
