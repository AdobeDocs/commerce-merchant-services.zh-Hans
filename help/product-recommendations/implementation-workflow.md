---
title: 实施工作流
description: 了解成功实施的步骤 [!DNL Product Recommendations] 你的店面。
exl-id: 766e1191-0330-4515-9331-e45318539dc9
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---

# 实施工作流

[!DNL Product Recommendations] 同时使用行为和目录数据：

- 行为 — 购物者在您网站上的参与数据，例如产品查看、添加到购物车的商品和购买。 Adobe Commerce和Adobe Sensei不收集个人身份信息。

- 目录 — 产品元数据，如名称、价格和可用性。

当您安装 `magento/product-recommendations module`，Adobe Sensei会聚合行为和目录数据并创建 [!DNL Product Recommendations] 适用于每种推荐类型。 此 [!DNL Product Recommendations] 然后，服务将这些推荐部署到您的店面。 要帮助您在店面中实施产品推荐，请使用以下工作流：

>[!NOTE]
>
> 如果您的店面是使用PWA Studio实现的，请参阅 [PWA文档](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). 如果您使用自定义前端技术，例如React或Vue JS，请了解如何 [集成](headless.md) [!DNL Product Recommendations] 到你的无头店面。

## 工作流

1. **将数据收集部署到生产环境**

   部署 [!DNL Product Recommendations] 需要两个主节点 [数据源](type.md)：目录和行为。 由于生产是捕获和分析购物者行为的唯一环境，因此尽早在生产上开始数据收集符合您的最大利益。 [了解](behavioral-data.md) Adobe Sensei如何训练可生成高质量推荐的机器学习模型。 作为一项附加好处，当您开始收集生产中的行为数据时，可以 [获取推荐](verify.md) 基于此生产数据，同时在非生产环境中运行。 然后，您可以测试和试验根据生产中收集的真实购物者数据计算的各种推荐。

   要将数据收集部署到生产环境，您必须 [安装和配置](install-configure.md) 此 [!DNL Product Recommendations] 模块 [API密钥](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html).

   >[!TIP]
   >
   > 部署数据收集不会更改店面的外观或购物者的体验。 只有创建和部署推荐单元才能改变店面的客户体验。 在部署到生产环境之前，请确保在非生产环境中进行测试。 此外，在自定义模板之前，请勿创建推荐单位。 请参阅下一步。

1. **自定义模板以匹配您的样式**

   您的店面代表您的品牌，因此请确保修改产品推荐模板以匹配您的站点主题。

   >[!TIP]
   >
   > 通过自定义模板，您可以指定样式表、覆盖推荐单元在页面上的显示位置等。

   参见 [自定义](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/customize.html) ，了解如何完成此步骤。

1. **在非生产环境中测试推荐**

   在将技术部署到生产环境之前，最好在非生产环境中测试新技术。 通过在非生产环境中测试推荐，您可以播放不同的推荐单元类型、位置和页面。 您可以在非生产环境中进行测试时，根据已在生产环境中收集的行为数据提取推荐，以使推荐结果基于实际客户的购物行为。

   >[!TIP]
   >
   > 确保您的非生产环境目录与生产环境中的目录大致相同。 使用类似的目录可确保推荐单元中返回的产品与生产中的产品非常相似。

   参见 [Fetch](staging-environment.md) 生产环境中的行为数据，以了解如何完成此步骤。

1. **创建建议并将其部署到生产店面**

   现在，您已部署了生产中的行为数据收集、修改了产品推荐模板，并使用实际购物者行为测试了推荐，接下来可以将所有代码提升到生产环境并 [创建](create.md) 实时产品推荐。
