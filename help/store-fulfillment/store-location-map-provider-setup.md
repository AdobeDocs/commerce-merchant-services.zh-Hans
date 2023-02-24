---
title: 存储位置和映射系统配置
description: 配置距离提供程序以支持店面UI中的存储位置映射。 商店完成解决方案需要一个距离提供商来启用零售商店搜索以及端到端完成工作流程的其他映射和计划功能。
role: User, Admin
level: Intermediate
exl-id: d09c4652-e2eb-49dc-8c42-2aa9b6be5d6b
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# 存储位置和映射设置

通过配置 [距离提供商](https://docs.magento.com/user-guide/catalog/inventory-configure-distance-priority.html) 搜索零售商店位置。

**要求**

在配置过程中，您为Google映射平台提供Google API密钥。 如果你没有， [从Google映射平台生成一个](https://docs.magento.com/user-guide/catalog/inventory-configure-distance-priority.html#configure-google-maps).

要配置距离提供程序，请执行以下操作：

1. 从 **[!UICONTROL Stores > General]** 在“管理员”中，为“地图”内容类型添加Google地图集成。

   - 转到 **[!UICONTROL Stores > Configuration  > General > Content Management]**.

   - 将Google API密钥添加到 **[!UICONTROL Google Maps API Key]** 字段。

1. 从 **[!UICONTROL Stores > Inventory]** 在“管理员”中，选择“商店履行”的距离提供程序。

   - 转到 **[!UICONTROL Stores > Configuration > Catalog > Inventory]**.

   - 展开 **[!UICONTROL Distance Provider for Distance Based SSA]** 中。

   - 设置 **提供程序** to **Google地图**.

1. 配置 **[!UICONTROL Google Distance Provider]**.

   - 添加 **Google API密钥**.

   - 已设置 **[!UICONTROL Computation Mode]** to `Driving` 和 **[!UICONTROL Value]** to `Distance`
