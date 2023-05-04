---
title: 产品Recommendations管理员开发
description: 产品Recommendations架构和开发功能概述。
exl-id: caef5e0c-dd69-4846-8f85-b1c5e1c6a28f
source-git-commit: e74bc4aeaa154e751f8d986e0426dd19d55d335e
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# 产品Recommendations管理员开发

产品Recommendations是一款功能强大的营销工具，可用于提高转化率、增加收入和刺激购物者参与。 产品Recommendations以单位形式显示在店面上，例如“查看过此产品的客户也查看过”、“购买过此产品的客户也购买过”、“为您推荐”等。 Adobe Commerce产品Recommendations由 [Adobe Sensei](https://www.adobe.com/sensei.html)，它使用人工智能和机器学习算法对聚合购物者数据进行深入分析。 此数据与您的商务目录结合使用后，可为购物者提供极具吸引力、相关且个性化的体验。

>[!NOTE]
>
>如果您的店面是使用PWA Studio实施的，请参阅 [PWA文档](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). 如果您使用自定义前端技术（如React或Vue JS），请参阅用户指南，以了解如何在 [无头](headless.md) 环境。 无标题实例必须实施事件才能为产品推荐工作区提供动力。

## 架构概述

在高级别上，商务产品Recommendations部署为SaaS。 商务端包括店面（其中包含事件收集器和推荐布局模板）和后端（包括数据服务、SaaS导出模块和管理员UI）。 Adobe Sensei智能服务在SaaS端得到利用。

![产品推荐架构图](assets/arch-diag-sensei.svg)

安装和配置推荐模块后，您的店面将开始收集行为数据。 Adobe Sensei会将此行为数据与您的目录数据一起处理，并计算由“推荐”服务利用的产品关联。 此时，商家可以直接从管理员UI创建、管理和部署产品推荐单元并将其部署到其店面。

## 数据类型

产品Recommendations需要以下数据：

- **行为**  — 来自您网站上购物者参与度的数据，例如产品查看次数、添加到购物车的项目以及购买次数。 Commerce和Adobe Sensei不会收集个人身份信息。

- **目录**  — 产品元数据，例如名称、价格、可用性等。

安装 `magento/product-recommendations` 模块中， Adobe Sensei会聚合行为和目录数据，从而为每个推荐类型创建产品Recommendations。 然后，产品Recommendations服务会将这些推荐部署到您的店面。

## 后续步骤

请阅读以下主题以开始使用产品Recommendations:

- [如何实施产品Recommendations](implementation-workflow.md)

- [安装和配置产品Recommendations](install-configure.md)

- [创建产品Recommendations](create.md)
