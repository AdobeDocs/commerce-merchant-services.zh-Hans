---
title: "[!DNL Live Search] 指南概述"
description: '"[!DNL Live Search] Adobe Commerce提供了闪电般快速、超级相关且直观的搜索体验。”'
exl-id: 11e2ed97-ce80-4826-b914-71688dd29e4b
recommendations: noCatalog
source-git-commit: 888b81683a4e139a35b771d9c573f1f5f0c3b902
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 2%

---

# [!DNL Live Search] 指南概述

[!DNL Live Search] for Adobe Commerce提供了快速、相关且直观的搜索体验，而无需支付额外费用。 [!DNL Live Search] 提供者 [Adobe Sensei](https://www.adobe.com/sensei.html) 使用人工智能和机器学习算法对汇总的访客数据执行深度分析。 此数据与Adobe Commerce目录结合使用后，可提供相关且个性化的购物体验。

[!DNL Live Search] 管理员有三个区域：

* 店面：使用CSS样式自定义 [!DNL storefront popover].
* 管理员：使用此区域可访问配置和设置。
* 命令行界面：使用此工具执行安装和后端配置任务。

## 其他文档

| 指南 | 描述 |
|------ | ----------- |
| [Adobe Commerce 2.4用户指南](https://experienceleague.adobe.com/docs/commerce.html) | 适用于Adobe Commerce和Magento Open Source的以商家为中心的文档 |
| [Adobe Commerce 2.4开发人员指南](https://developer.adobe.com/commerce/docs) | 用于构建和自定义Adobe Commerce或Magento Open Source的以开发人员为中心的文档 |

## 支持

如果您需要本指南中未涉及的信息或问题，请使用以下资源：

[知识库](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html)  — 请参阅 [!DNL Live Search] — 相关的故障排除文章。
[支持票证](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket)  — 提交票证以接收其他帮助。

在提交支持票证之前，从命令行运行以下命令以检查 [!DNL Live Search] 当前已安装的：

```bash
composer show magento/module-live-search | grep version
```
