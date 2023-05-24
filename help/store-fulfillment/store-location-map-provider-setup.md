---
title: 存储位置和映射系统配置
description: 配置距离提供商以支持店面UI中的商店位置映射。 “商店履行”解决方案需要一个距离提供商，以便为端到端履行工作流启用零售商店搜索以及其他映射和计划功能。
role: User, Admin
level: Intermediate
exl-id: d09c4652-e2eb-49dc-8c42-2aa9b6be5d6b
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# 存储位置和映射设置

通过配置，为“存储实施”启用存储位置和映射功能 [距离提供器](https://docs.magento.com/user-guide/catalog/inventory-configure-distance-priority.html) 以搜索零售商店位置。

**要求**

在配置过程中，您将为Google Maps平台提供一个Google API密钥。 如果你没有， [从Google Maps平台生成一个](https://docs.magento.com/user-guide/catalog/inventory-configure-distance-priority.html#configure-google-maps).

要配置距离提供器，请执行以下操作：

1. 从 **[!UICONTROL Stores > General]** 配置中，为“映射”内容类型添加Google映射集成。

   - 转到 **[!UICONTROL Stores > Configuration  > General > Content Management]**.

   - 将您的Google API密钥添加到 **[!UICONTROL Google Maps API Key]** 字段。

1. 从 **[!UICONTROL Stores > Inventory]** 配置中，为“商店履行”选择距离提供方。

   - 转到 **[!UICONTROL Stores > Configuration > Catalog > Inventory]**.

   - 展开 **[!UICONTROL Distance Provider for Distance Based SSA]** 部分。

   - 设置 **提供商** 到 **Google Map**.

1. 配置设置 **[!UICONTROL Google Distance Provider]**.

   - 添加您的 **Google API密钥**.

   - 设置 **[!UICONTROL Computation Mode]** 到 `Driving` 和 **[!UICONTROL Value]** 到 `Distance`
