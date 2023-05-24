---
title: ‘[!DNL Catalog Service] 发行说明
description: 的最新发行信息 [!DNL Catalog Service] 适用于Adobe Commerce的。
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
source-git-commit: f955cfc918c19a3c32126d8c9ef8a59b0e0dce0a
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# [!DNL Catalog Service] 发行说明

以下发行说明介绍了最新版本的 [!DNL Catalog Service].
为当前的主要发行版本提供支持。 提供了旧版本的发行说明以供参考。
更新包括：

![新](../assets/new.svg) 新增功能
![修复](../assets/fix.svg) 修复和改进功能
![错误](../assets/bug.svg) 已知问题

## 当前主要版本

_2023年4月25日_

![新](../assets/new.svg) 目录服务客户现在可以利用新的 [SaaS价格索引器](../price-index/index.md).

### V1.7版本

_2023年4月12日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新](../assets/new.svg) 目录服务现在可以清除已删除的产品变型。
![修复](../assets/fix.svg) 基础架构可扩展性和性能改进。

#### 已知限制

尚不支持以下功能：

* 捆绑固定价格的产品
* 动态属性有效负载的最大大小为9 MB。
* 组产品价格。 可以通过简单的产品价格计算。
* 在图像数组中，只有第一个图像包含角色。

使用API网格和核心GraphQL API可以解决以下限制：

* 最低广告价格
* [分层定价](mesh.md)
* 可下载的产品和礼品卡

### V1.6发布

_2023年3月28日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新](../assets/new.svg) 已将样本添加到 [`products`](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/products/) 查询。
![新](../assets/new.svg) 添加了获取 `entityId` 使用 [API网格](mesh.md).

### V1.5发布

_2023年3月6日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新](../assets/new.svg) 已添加 [`categories`](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/categories/) GraphQL功能。
![修复](../assets/fix.svg) 改进了性能和API可扩展性。

### V1.4版本

_2023年2月7日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新](../assets/new.svg) 已发布目录服务元包以简化安装步骤。
![修复](../assets/fix.svg) API可扩展性和性能改进。

### V1.3发布

_2023年1月17日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新](../assets/new.svg) 简化并改进了载入体验。
![新](../assets/new.svg) 新的客户沙盒端点可用于生产前测试。
![新](../assets/new.svg) 为虚拟产品添加了支持。
![修复](../assets/fix.svg) API可扩展性和性能改进。

### V1.1版本

_2022年11月18日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新](../assets/new.svg) 目录服务现在支持Adobe [API网格](https://developer.adobe.com/graphql-mesh-gateway/).
![修复](../assets/fix.svg) 改进了API可扩展性和整体性能。

### V1.0发布

_2022年10月4日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新](../assets/new.svg) 现在支持捆绑和分组的产品。
![新](../assets/new.svg) 添加了B2B可见性覆盖。 产品现在可搜索，并可添加到特定客户组的购物车中。
![修复](../assets/fix.svg) 服务现在更加稳定，性能也有所提高。

## 以前的版本

+++测试版

### 0.3版本 — Beta+

_2022年9月12日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新](../assets/new.svg) 变体支持的图像：根据选定的选项返回产品图像
![新](../assets/new.svg) 价格支持的角色：仅允许特定客户组的成员查看产品价格
![修复](../assets/fix.svg) 提高了服务的稳定性和性能
![新](../assets/new.svg) 从目录中删除产品时会收到更新

### 测试版

_2022年8月9日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新](../assets/new.svg) 此 `products` 和 `refineProduct` 查询返回以下数据：

* 预定义的（系统）产品属性。
* 动态产品属性，并按角色（产品显示页面/产品列表页面）筛选这些属性。
* 产品选项。
* 产品图像并按角色(PDP/PLP)筛选它们。
* 简单产品的特定价格以及可配置产品的价格范围。
* 客户组价格及价格范围。 它们向没有客户群体的购物者返还后备默认价格。
* 使用B2B客户特定定价的产品类型。

+++
