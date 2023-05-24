---
title: '[!DNL Catalog Service]'
description: ‘[!DNL Catalog Service] for Adobe Commerce提供了一种方法，可以比本机Adobe Commerce GraphQL查询更快地检索产品显示页面和产品列表页面的内容。
exl-id: 266faca4-6a65-4590-99a9-65b1705cac87
source-git-commit: 86e6fdb653278f3e70640155d697897a2ea1b674
workflow-type: tm+mt
source-wordcount: '930'
ht-degree: 0%

---

# [!DNL Catalog Service] 适用于Adobe Commerce的

此 [!DNL Catalog Service] for Adobe Commerce扩展提供了丰富视图模型（只读）目录数据，以快速并完全渲染与产品相关的店面体验，包括：

* 产品详细信息页面
* 产品列表和类别页面
* 搜索结果页面
* 产品轮播
* 产品比较页面
* 渲染产品数据的任何其他页面，例如购物车、订单和愿望清单页面

此 [!DNL Catalog Service] 用途 [GraphQL](https://graphql.org/) 以请求和接收产品数据。 GraphQL是一种查询语言，前端客户端使用该语言与在后端(如Adobe Commerce)上定义的应用程序编程接口(API)进行通信。 GraphQL是一种流行的通信方法，因为它很轻便，允许系统集成商指定每个响应的内容和顺序。

Adobe Commerce有两个GraphQL系统。 核心GraphQL系统提供了广泛的查询（读取操作）和突变（写入操作），允许购物者与多种类型的页面交互，包括产品、客户帐户、购物车、结帐等。 但是，返回产品信息的查询没有针对速度进行优化。 GraphQL系统提供的服务只能对产品及相关信息执行查询。 这些查询的性能优于相似的核心查询。

目录服务客户可以使用新的 [SaaS价格索引器](../price-index/index.md)，可以加快价格变更更新和同步时间。

## 架构

下图显示了两个GraphQL系统：

![目录架构图](assets/catalog-service-architecture.png)

在核心GraphQL系统中，PWA向Commerce应用程序发送请求，该应用程序接收每个请求，对其进行处理，可能通过多个子系统发送请求，然后向店面返回响应。 此往返可能会导致页面加载时间变慢，从而可能导致转化率降低。

[!DNL Catalog Service] 是Storefront Services网关。 该服务可访问单独的数据库，该数据库包含产品详细信息和相关信息，例如产品属性、变型、价格和类别。 此服务通过索引使数据库与Adobe Commerce保持同步。
由于服务绕过了与应用程序的直接通信，因此它可以减少请求的延迟和响应周期。

>[!NOTE]
>
>该网关用于将来与Product Recommendations集成。 在此版本中，您可以访问 [!DNL Catalog Service GraphQL] 和 [!DNL Live Search] 来自同一端点的查询（如果您拥有两个产品的有效许可证密钥）。

GraphQL系统的核心和服务不会直接相互通信。 您可以从不同的URL访问每个系统，并且调用需要不同的标头信息。 这两个GraphQL系统旨在共同使用。 此 [!DNL Catalog Service] GraphQL系统增强了核心系统，使产品店面体验更快。

您可以选择实施 [Adobe Developer App Builder的API网格](https://developer.adobe.com/graphql-mesh-gateway/) 使用Adobe Developer将两个Adobe Commerce GraphQL系统与专用和第三方API以及其他软件界面集成。 可以配置网格以确保路由到每个端点的调用在标头中包含正确的授权信息。

## 体系结构详细信息

以下部分介绍了这两种GraphQL系统之间的一些差异。

### 架构管理

由于目录服务作为服务运行，因此集成商无需担心Commerce的基础版本。 所有版本的查询语法相同。 此外，该架构对所有商家都是一致的。 这种一致性使建立最佳实践变得更加容易，并显着提高了店面构件的重复使用率。

### 产品类型的简化

该架构将产品类型的多样性减少为两个用例：

* 简单产品是指使用单一价格和数量定义的产品。 目录服务将简单、虚拟、可下载和礼品卡产品类型映射到 `simpleProductViews`.

* 复杂的产品由多个简单的产品组成。 组件简单产品可以有不同的价格。 还可以定义复杂产品，以便购物者可以指定简单产品的组成数量。 目录服务将可配置、捆绑包和分组的产品类型映射到 `complexProductViews`.

复杂的产品选项通过其行为而非类型进行统一和区分。 每个选项值表示一个简单的产品。 此选项值可以访问简单产品属性，包括价格。 当购物者选择复杂产品的所有选项时，所选选项的组合指向特定的简单产品。 在购物者为所有可用选项选择一个值之前，简单产品将保持模糊状态。

### 价格

简单产品表示具有价格的基本销售单位。 目录服务计算折扣前的常规价格以及折扣后的最终价格。 定价计算可以包括固定产品税。 它们不包括个性化促销。

复杂的产品没有确定的价格。 相反，目录服务会返回所链接元素的价格。 例如，商家最初可以为可配置产品的所有变体分配相同的价格。 如果某些尺寸或颜色不受欢迎，商家可以降低这些系列的价格。 因此，复杂（可配置）产品的价格首先显示一个价格范围，同时反映标准和不受欢迎的变体的价格。 购物者为所有可用选项选择了一个值后，店面会显示一个价格。

>[!NOTE]
>
> 商业客户，具有 [!DNL Catalog Service] 可以利用，网站上的更快价格更改更新和同步时间与 [SaaS价格索引器](../price-index/index.md).

## 实现

安装过程需要配置 [商务服务连接器](../landing/saas.md). 完成此操作后，系统集成商下一步将更新店面代码以纳入 [!DNL Catalog Service] 查询。 全部 [!DNL Catalog Service] 查询将路由到GraphQL网关。 在新用户引导过程中提供该URL。
