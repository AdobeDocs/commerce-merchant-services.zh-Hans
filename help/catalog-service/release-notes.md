---
title: '[!DNL Catalog Service] 发行说明'
description: 的最新发行信息 [!DNL Catalog Service] Adobe Commerce。
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
source-git-commit: 624c959119958f9fdd15d3d9559092c35d079c2c
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# [!DNL Catalog Service] 发行说明

以下发行说明介绍了 [!DNL Catalog Service] 包括：

* ![新建](../assets/new.svg) 新增功能
* ![修复](../assets/fix.svg) 修复和改进功能
* ![错误](../assets/bug.svg) 已知问题

## V1.1版本

发行日期：2022-11-18与Adobe Commerce(EE)兼容：2.4.x与Adobe Commerce for Cloud(ECE)兼容：2.4.x稳定性：正式发布

![新建](../assets/new.svg) 目录服务现在支持Adobe [API Mesh](https://developer.adobe.com/graphql-mesh-gateway/).
![修复](../assets/fix.svg) 我们改进了API可扩展性和整体性能。

### 已知限制

尚不支持以下功能：

* 以固定价格捆绑产品
* 从目录中删除变体后，不会收到任何更新。
* 动态属性有效负载的最大大小为9MB。
* 组产品价格。 可以使用简单的产品价格计算。
* 在图像阵列中，只有第一个图像包含角色。
* 颜色色板
* 通过产品URL加载产品详细信息页面。

使用GraphQL API可以解决以下限制：

* 最低广告价格
* 分层定价
* 可下载的产品和礼品卡
* 类别(`categories` 和 `categoryList`)

## V1.0版本

发行日期：2022-10-04与Adobe Commerce(EE)兼容：2.4.x与Adobe Commerce for Cloud(ECE)兼容：2.4.x稳定性：正式发布

![新建](../assets/new.svg) 现在支持捆绑和分组的产品。
![新建](../assets/new.svg) 添加了B2B可见性覆盖。 现在可搜索产品，并可将其添加到特定客户群的购物车。
![修复](../assets/fix.svg) 服务现在更加稳定，性能也得到提高。

### 已知限制

尚不支持以下功能：

* 分层定价
* 从目录中删除变体时，未收到更新
* 动态属性有效负载的最大大小为&lt;9MB
* 捆绑产品的固定价格
* 分组产品的总价
* 支持虚拟、可下载和礼品卡产品类型
* 最低广告价格(MAP)

## 0.3版本 — Beta+

发行日期：2022-09-12与Adobe Commerce(EE)兼容：2.4.x与Adobe Commerce for Cloud(ECE)兼容：2.4.x稳定性：Beta

![新建](../assets/new.svg) 变体支持的图像：产品图像会根据选定的选项返回
![新建](../assets/new.svg) 价格支持的作用：仅允许特定客户群组成员查看产品价格
![修复](../assets/fix.svg) 提高了服务的稳定性和性能
![新建](../assets/new.svg) 产品从目录中删除后，将收到更新

### 已知限制

尚不支持以下功能：

* 分层定价
* 捆绑和分组产品
* 从目录中删除变体后，不会收到任何更新
* B2B可见性覆盖：可搜索产品，或将产品添加到购物车中（针对特定客户群）

## 测试版

发行日期：2022-08-09与Adobe Commerce(EE)兼容：2.4.x与Adobe Commerce for Cloud(ECE)兼容：2.4.x稳定性：Beta

![新建](../assets/new.svg) 的 `products` 和 `refineProduct` 查询会返回以下数据：

* 预定义（系统）产品属性。
* 动态产品属性，并按角色（产品显示页面/产品列表页面）对其进行筛选。
* 产品选项。
* 产品图像并按角色(PDP/PLP)进行过滤。
* 简单产品的特定价格和可配置产品的价格范围。
* 客户组价格和价格范围。 对于没有客户群组的购物者，它们会返回回退默认价格。
* 使用特定于B2B客户的定价的产品类型。

### 已知限制

* 不支持捆绑和分组产品。
* 不支持层定价。
* 在图像数组中，只有第一个图像包含角色。
* 不会检索变体的图像。
* 从目录中删除产品或变体时，未收到更新。
