---
title: Inventory management源传输
description: “配置 [!DNL Store Fulfillment solution] Adobe Commerce·Inventory management。 设置新库存并从默认库存中转移库存，以便您将其分配给配置为启用“商店完成”解决方案所需的“商店提货”功能的来源。
role: User, Admin
level: Intermediate
exl-id: 669d4dce-4cac-4bde-acc5-26c70a51f7f1
source-git-commit: 42b0118b427b1e04186793b4a57c058bc1cabdd4
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---


# Inventory management源传输

的 [!DNL Store Fulfillment] 解决方案使用本机Adobe Commerce Inventory management。 默认情况下， [!DNL Commerce] 配置会将所有web库存分配给默认库存，而默认库存则无法分配其他来源。 由于网站只能分配一只股票，因此商家必须配置一只新股票，并选择性地将其默认来源库存转移到分配给相应范围的来源。 然后，可将源分配给新库存。

这些配置更改可帮助您完成以下三项任务：

1. [将库存转移到来源](https://docs.magento.com/user-guide/catalog/inventory-bulk-transfer-inventory.html) 将库存从默认库存/来源移至新库存/来源。

1. [批量分配源](https://docs.magento.com/user-guide/catalog/inventory-bulk-assign-sources.html) 添加所有产品的新源。

1. [完成产品属性的批量更新](https://docs.magento.com/user-guide/stores/bulk-product-attribute-update.html) 添加 `Allow Store Pickup` 和 `Allow Home Delivery` 属性。 安装解决方案后，属性会得到最佳 *默认* 值。 但是，在您完成批量更新过程之前，这些属性不会应用于现有产品。

库存将从所选来源（零售商店位置或电子商务仓库）中扣除。 用作电子商务仓库的来源必须分配给与商店提货位置相同的库存，并且在零售位置之前按优先级排列。 有关其他信息，请参阅 [对股票的来源进行优先级排序](https://docs.magento.com/user-guide/catalog/inventory-stock-priority.html).

有关管理库存、库存和来源的更多信息，请参阅Adobe Commerce用户文档：

- [管理库存](https://docs.magento.com/user-guide/catalog/inventory-management.html)

- [管理库存数量](https://docs.magento.com/user-guide/catalog/inventory-manage-inventory-quantities.html)

- [管理库存](https://docs.magento.com/user-guide/catalog/inventory-stock.html)

- [管理源](https://docs.magento.com/user-guide/catalog/inventory-sources.html)

- [对股票的来源进行优先级排序](https://docs.magento.com/user-guide/catalog/inventory-stock-priority.html)

- [产品属性的批量更新](https://docs.magento.com/user-guide/stores/bulk-product-attribute-update.html)


>[!IMPORTANT]
>
>更改库存和库存源的配置也会对集成系统产生下游影响。 确保您了解对库存配置所做的更改对这些系统有何影响。
