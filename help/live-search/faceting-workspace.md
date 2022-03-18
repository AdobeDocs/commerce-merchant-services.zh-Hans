---
title: 分面工作区
description: 通过实时搜索分面工作区了解您的方法。
exl-id: b47b5c19-59bb-41e4-9599-3b90cbc44b70
source-git-commit: 19f0c987ab6b43b6fac1cad266b5fd47a7168e73
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# 分面工作区

的 [!DNL Live Search] 工作区会列出当前可用的所有facet，并允许您访问设置和管理facet所需的工具。 已固定的彩块化首先会在现有彩块化列表中显示，然后是动态彩块化。 可以过滤该列表以显示所有彩块化，或仅显示已固定或动态彩块化。

![分面工作区](assets/faceting-workspace.png)

## 设置范围

如果Adobe Commerce安装包含多个商店视图，请设置 **范围** 到 [商店视图](https://docs.magento.com/user-guide/configuration/scope.html) 应用facet设置的位置。

## 过滤列表

1. 单击 **过滤依据** 控制。
1. 选择以下选项之一：

   * 所有过滤器
   * 已固定
   * 动态

   ![分面工作区](assets/facets-filter-by.png)

## 添加facet

1. 单击 **添加Facet**.
1. 请参阅 [添加Facet](facets-add.md) 以了解详细说明。

## 列描述

| 列 | 描述 |
|--- |--- |
| （第一列） | 列出通过 [标签](facets-type.md) 对购物者可见。 |
| 选择类型 | 的 [选择方法](facets-type.md) 分配给相应产品属性的ID。 的 `single select` 类型用于所有 [!DNL Commerce] 店面。 对于无头实施， `multi-select` 类型可以分配逻辑运算符(`or` 或 `and`)来确定返回的产品集。 |
| 排序类型 | 的 [排序顺序](facets-type.md) facet值。 彩块化按字母顺序排序 [!DNL Commerce] 店面。 对于 [无头] 实施中，facet可以按字母顺序或按计数进行排序。 选项：按字母顺序，计数（仅限无头） |
| 最大值 | 店面中可用作过滤器的facet值的数量，最多为10个。 |

## 控件

| 控制 | 描述 |
|--- |--- |
| 添加Facet | 打开 [facet editor](facets-add.md). |
| 过滤依据 | 确定 [facet类型](facets-type.md) 列表中显示的。 选项：全部、固定、动态 |
