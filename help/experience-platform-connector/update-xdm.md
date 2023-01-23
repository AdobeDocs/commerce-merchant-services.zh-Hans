---
title: 将字段组添加到XDM架构
description: 了解如何将特定于Adobe Commerce的字段组添加到XDM模式。
exl-id: 4401bbe7-1ccc-4349-a998-9e9ee9db590f
source-git-commit: c9b1d7e34632f7a54544bc6944144b1833ecc5a5
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# 将字段组添加到XDM架构

其中一个 [入门步骤](overview.md#onboarding-steps) 使用Experience Platform连接器是访问数据流工作区和 [创建数据流](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) 是Adobe Commerce的特有。 在创建该数据流时，还必须选择一个XDM架构来表示您计划摄取的数据。 本主题为您提供了XDM架构必须包含的字段组，以成功收集Adobe Commerce店面提供的数据 [事件](events.md).

1. 如果您还没有XDM架构， [创建](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) 一个。 否则， [编辑](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#edit) 您在Adobe Experience Platform UI中的现有XDM架构。

1. [添加](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) 以下特定于商务的字段组：

   - 网站搜索
   - 访问网页
   - 用户登录过程
   - 引用键
   - 个人联系详细信息
   - 商务详细信息
   - Adobe Analytics Experience Event Commerce(如果要将数据发送到Adobe Analytics)
   - 身份映射

   >[!NOTE]
   >
   > 请勿将任何特定于商务的字段组设置为 `Primary identity`. 这样可将字段标识为必填字段，而Experience Platform应在每个事件中显示该字段。 如果该字段不存在，则数据摄取失败。

   您的XDM架构现在包含特定于商务的字段组，以便从商务店面收集的数据 [事件](events.md) 表示在XDM中。

1. [创建数据集](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) 基于您创建或更新的架构。

   数据集是用于数据集合（通常是表）的存储和管理结构，其中包含架构（列）和字段（行）。 数据集还包含描述其存储数据各个方面的元数据。

1. [创建数据流](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) 并选择包含特定于商务的字段组和相应数据集的XDM架构。

   数据流会将收集的数据转发到数据集。 数据基于所选架构在数据集中表示。
