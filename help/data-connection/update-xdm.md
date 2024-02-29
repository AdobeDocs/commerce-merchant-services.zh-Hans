---
title: 更新Commerce数据摄取的时间系列事件架构
description: 了解如何创建架构、数据集和数据流，以收集和发送用于Commerce数据提取的时间序列事件数据。
exl-id: 4401bbe7-1ccc-4349-a998-9e9ee9db590f
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: 99d1097b98ea18c8a317613b2366a97db131432f
workflow-type: tm+mt
source-wordcount: '978'
ht-degree: 0%

---

# 更新Commerce数据摄取的时间系列事件架构

其中一项 [载入步骤](overview.md#onboarding-steps) 使用 [!DNL Data Connection] 扩展是访问数据流工作区和 [创建数据流](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) 特定于Adobe Commerce的页面。 在创建该数据流时，还必须选择描述您计划摄取的数据的架构。 该架构必须包含特定于商务的字段组。

本文为您提供了架构必须包含的字段组，以便成功收集由Adobe Commerce事件提供的以下时间序列数据：

- [行为](events.md)  — 包括storefront、profile、search和B2B事件。
- [后台](events-backoffice.md)  — 包括订单状态和配置文件事件。

了解有关 [时间序列数据](data-ingestion.md).

了解关于 [模式组合基础](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html).

## 使用时间序列行为和后台事件数据更新模式

在此部分中，您将了解如何更新现有模式或创建模式以包含行为和后台事件数据。

>[!NOTE]
>
>请参阅 [时间序列配置文件事件数据](#time-series-profile-event-data) 以了解如何添加特定于用户档案的字段。

1. 如果您还没有架构， [创建](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) 类设置为 **体验事件**.

1. [添加](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) 以下特定于Commerce的字段组（或者编辑您的现有架构并添加这些字段组）：

   - 站点搜索
   - 访问网页
   - 用户登录过程
   - 引用键
   - 个人联系人详细信息
   - 渠道详细信息
   - 商业详细信息
   - Adobe Analytics ExperienceEvent Commerce(如果要将数据发送到Adobe Analytics)

   >[!NOTE]
   >
   > 请勿将任何特定于商务的字段组设置为 `Primary identity`. 这样做会将字段标识为必填字段，并且Experience Platform在每个事件中都需要该字段。 如果该字段不存在，则数据摄取失败。

   您的架构现在包含特定于Commerce的字段组，以便从Commerce收集的时间系列数据 [行为](events.md) 和 [后台](events-backoffice.md) 事件在架构中呈现。

1. [启用](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#profile) 配置文件的架构。

   为配置文件启用某个架构后，从该架构创建的任何数据集都将参与Real-Time CDP，后者将合并来自不同源的数据，以构建每个客户的完整视图。

1. [创建数据集](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) 基于您创建或更新的架构。

   数据集是用于数据集合的存储和管理结构，通常是包含架构（列）和字段（行）的表。 数据集还包含描述其存储的数据的各个方面的元数据。

1. [创建数据流](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) 并选择包含特定于Commerce的字段组和相应数据集的架构。

   数据流将收集的数据转发到数据集。 数据根据所选架构在数据集中表示。

1. **测试版** （可选）如果要将自定义后台事件数据从Commerce实例传递到Experience Platform，则可以使用自定义属性。 此功能处于测试阶段。 如果您想加入Beta计划，请发送请求至 [dataconnection@adobe.com](mailto:dataconnection@adobe.com). 在您的请求中，包含以下内容：

   - 您的 [Adobe组织ID](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255). 例如 `organization_id@AdobeOrg`.
   - 订单级别自定义属性的列表。
   - 订单物料层属性的列表。

   Adobe Commerce团队将与您联系以了解更多信息和后续步骤。

通过为行为数据和后台数据配置架构、数据集和数据流，您可以 [配置](connect-data.md#data-collection) 您的Commerce实例，以收集该数据并将其发送到Experience Platform。

要包含购物者的配置文件信息，请参阅下一部分。

## 时间序列配置文件事件数据

时间序列配置文件事件数据由以下事件生成：

- [&#39;帐户已创建&#39;](events-backoffice.md#accountcreated)
- [&#39;帐户已更新&#39;](events-backoffice.md#accountupdated)
- [&#39;帐户已删除&#39;](events-backoffice.md#accountdeleted)

如果要将客户的配置文件事件数据摄取到Experience Platform中，您可以更新现有的Commerce架构并使用已配置的相同数据流，也可以创建特定于配置文件的数据流和架构。 该决策基于贵公司的数据治理。 下面两个部分将介绍这两种情况。

### 使用现有数据流将时间序列配置文件事件数据发送到Experience Platform

如果要添加时间序列 [服务器端配置文件事件数据](events-backoffice.md#customer-profile-events-server-side) 到您现有的Commerce数据流，添加 `Demographic Details` 字段组添加到您的架构。 您的架构现在包含以下特定于Commerce的字段组：

- 站点搜索
- 访问网页
- 用户登录过程
- 引用键
- 个人联系人详细信息
- 渠道详细信息
- 商业详细信息
- Adobe Analytics ExperienceEvent Commerce(如果要将数据发送到Adobe Analytics)
- 新增： **人口统计详细信息**

添加了 `Demographic Details` 字段组时，已与Commerce架构关联的数据集和数据流将用于此时间序列配置文件数据。

### 将时间序列配置文件事件数据发送到单独的数据流中Experience Platform

如果要添加 [服务器端配置文件事件数据](events-backoffice.md#customer-profile-events-server-side) 到新的特定于配置文件的数据流和架构，请完成以下步骤。

1. [创建](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) 架构并将类设置为 **体验事件**.

1. [添加](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) 以下特定于用户档案的字段组：

   - 人口统计详细信息
   - 个人联系人详细信息
   - 渠道详细信息
   - 商业详细信息

1. [启用](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#profile) 配置文件的架构。

   为配置文件启用某个架构后，从该架构创建的任何数据集都将参与Real-Time CDP，后者将合并来自不同源的数据，以构建每个客户的完整视图。

1. [创建数据集](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) 基于您创建的架构。

   数据集是用于数据集合的存储和管理结构，通常是包含架构（列）和字段（行）的表。 数据集还包含描述其存储的数据的各个方面的元数据。

1. [创建数据流](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) 并选择包含特定于商务的字段组和相应数据集的XDM架构。

   数据流将收集的数据转发到数据集。 数据根据所选架构在数据集中表示。

通过为客户个人资料数据配置架构、数据集和数据流，您可以 [配置](connect-data.md#data-collection) 您的Commerce实例，以收集该数据并将其发送到Experience Platform。

要为配置文件记录数据创建架构、数据集和数据流，请参阅 [将配置文件记录数据发送到Experience Platform](profile-data.md).
