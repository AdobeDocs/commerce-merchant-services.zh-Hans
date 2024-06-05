---
title: ’[!DNL Catalog Service] 发行说明
description: 的最新发行信息 [!DNL Catalog Service] 用于Adobe Commerce。
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
feature: Services, Catalog Service, Release Notes
source-git-commit: 7293914fab34381deb5bc841d147371f9f3470a5
workflow-type: tm+mt
source-wordcount: '677'
ht-degree: 0%

---

# [!DNL Catalog Service] 发行说明

以下发行说明介绍了 [!DNL Catalog Service].
为当前的主要发行版本提供支持。 提供了旧版本的发行说明以供参考。
更新包括：

![新建](../assets/new.svg) 新增功能
![修复](../assets/fix.svg) 修复和改进功能
![错误](../assets/bug.svg) 已知问题

## 当前主要版本

### V1.19发布

_2024年5月23日_

![修复](../assets/fix.svg) <!--DATA-5033-->此 `InStock` 现在，选项值的标记会考虑限定范围的值 `enabled` 产品变体的状态。

![修复](../assets/fix.svg) <!--DATA-5888-->添加对需要大数字（最多16位）和高小数精度（最多4位小数）的产品价格的支持。 要将价格配置更新应用到现有目录，请从以下位置重新同步目录数据： [数据管理功能板](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard)，或使用 [Adobe Commerce命令行界面](../landing/catalog-sync.md#command-line-interface).

## 先前版本

+++ 先前版本

### V1.18发布

_2024年4月11日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/new.svg) 添加了对PHP 8.3的支持。

![新建](../assets/new.svg) 此 [`products`](https://developer.adobe.com/commerce/services/graphql/catalog-service/products/) 和 [`refineProduct`](https://developer.adobe.com/commerce/services/graphql/catalog-service/refine-product/) 现在，查询会返回简单和复杂产品的可自定义选项数据。<!--DATA-5538-->

### V1.17发布

_2024年2月22日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/new.svg) 此 [[!DNL Data Management Dashboard]](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html) 现已推出。 这个改版后的功能板提供了有关以下内容的数据流的分析： [!DNL Product Recommendations]， [!DNL Live Search]、和 [!DNL Catalog Service]. 对此功能的支持已在的v3.1.0中引入 `catalog-service` 暗喻。

### V1.16发布

_2024年2月13日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/new.svg) 目录服务API现在支持产品视频。
![修复](../assets/fix.svg) 现在支持固定价格的捆绑产品。
![修复](../assets/fix.svg) 缺货期权现在显示在PDP构件中。

#### 已知限制

尚不支持以下功能：

* 动态属性有效负载的最大大小为9 MB。
* 组产品价格。 此值可使用简单的产品价格计算。
* 在图像数组中，只有第一个图像包含角色。

使用API Mesh和核心GraphQL API可以解决以下限制：

* 最低广告价格
* [分层定价](mesh.md)

### V1.13发布

_2023年10月12日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/new.svg) 目录服务支持 `inStock` 产品变型的标记。
![新建](../assets/new.svg) 此 `urlKey` 和 `externalId` 字段已添加到GraphQL架构中。
![新建](../assets/new.svg) 现在支持可下载产品和礼品卡。

### V1.12发布

_2023年9月19日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/new.svg) 目录服务现在使用 [SaaS价格索引](../price-index/price-indexing.md).
![修复](../assets/fix.svg) 此版本包含服务端的错误修复和改进。

### V1.11发布

_2023年7月18日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/new.svg) 目录服务现在支持 [`recommendations`](https://developer.adobe.com/commerce/services/graphql/recommendations/recommendations/) GraphQL查询产品Recommendations。

### V1.10发布

_2023年6月27日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/new.svg) 目录服务API现在支持 `related products`.

### V1.7发布

_2023年4月12日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/new.svg) 目录服务现在可以清理已删除的产品变型。
![修复](../assets/fix.svg) 基础架构可扩展性和性能改进。

### V1.6发布

_2023年3月28日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/new.svg) 已将样本添加到 [`products`](https://developer.adobe.com/commerce/services/graphql/catalog-service/products/) 查询。
![新建](../assets/new.svg) 添加了获取 `entityId` 使用 [API网格](mesh.md).

### V1.5发布

_2023年3月6日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/new.svg) 已添加 [`categories`](https://developer.adobe.com/commerce/services/graphql/schema/catalog-service/categories/) GraphQL功能。
![修复](../assets/fix.svg) 改进了性能和API可扩展性。

### V1.4发布

_2023年2月7日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/new.svg) 已发布目录服务元包以简化安装步骤。
![修复](../assets/fix.svg) API可扩展性和性能改进。

### V1.3发布

_2023年1月17日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/new.svg) 简化并改进了载入体验。
![新建](../assets/new.svg) 新的客户沙盒端点可用于预生产测试。
![新建](../assets/new.svg) 添加了对虚拟产品的支持。
![修复](../assets/fix.svg) API可扩展性和性能改进。

### V1.1发布

_2022年11月18日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/new.svg) 目录服务现在支持Adobe [API网格](https://developer.adobe.com/graphql-mesh-gateway/).
![修复](../assets/fix.svg) 改进了API可扩展性和整体性能。

### V1.0发布

_2022年10月4_

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/new.svg) 现在支持捆绑产品和分组产品。
![新建](../assets/new.svg) 添加了B2B可见性覆盖。 产品现在可供搜索，并可添加到特定客户组的购物车中。
![修复](../assets/fix.svg) 服务现在更加稳定并提高了性能。

### 0.3版本 — Beta+

_2022年9月12日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/new.svg) 变体支持的图像：根据所选选项返回产品图像
![新建](../assets/new.svg) 价格支持角色：仅允许特定客户组的成员查看产品价格
![修复](../assets/fix.svg) 提高了服务的稳定性和性能
![新建](../assets/new.svg) 从目录中删除产品时会收到更新

### 测试版

_2022年8月9日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/new.svg) 此 `products` 和 `refineProduct` 查询返回以下数据：

* 预定义的（系统）产品属性。
* 动态产品属性，并按角色（产品显示页面/产品列表页面）筛选这些属性。
* 产品选项。
* 产品图像并按角色(PDP/PLP)过滤它们。
* 简单产品的具体价格以及可配置产品的价格范围。
* 客户组价格及价格范围。 它们向没有客户群组的购物者返还后备默认价格。
* 使用B2B客户特定定价的产品类型。
