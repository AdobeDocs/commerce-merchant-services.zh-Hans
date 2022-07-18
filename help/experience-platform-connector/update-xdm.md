---
title: 将字段组添加到XDM架构
description: 了解如何将特定于Adobe Commerce的字段组添加到XDM模式。
source-git-commit: 4d6a4cec81dbb1e71718066be2ba13a4d292aea3
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# 将字段组添加到XDM架构

其中一个 [先决条件](overview.md#prereqs) 使用Experience Platform连接器是访问数据流工作区和 [创建数据流](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en) 是Adobe Commerce的特有。 在创建该数据流时，还必须选择一个XDM架构来表示您计划摄取的数据。 本主题为您提供了XDM架构必须包含的字段组，以成功收集Adobe Commerce店面提供的数据 [事件](events.md).

1. 如果您还没有XDM架构， [创建](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html?lang=en#create) 一个。 否则， [编辑](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html?lang=en#edit) 您在Adobe Experience Platform UI中的现有XDM架构。
1. [添加](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html?lang=en#add-field-groups) 以下特定于商务的字段组：

   - 商务
   - 网站搜索
   - 访问网页
   - 用户登录过程
   - 引用键
   - 个人联系详细信息
   - 商务详细信息
   - Adobe Analytics Experience Event Commerce(如果要将数据发送到Adobe Analytics)
   - 人员标识符

   您的XDM架构现在包含特定于商务的字段组，以便从商务店面收集的数据 [事件](events.md) 表示在XDM中。
1. 您现在应该 [创建数据流](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en) 并选择包含特定于商务的字段组的XDM架构。
