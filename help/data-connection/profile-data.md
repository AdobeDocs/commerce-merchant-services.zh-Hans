---
title: 更新Commerce数据摄取的配置文件记录架构
description: 了解如何创建架构、数据集和数据流，以收集Commerce配置文件记录数据并将其发送到Experience Platform。
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: 8456f9b81812cf8ace55b7406d8b4fe50332c17a
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---

# 更新Commerce数据摄取的配置文件记录架构

>[!NOTE]
>
>此功能处于测试阶段。 如果您想加入Beta计划，请发送请求至 [dataconnection@adobe.com](mailto:dataconnection@adobe.com).

当购物者在Commerce网站中创建配置文件时，将创建配置文件记录并捕获数据。 您必须先创建特定于配置文件记录的架构和数据集，然后才能将该配置文件数据流式传输到Experience Platform。

1. [创建](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) 架构并将类设置为 **个人资料**.

1. [添加](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) 以下特定于用户档案的字段组：

   - identityMap
   - 人口统计详细信息
   - 个人联系人详细信息
   - 用户帐户详细信息

1. [启用](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#profile) 配置文件的架构。

   为配置文件启用某个架构后，从该架构创建的任何数据集都将参与Real-Time CDP，后者将合并来自不同源的数据，以构建每个客户的完整视图。

1. [创建数据集](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) 基于您创建或更新的架构。

   数据集是用于数据集合的存储和管理结构，通常是包含架构（列）和字段（行）的表。 数据集还包含描述其存储的数据的各个方面的元数据。

通过为客户配置文件记录数据配置架构和数据集，您可以 [配置](connect-data.md#data-collection) 您的Commerce实例，以收集该数据并将其发送到Experience Platform。

要为行为和后台事件数据创建架构、数据集和数据流，请参阅 [更新Commerce数据摄取的时间系列事件架构](update-xdm.md).
