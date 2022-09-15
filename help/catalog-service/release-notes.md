---
title: '[!DNL Catalog Service] 发行说明'
description: 的最新发行信息 [!DNL Catalog Service] Adobe Commerce。
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
source-git-commit: 6609060a4ef09f72d579d97383ac487b105c81d6
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 1%

---

# [!DNL Catalog Service] 发行说明

{{catalog-service-beta}}

以下发行说明介绍了 [!DNL Catalog Service] 包括：

* ![新建](../assets/new.svg)  — 新增功能
* ![修复](../assets/fix.svg)  — 修复和改进功能
* ![错误](../assets/bug.svg)  — 已知问题

## 0.3版本 — Beta+

发行日期：2022-09-12与Adobe Commerce(EE)兼容：2.4.x与Adobe Commerce for Cloud(ECE)兼容：2.4.x稳定性：Beta

![新建](../assets/new.svg)  — 变体支持的图像：产品图像会根据选定的选项返回
![新建](../assets/new.svg)  — 价格支持的作用：仅允许特定客户群组成员查看产品价格
![修复](../assets/fix.svg)  — 提高了服务的稳定性和性能
![新建](../assets/new.svg)  — 从目录中删除产品时，会收到更新

### 已知限制

尚不支持以下功能：

* 分层定价
* 捆绑和分组产品
* 从目录中删除变体后，不会收到任何更新
* B2B可见性覆盖：可搜索产品，或将产品添加到购物车中（针对特定客户群）


## 测试版

发行日期：2022-08-09与Adobe Commerce(EE)兼容：2.4.x与Adobe Commerce for Cloud(ECE)兼容：2.4.x稳定性：Beta

* ![新建](../assets/new.svg) - `products` 和 `refineProduct` 查询会返回以下数据：
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
