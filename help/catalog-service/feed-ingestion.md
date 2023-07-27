---
title: 馈送引入服务
description: 了解Adobe Commerce的信息源摄取服务
source-git-commit: 12b1e89924a2eb89494bcb884fc3bc14e87b2b1c
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---


# 馈送引入服务

>[!NOTE]
>
>信息源引入服务当前为私有测试版。 尚不可用于一般用途。

信息源摄取服务绕过Adobe Commerce实例，将目录数据从第三方企业资源规划(ERP)直接移动到Adobe Commerce服务，从而减少处理产品更改（价格更新、添加新属性）所需的时间。

此服务适用于在核心Adobe Commerce应用程序外部系统中存储和管理其产品目录的客户。

拥有大型、复杂目录或频繁更新的目录的客户担心新数据在Live Store中显示所花的时间可能超过预期。 由于目录服务知道它处理这些更新需要哪些数据，因此无需通过核心Commerce产品发送数据，只需将其转发到目录服务。 消除此中间步骤是发现效率提高的地方。

## 馈送摄取流程

数据存储和数据流可能采用不同的路径，具体取决于Adobe Commerce配置。

* 在标准Adobe Commerce实例中，产品目录存储在核心数据库中。
* 使用Adobe Commerce服务时，目录数据会从核心数据库复制到服务，并从那里进行处理和交付。
* 当在第三方系统(ERP、MDM、PIM)中存储目录数据时，数据流经核心Commerce应用程序，然后流向Commerce服务。
* 借助信息源摄取服务，产品数据可直接从第三方系统传输到商务服务基础架构。

![馈送引入服务](assets/feed-ingestion.png)

通过绕过核心Commerce应用程序并将数据直接移动到Commerce服务，产品更新可更快地反映在商店中。 核心目录数据（例如SKU）将发送到核心Commerce应用程序进行单独处理。

## 加入Beta

馈送摄取服务专为以下目的而设计：

* 具有Headless实施的中型企业客户
* 拥有大型复杂目录的客户
* 客户未使用Adobe Commerce管理员管理目录数据，而是使用ERP或第三方系统管理目录数据

如果您有兴趣加入Beta计划，请通过sagonzal@adobe.com联系团队。
