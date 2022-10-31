---
title: '[!DNL Catalog Service]'
description: '''[!DNL Catalog Service] for Adobe Commerce提供了一种方法，可比本机Adobe Commerce GraphQL查询更快地检索产品显示页面和产品列表页面的内容。'
exl-id: 266faca4-6a65-4590-99a9-65b1705cac87
source-git-commit: 55036065c686553bc530bb7a4fe46fcec1bd9ee8
workflow-type: tm+mt
source-wordcount: '905'
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

通过将这些查询发送到网关(https://catalog-service.adobe.io/graphql)，可运行这些查询。

## 架构

下图显示了两个GraphQL系统：

![目录架构图](assets/catalog-service-architecture.png)

在核心GraphQL系统中，PWA向商务应用程序发送请求，该应用程序接收每个请求，处理每个请求，可能通过多个子系统发送请求，然后返回对店面的响应。 此往返可能会导致页面加载时间变慢，从而可能降低转化率。

[!DNL Catalog Service] 是联合GraphQL网关服务。 该服务将访问一个单独的数据库，其中包含产品详细信息和相关信息，如产品属性、变体、价格和类别。 该服务通过索引使数据库与Adobe Commerce保持同步。
由于该服务绕过了与应用程序的直接通信，因此能够减少请求的延迟和响应周期。

>[!NOTE]
>
>该网关可供将来与产品Recommendations集成。 在此版本中，您可以访问 [!DNL Catalog Service Federated GraphQL] 和 [!DNL Live Search] 如果您有两个产品的有效许可证密钥，则从同一端点联合查询。

核心和服务GraphQL系统不直接相互通信。 您可以从不同的URL访问每个系统，而调用需要不同的标头信息。 两个GraphQL系统设计为可一起使用。 的 [!DNL Catalog Service] GraphQL系统增强了核心系统，以加快产品店面体验的速度。

您可以选择实施 [适用于Adobe Developer App Builder的API网格](https://developer.adobe.com/graphql-mesh-gateway/) 要将两个Adobe Commerce GraphQL系统与使用Adobe Developer的专用和第三方API及其他软件接口相集成。 网格可以配置为确保路由到每个端点的调用在标头中包含正确的授权信息。

## 架构细节

以下各节介绍了两个GraphQL系统之间的一些差异。

### 架构管理

由于目录服务是作为服务运行的，因此集成商不必担心底层版本的商务。 所有版本的查询语法都相同。 此外，所有商户的架构都是一致的。 此一致性使建立最佳实践变得更加容易，并显着增加了店面小组件的重复使用。

### 简化产品类型

该架构将产品类型的多样性降低为两个用例：

* 简单产品是指使用单一价格和数量定义的产品。 目录服务将简单、虚拟、可下载和礼品卡产品类型映射到 `simpleProductViews`.

* 复杂产品由多个简单产品组成。 组件简单的产品可以有不同的价格。 还可以定义复杂产品，以便购物者可以指定组件简单产品的数量。 目录服务将可配置、捆绑和分组的产品类型映射到 `complexProductViews`.

复杂的产品选项会因其行为（而非类型）而统一和区分。 每个选项值代表一个简单的产品。 此选项值有权访问简单的产品属性，包括价格。 当购物者为复杂产品选择所有选项时，选定选项的组合将指向特定的简单产品。 在购物者为所有可用选项选择一个值之前，简单产品仍然不明确。

### 价格

简单产品表示具有价格的基本销售单位。 目录服务计算折扣前的常规价格以及折扣后的最终价格。 定价计算可以包括固定产品税。 它们会排除个性化促销活动。

复杂产品没有固定价格。 Catalog Service而是会返回链接示例的价格。 例如，商家最初可以为可配置产品的所有变体分配相同的价格。 如果某些尺寸或颜色不受欢迎，商家可以降低这些变体的价格。 因此，复杂（可配置）产品的价格首先显示一个价格范围，反映了标准变体和不受欢迎的变体的价格。 购物者为所有可用选项选择了值后，店面会显示单个价格。

## 实施

安装过程需要配置 [Commerce Services Connector](../landing/saas.md). 完成后，下一步是由系统集成商更新店面代码以合并 [!DNL Catalog Service] 查询。 全部 [!DNL Catalog Service] 查询将路由到GraphQL网关。 URL在载入过程中提供。
