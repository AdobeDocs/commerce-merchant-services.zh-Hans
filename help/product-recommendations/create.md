---
title: 创建新推荐
description: 了解如何创建产品推荐单位。
exl-id: d393ab78-0523-463f-9b03-ad3f523dce0f
source-git-commit: d56fd57281a5b675e128cca75d4057756a0bf4bf
workflow-type: tm+mt
source-wordcount: '853'
ht-degree: 0%

---

# 创建新推荐

在创建推荐时，您需要 _推荐单位_ 包含推荐的产品 _个项目_.

![推荐单位](assets/unit.png)
_推荐单位_

激活推荐单元后，Adobe Commerce将开始 [收集数据](workspace.md) 用于测量展示次数、查看次数、点击次数等。 此 [!DNL Product Recommendations] 此表显示每个推荐单位的量度，以帮助您做出明智的业务决策。

1. 在 _管理员_ 侧栏，转到 **营销** > _促销活动_ > **产品Recommendations** 以显示 _产品Recommendations_ 工作区。

1. 指定 [商店视图](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) 您希望推荐显示的位置。

   >[!NOTE]
   >
   > 必须在默认商店视图中创建Page Builder推荐单位，然后才可以在任何位置使用。 要了解有关使用页面生成器创建产品推荐的更多信息，请参阅 [添加内容 — 产品Recommendations](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html).

1. 单击 **创建推荐**.

1. 在 _为您的推荐命名_ 部分，输入描述性名称以供内部参考，例如 `Home page most popular`.

1. 在 _选择页面类型_ 部分，从以下选项中选择要在其中显示推荐的页面：

   - 主页
   - 类别
   - 产品详细信息
   - 购物车
   - 确认
   - [页面生成器](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html)

   您最多可以为每种页面类型创建5个有效的推荐单位，并为页面生成器创建25个有效的推荐单位。 当达到限制时，页面类型将灰显。

   ![推荐名称和页面](assets/create-recommendation.png)
   _推荐名称和页面位置_

1. 在 _选择推荐类型_ 部分，指定 [推荐类型](type.md) 您希望显示在所选页面上。 对于某些页面， [投放](placement.md) 个建议中的个建议仅限用于某些类型。

   某些推荐类型使用购物者的行为数据来 [训练机器学习模型](behavioral-data.md) 以构建个性化推荐。 为了帮助您可视化每种推荐类型的培训进度，此部分显示每种类型的准备程度度量。 这些就绪性指标是根据以下两个因素计算的：

   - 足够的结果集大小：在大多数情况下返回的结果是否足够以避免使用 [备用建议](behavioral-data.md#backuprecs)？

   - 结果集种类充足：返回的产品是否代表目录中的各种产品？ 此因素的目标是避免少数产品成为网站上唯一推荐的项目。

   根据上述因素，计算并显示就绪值。 当推荐类型的就绪值达到或高于75%时，会将该推荐类型视为准备部署。 当推荐类型的准备程度至少为50%时，即被视为部分准备就绪。 最后，推荐类型在其就绪值小于50%时被视为未做好部署准备。

   ![推荐类型](assets/create-recommendation-select-type.png)
   _推荐类型_

1. 在 _店面显示标签_ 部分，输入 [标签](placement.md#recommendation-labels) 对您的购物者可见，例如“最畅销商品”。

1. 在 _选择产品数量_ 部分，使用滑块指定要在推荐单元中显示的产品数量。

   默认为 `5`，最大值为 `20`.

1. 在 _选择投放位置_ 部分，指定推荐单位在页面上的显示位置。

   - 在主内容的底部
   - 在主内容的顶部

1. （可选）要更改推荐的顺序，请选择并移动 _选择位置_ 表格。

   此 _选择位置_ 部分显示为所选页面类型创建的所有推荐（如果有）。

   ![推荐顺序](assets/create-recommendation-select-placement.png)
   _页面上的推荐顺序_

1. （可选）在 _筛选器_ 部分， [应用筛选器](filters.md) 控制推荐单元中显示的产品。

   ![推荐过滤器](assets/create-recommendation-filter-products.png)
   _推荐产品过滤器_

1. 完成后，单击以下选项之一：

   - **另存为草稿** 以稍后编辑推荐单元。 您无法修改处于草稿状态的推荐单元的页面类型或推荐类型。

   - **激活** 以启用店面上的推荐单元。

## 预览Recommendations {#preview}

此 _推荐的产品预览_ 面板始终可用于示例产品选择，当建议单元部署到店面时，这些产品选择可能会显示在建议单元中。

要在非生产环境中工作时测试推荐，您可以从获取推荐数据 [不同来源](settings.md). 这允许商家在部署到生产环境之前试验规则并预览推荐。

| 字段 | 描述 |
|---|---|
| 名称 | 产品的名称。 |
| SKU | 分配给产品的库存单位 |
| 价格 | 产品的价格。 |
| 结果类型 | 主要 — 表示收集的训练数据足以显示推荐。<br />备份 — 表示收集的训练数据不足，因此使用备份推荐来填充插槽。 转到 [行为数据](behavioral-data.md) 详细了解机器学习模型和备用推荐。 |

在创建推荐单元时，请尝试使用页面类型、推荐类型和过滤器，以立即实时获取有关将包含的产品的反馈。 当您开始了解显示哪些产品时，可以配置推荐单元以满足您的业务需求。

Adobe Commerce [过滤器](filters.md) 推荐，以避免在单个页面上部署多个推荐单元时显示重复的产品。 因此，预览面板中显示的产品可能与店面中显示的产品不同。

>[!NOTE]
>
> 您无法预览 `Recently viewed` 推荐类型，因为数据在管理员中不可用。
