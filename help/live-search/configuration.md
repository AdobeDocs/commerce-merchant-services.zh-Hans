---
title: 'Commerce配置设置'
description: 介绍Commerce配置设置，这些设置可以 [!DNL Live Search] 可以阅读。
exl-id: a4e9e2dd-e912-4ced-a44a-091ac5334e50
features: Services, Search, Configuration
source-git-commit: 4978bdb5549f5df911863a23fdfbfc9ab9ad05df
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---

# Commerce配置设置

有一些Commerce配置设置可以 [!DNL Live Search] 支持。 本文列出了这些配置值。

## 支持的配置值

| Commerce配置设置 | 受Popover支持 | 适配器支持 |
|---|---|---|
| 存储>配置>目录>目录>目录搜索>允许每个页面长度的所有产品 | 是的。 最多500个产品 | 是的。 最多500个产品 |
| 存储>配置>目录>目录>目录搜索>最小查询长度 | 是 | 是 |
| 存储>配置>目录>目录>目录搜索>每页产品在网格中的允许值 | 是 | 是 |
| 存储>配置>目录>目录>目录搜索>每页产品在网格上的默认值 | 是的。 最多500个产品 | 是的。 最多500个产品 |
| 商店>配置>目录>库存>显示缺货产品 | 是，带v2.0.4+ | 是，带v2.0.4+ |
| 存储>配置>货币>默认显示货币 | 是，带3.1.0+ | 是，带3.1.0+ |
| 存储>配置>常规>货币设置>货币选项>基本货币 | 是 | 是 |

现在，小组件产品列表页面和弹出框中的价格将使用配置的汇率转换为默认显示货币。

## 搜索词

[!DNL Live Search] 支持 [搜索词重定向](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html) 在Adobe Commerce处理路由的实施中： Luma和其他基于php的主题。

## 不支持的配置值

[!DNL Live Search] 无法读取所有配置值。 此表列出了开发人员可能更感兴趣的值。

| Commerce配置设置 | 注释 |
|---|---|
| 存储>配置>目录>店面>列表模式 | 正确呈现，但是对于某些页面交互，不会发送事件 |
| 存储>配置>目录>目录>目录搜索>最大查询长度 | 未实现；搜索服务最多接受255个字符 |
| 配置>销售>税>价格显示设置>在目录中显示产品价格 |  |
| 商店>配置>目录>店面>产品列表排序依据 | 不适用于 [!DNL Live Search] [产品列表页面小组件](plp-styling.md) |
