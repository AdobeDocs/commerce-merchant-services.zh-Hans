---
title: 数据引入服务
description: 了解Adobe Commerce的数据引入服务
exl-id: bb5aec74-faca-42ec-9fdb-3261677d451e
source-git-commit: a2f933151481cbdd39d66a0dfbd36e6c339ede62
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# 数据引入服务

数据摄取服务允许拥有大型和/或复杂目录的客户直接将数据发送到Adobe Commerce服务。

数据摄取服务绕过Adobe Commerce实例，将目录数据从第三方企业资源规划(ERP)直接移动到Adobe Commerce服务，从而减少处理产品更改（价格更新、添加新属性）所需的时间。

此服务适用于在核心Adobe Commerce应用程序外部系统中存储和管理其产品目录的客户。 它作为API提供，因此客户可以将其集成到其现有系统中，从而在其部署方式上提供了更大的灵活性。

拥有大型、复杂目录或频繁更新的目录的客户担心新数据在Live Store中显示所花的时间可能超过预期。 由于目录服务知道它处理这些更新需要哪些数据，因此无需通过核心Commerce产品发送数据，只需将其转发到目录服务。 消除此中间步骤是发现效率提高的地方。

## 数据引入流程

数据存储和数据流可能采用不同的路径，具体取决于Adobe Commerce配置。

* 在标准Adobe Commerce实例中，产品目录存储在核心数据库中。
* 使用Adobe Commerce服务时，目录数据会从核心数据库复制到服务，并从那里进行处理和交付。
* 当在第三方系统(ERP、MDM、PIM)中存储目录数据时，数据流经核心Commerce应用程序，然后流向Commerce服务。
* 使用数据摄取服务，产品数据直接从第三方系统传输到商务服务基础架构。

![数据引入服务](assets/data-ingestion.png)

通过绕过核心Commerce应用程序并将数据直接移动到Commerce服务，产品更新可更快地反映在商店中。 核心目录数据（例如SKU）将发送到核心Commerce应用程序进行单独处理。

## API

此 [数据摄取服务API文档](https://developer.adobe.com/commerce/services/data-ingestion) 提供了有关如何实施服务的详细信息。
