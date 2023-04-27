---
title: '[!DNL Catalog Service] 发行说明'
description: 的最新发行信息 [!DNL Catalog Service] Adobe Commerce。
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
source-git-commit: f955cfc918c19a3c32126d8c9ef8a59b0e0dce0a
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# [!DNL Catalog Service] 发行说明

以下发行说明介绍了 [!DNL Catalog Service].
对当前主要发布的版本提供支持。 提供了早期版本的发行说明供参考。
更新包括：

![新建](../assets/new.svg) 新增功能
![修复](../assets/fix.svg) 修复和改进功能
![错误](../assets/bug.svg) 已知问题

## 当前主要版本

_2023年4月25日_

![新建](../assets/new.svg) 目录服务客户现在可以利用新的 [SaaS价格索引器](../price-index/index.md).

### V1.7版本

_2023年4月12日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新建](../assets/new.svg) 目录服务现在可以清理已删除的产品变体。
![修复](../assets/fix.svg) 基础架构的可扩展性和性能改进。

#### 已知限制

尚不支持以下功能：

* 以固定价格捆绑产品
* 动态属性有效负载的最大大小为9 MB。
* 组产品价格。 可以使用简单的产品价格计算。
* 在图像阵列中，只有第一个图像包含角色。

使用API Mesh和核心GraphQL API可以解决以下限制：

* 最低广告价格
* [分层定价](mesh.md)
* 可下载的产品和礼品卡

### V1.6版本

_2023年3月28日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新建](../assets/new.svg) 向 [`products`](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/products/) 查询。
![新建](../assets/new.svg) 添加了 `entityId` 使用 [API Mesh](mesh.md).

### V1.5版本

_2023年3月6日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新建](../assets/new.svg) 添加了 [`categories`](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/categories/) GraphQL功能。
![修复](../assets/fix.svg) 提高了性能和API可扩展性。

### V1.4版本

_2023年2月7日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新建](../assets/new.svg) 发布了目录服务元包，以简化安装步骤。
![修复](../assets/fix.svg) API可扩展性和性能改进。

### V1.3版本

_2023年1月17日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新建](../assets/new.svg) 简化并改进了入门体验。
![新建](../assets/new.svg) 新的客户沙盒端点可用于预生产测试。
![新建](../assets/new.svg) 添加了对虚拟产品的支持。
![修复](../assets/fix.svg) API可扩展性和性能改进。

### V1.1版本

_2022年11月18日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新建](../assets/new.svg) 目录服务现在支持Adobe [API Mesh](https://developer.adobe.com/graphql-mesh-gateway/).
![修复](../assets/fix.svg) 提高了API可扩展性和整体性能。

### V1.0版本

_2022年10月4日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新建](../assets/new.svg) 现在支持捆绑和分组的产品。
![新建](../assets/new.svg) 添加了B2B可见性覆盖。 现在可搜索产品，并可将其添加到特定客户群的购物车。
![修复](../assets/fix.svg) 服务现在更加稳定，性能也得到提高。

## 早期版本

+++测试版

### 0.3版本 — Beta+

_2022年9月12日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新建](../assets/new.svg) 变体支持的图像：产品图像会根据选定的选项返回
![新建](../assets/new.svg) 价格支持的作用：仅允许特定客户群组成员查看产品价格
![修复](../assets/fix.svg) 提高了服务的稳定性和性能
![新建](../assets/new.svg) 产品从目录中删除后，将收到更新

### 测试版

_2022年8月9日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新建](../assets/new.svg) 的 `products` 和 `refineProduct` 查询会返回以下数据：

* 预定义（系统）产品属性。
* 动态产品属性，并按角色（产品显示页面/产品列表页面）对其进行筛选。
* 产品选项。
* 产品图像并按角色(PDP/PLP)进行过滤。
* 简单产品的特定价格和可配置产品的价格范围。
* 客户组价格和价格范围。 对于没有客户群组的购物者，它们会返回回退默认价格。
* 使用特定于B2B客户的定价的产品类型。

+++
