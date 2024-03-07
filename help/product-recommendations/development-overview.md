---
title: 产品Recommendations管理员开发
description: 产品Recommendations架构和开发功能的概述。
exl-id: caef5e0c-dd69-4846-8f85-b1c5e1c6a28f
source-git-commit: a433d970e83792a9f53b2a09afd84c335d980024
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# 产品Recommendations管理员开发

产品Recommendations是一款功能强大的营销工具，可用于提高转化率、增加收入和刺激购物者参与。 产品Recommendations以单元（如“查看了这个产品的客户也查看了”、“购买了这个产品的客户也购买了”、“为您推荐”等）的形式出现在店面上。 Adobe Commerce产品Recommendations由提供支持 [Adobe Sensei](https://www.adobe.com/sensei.html)，它使用人工智能和机器学习算法对汇总的购物者数据进行深度分析。 此数据与Commerce目录结合使用后，可为购物者提供引人入胜、相关且个性化的体验。

>[!NOTE]
>
>如果您的店面是使用PWA Studio实现的，请参阅 [PWA文档](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). 如果您使用自定义前端技术，例如React或Vue JS，请参阅用户指南，以了解如何在中集成Product Recommendations [headless](headless.md) 环境。 Headless实例必须实施事件才能为产品推荐工作区提供支持。

## 架构概述

从较高层面看，Commerce产品Recommendations部署为SaaS。 Commerce端包括店面（包含事件收集器和推荐布局模板）和后端（包括Data Services、SaaS导出模块和管理员UI）。 Adobe Sensei情报服务在SaaS方面得到利用。

![产品推荐架构图](assets/arch-diag-sensei.svg)

安装和配置推荐模块后，您的店面将开始收集行为数据。 Adobe Sensei会处理此行为数据与您的目录数据，并计算推荐服务所利用的产品关联。 此时，商家可以直接从管理UI创建、管理产品推荐单元并将其部署到其店面。

## 数据类型

产品Recommendations需要以下数据：

- **行为**  — 购物者在您网站上的参与数据，例如产品查看次数、添加到购物车的商品数，以及购买次数。 Commerce和Adobe Sensei不收集个人身份信息。

- **目录**  — 产品元数据，如名称、价格、可用性等。

当您安装 `magento/product-recommendations` 模块时，Adobe Sensei会聚合行为和目录数据，并为每种推荐类型创建产品Recommendations 。 然后，产品Recommendations服务会将这些推荐部署到您的店面。

>[!NOTE]
>
>对于可配置产品，产品Recommendations使用推荐单元中的父产品的图像。 如果可配置产品未指定图像，则该特定产品的推荐单元将为空。

## 后续步骤

请阅读以下主题以开始使用产品Recommendations：

- [如何实施产品Recommendations](implementation-workflow.md)

- [安装和配置产品Recommendations](install-configure.md)

- [创建产品Recommendations](create.md)
