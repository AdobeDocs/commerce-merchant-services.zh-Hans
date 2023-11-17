---
title: 将字段组添加到XDM架构
description: 了解如何将特定于Adobe Commerce的字段组添加到XDM架构。
exl-id: 4401bbe7-1ccc-4349-a998-9e9ee9db590f
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: 4a5877d6e1a5c7d840e36f4913306b0c440bbac5
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# 将字段组添加到XDM架构

其中一项 [载入步骤](overview.md#onboarding-steps) 使用 [!DNL Data Connection] 扩展是访问数据流工作区和 [创建数据流](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) 特定于Adobe Commerce的页面。 在创建该数据流时，还必须选择代表您计划摄取的数据的XDM架构。 本主题将为您提供您的XDM架构必须包括的字段组，以成功收集Adobe Commerce提供的数据 [事件](events.md).

1. 如果您还没有XDM架构， [创建](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) 一。 否则， [编辑](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#edit) Adobe Experience Platform UI中现有的XDM架构。

1. [添加](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) 以下特定于Commerce的字段组：

   - 站点搜索
   - 访问网页
   - 用户登录过程
   - 引用键
   - 个人联系人详细信息
   - 商业详细信息
   - Adobe Analytics ExperienceEvent Commerce(如果要将数据发送到Adobe Analytics)
   - 标识映射

   >[!NOTE]
   >
   > 请勿将任何特定于商务的字段组设置为 `Primary identity`. 这样做会将字段标识为必填字段，并且Experience Platform在每个事件中都需要该字段。 如果该字段不存在，则数据摄取失败。

   您的XDM架构现在包含特定于Commerce的字段组，以便从商务收集的数据 [事件](events.md) 在XDM中表示。

1. [创建数据集](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) 基于您创建或更新的架构。

   数据集是用于数据集合的存储和管理结构，通常是表，包含架构（列）和字段（行）。 数据集还包含描述其存储的数据的各个方面的元数据。

1. [创建数据流](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) 并选择包含特定于商务的字段组和相应数据集的XDM架构。

   数据流将收集的数据转发到数据集。 数据根据所选架构在数据集中表示。