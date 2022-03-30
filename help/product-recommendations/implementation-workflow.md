---
title: 实施工作流程
description: 了解成功实施的步骤 [!DNL Product Recommendations] 在你的店面。
source-git-commit: 4ad607c8595b25d01b5f5020b787fc1d35d4df25
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

---

# 实施工作流程

[!DNL Product Recommendations] 同时使用行为数据和目录数据：

- 行为 — 来自您网站上购物者参与度的数据，例如产品查看次数、添加到购物车的项目以及购买次数。 Adobe Commerce和Adobe Sensei不会收集个人身份信息。

- 目录 — 产品元数据，如名称、价格和可用性。

安装 `magento/product-recommendations module`, Adobe Sensei汇总行为和目录数据并创建 [!DNL Product Recommendations] 的值。 的 [!DNL Product Recommendations] 然后，服务会将这些推荐部署到您的店面。 要帮助您在店面上实施产品推荐，请使用以下工作流：

>[!NOTE]
>
> 如果您的店面是使用PWA Studio实施的，请参阅 [PWA文档](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). 如果您使用自定义前端技术（如React或Vue JS），请了解如何 [集成](headless.md) [!DNL Product Recommendations] 进你的无头店。

## 工作流

1. **将数据收集部署到生产环境**

   部署 [!DNL Product Recommendations] 需要两个主要 [数据源](type.md):目录和行为。 由于生产是捕获和分析购物者操作的唯一环境，因此尽早开始收集生产数据符合您的最佳利益。 [学习](behavioral-data.md) Adobe Sensei如何训练机器学习模型，从而提供更优质的推荐。 作为附加的好处，当您开始收集有关生产的行为数据时，您可以 [获取推荐](verify.md) 在非生产环境中运行时，会根据此生产数据生成数据。 然后，您可以测试和试验基于生产中收集的实际购物者数据计算的不同推荐。

   要将数据收集部署到生产环境，您必须 [安装和配置](install-configure.md) the [!DNL Product Recommendations] 模块 [API密钥](https://docs.magento.com/user-guide/system/saas.html#apikey).

   >[!TIP]
   >
   > 部署数据收集不会更改店面的外观或购物者的体验。 只有创建和部署推荐单元，才会改变您店面上的客户体验。 在部署到生产之前，请确保在非生产环境中进行测试。 此外，在自定义模板之前，请勿创建推荐单元。 请参阅下一步。

1. **自定义模板以匹配您的样式**

   您的店面代表您的品牌，因此请确保修改产品推荐模板以匹配您的网站主题。

   >[!TIP]
   >
   > 通过自定义模板，可以指定样式表、覆盖推荐单元在页面上显示的位置等。

   请参阅 [自定义](https://devdocs.magento.com/recommendations/customize.html) ，以了解如何完成此步骤。

1. **在非生产环境中测试推荐**

   在部署到生产之前，始终最好在非生产环境中测试新技术。 在非生产环境中测试推荐允许您播放不同的推荐单元类型、位置和页面。 您可以在非生产环境中测试时，根据已在生产中收集的行为数据提取推荐，以便推荐结果基于实际客户的购物行为。

   >[!TIP]
   >
   > 确保您的非生产环境目录与生产环境目录大致相同。 使用相似的目录可确保推荐单元中返回的产品能够密切模拟生产中的产品。

   请参阅 [获取](staging-environment.md) 来自生产环境的行为数据，以了解如何完成此步骤。

1. **创建推荐并将其部署到生产店面**

   现在，您已在生产环境中部署行为数据收集、修改产品推荐模板，并使用实际的购物者行为测试推荐，接下来，您就可以将所有代码提升到生产环境和 [创建](create.md) 实时产品推荐。
