---
title: 产品Recommendations管理员开发
description: 产品Recommendations架构和开发功能的概述。
exl-id: caef5e0c-dd69-4846-8f85-b1c5e1c6a28f
source-git-commit: 4a5c3550b03651279c24de6b6361ffa6dc28776e
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# 产品Recommendations管理员开发

产品Recommendations是一款功能强大的营销工具，可用于提高转化率、增加收入和刺激购物者参与。 产品Recommendations以单元（如“查看了这个产品的客户也查看了”、“购买了这个产品的客户也购买了”、“为您推荐”等）的形式出现在店面上。 Adobe Commerce Product Recommendations由[Adobe Sensei](https://www.adobe.com/sensei.html)提供支持，后者使用人工智能和机器学习算法对汇总的购物者数据进行深入分析。 此数据与Commerce目录结合使用后，可为购物者提供引人入胜、相关且个性化的体验。

>[!NOTE]
>
>如果店面是使用PWA Studio实现的，请参阅[PWA文档](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/)。 如果您使用自定义前端技术，例如React或Vue JS，请参阅用户指南以了解如何在[headless](headless.md)环境中集成产品Recommendations。 Headless实例必须实施事件才能为产品推荐工作区提供支持。

## 架构概述

从较高层面来看，Commerce产品Recommendations部署为SaaS。 Commerce端包括店面（其中包含事件收集器和推荐布局模板）和后端（其中包含数据服务、SaaS导出模块和管理UI）。 Adobe Sensei情报服务在SaaS方面得到利用。

![产品推荐体系结构图](assets/arch-diag-sensei.svg)

安装和配置推荐模块后，您的店面将开始收集行为数据。 Adobe Sensei会处理此行为数据与您的目录数据，并计算推荐服务所利用的产品关联。 此时，商家可以直接从管理UI创建、管理产品推荐单元并将其部署到其店面。

## 后续步骤

请阅读以下主题以开始使用产品Recommendations：

- [如何实施产品Recommendations](implementation-workflow.md)

- [安装和配置产品Recommendations](install-configure.md)

- [创建产品Recommendations](create.md)
