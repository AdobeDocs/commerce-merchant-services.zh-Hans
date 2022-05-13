---
title: Live Search指南概述
description: Adobe Commerce的实时搜索功能可提供闪电般的快速、超相关且直观的搜索体验。
exl-id: 11e2ed97-ce80-4826-b914-71688dd29e4b
source-git-commit: 2676c363182d0b7cb02d15d1093066b1ad4e7b87
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 0%

---

# Live Search指南概述

[!DNL Live Search] 从Adobe Commerce免费为Adobe Commerce提供闪电般快速、超相关且直观的搜索体验。 [!DNL Live Search] 由Powered提供 [Adobe Sensei](https://www.adobe.com/sensei.html) 使用人工智能和机器学习算法对聚合的访客数据进行深入分析。 此数据与Adobe Commerce目录结合使用后，可提供极具吸引力、相关性和个性化的购物体验。 注重速度、相关性和易用性， [!DNL Live Search] 对购物者和商人而言，这是改变游戏规则的因素。

Live Search有三个管理员区域：

* 店面：使用CSS样式自定义 [!DNL storefront popover].
* 管理员：使用此区域可访问配置和设置。
* 命令行界面：使用此工具执行安装和后端配置任务。

## 其他文档

| 指南 | 描述 |
|--- |--- |
| Adobe Commerce 2.4用户指南 | 面向Adobe Commerce和Magento Open Source的以商户为中心的文档 |
| Adobe Commerce 2.4开发人员指南 | 以开发人员为中心的文档，用于构建和自定义Adobe Commerce或Magento Open Source |

## 支持

如果您需要信息或遇到本指南未涵盖的问题，请使用以下资源：

[帮助中心](https://support.magento.com/hc/en-us)  — 请参阅实时搜索相关疑难解答文章。
[支持票证](https://support.magento.com/hc/en-us/articles/360000913794#submit-ticket)  — 提交票证以接收其他帮助。

在提交支持票证之前，请从命令行中运行以下命令，以检查当前安装的Live Search版本：

```bash
composer show magento/module-live-search | grep version
```
