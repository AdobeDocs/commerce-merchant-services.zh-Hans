---
title: '[!DNL Catalog Service]'
description: '''[!DNL Catalog Service] for Adobe Commerce提供了一种方法，可比本机Adobe Commerce GraphQL查询更快地检索产品显示页面和产品列表页面的内容。'
exl-id: 266faca4-6a65-4590-99a9-65b1705cac87
source-git-commit: bb557e130a7dbef96c625d65cbe191a4ccbe26d0
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 0%

---

# [!DNL Catalog Service] 对于Adobe Commerce

的 [!DNL Catalog Service] for Adobe Commerce扩展提供了富视图模型（只读）目录数据，以快速、完全渲染与产品相关的店面体验，包括：

* 产品详细信息页面
* 产品列表和类别页面
* 搜索结果页面
* 产品轮播
* 产品比较页面
* 呈现产品数据的任何其他页面，例如购物车、订购和愿望列表页面

的 [!DNL Catalog Service] 使用 [GraphQL](https://graphql.org/) 请求和接收产品数据。 GraphQL是一种查询语言，前端客户端使用它与在后端(如Adobe Commerce)上定义的应用程序编程接口(API)通信。 GraphQL是一种常用的通信方法，因为它重量轻，允许系统集成商指定每个响应的内容和顺序。

Adobe Commerce有两个GraphQL系统。 核心GraphQL系统提供了各种查询（读取操作）和突变（写入操作），允许购物者与多种类型的页面进行交互，包括产品、客户帐户、购物车、结账等。 但是，返回产品信息的查询不会针对速度进行优化。 服务GraphQL系统只能对产品和相关信息执行查询。 这些查询比类似的核心查询更具性能。

## 架构

下图显示了两个GraphQL系统：

![目录架构图](assets/catalog-service-architecture.png)

在核心GraphQL系统中，PWA向商务应用程序发送请求，该应用程序接收每个请求，处理每个请求，可能通过多个子系统发送请求，然后返回对店面的响应。 此往返可能会导致页面加载时间变慢，从而可能降低转化率。

[!DNL Catalog Service] 向单独的GraphQL网关发送查询。 该服务将访问一个单独的数据库，其中包含产品详细信息和相关信息，如产品属性、变体、价格和类别。 该服务通过索引使数据库与Adobe Commerce保持同步。
由于该服务绕过了与应用程序的直接通信，因此能够减少请求的延迟和响应周期。

>[!NOTE]
>
>该网关可供将来与产品Recommendations集成。 在此版本中，您可以访问 [!DNL Catalog Service] 和 [!DNL Live Search] 如果您有两个产品的有效许可证密钥，则从同一端点联合查询。

核心和服务GraphQL系统不直接相互通信。 您可以从不同的URL访问每个系统，而调用需要不同的标头信息。 两个GraphQL系统设计为可一起使用。 的 [!DNL Catalog Service] GraphQL系统增强了核心系统，以加快产品店面体验的速度。

您可以选择实施 [适用于Adobe Developer App Builder的API网格](https://developer.adobe.com/graphql-mesh-gateway/) 要将两个Adobe Commerce GraphQL系统与使用Adobe Developer的专用和第三方API及其他软件接口相集成。 网格可以配置为确保路由到每个端点的调用在标头中包含正确的授权信息。

## 实施

安装过程需要配置 [Commerce Services Connector](../landing/saas.md). 完成后，下一步是由系统集成商更新店面代码以合并 [!DNL Catalog Service] 查询。 全部 [!DNL Catalog Service] 查询将路由到GraphQL网关。 URL在载入过程中提供。
