---
title: 创建新推荐
description: 了解如何创建产品推荐单元。
exl-id: d393ab78-0523-463f-9b03-ad3f523dce0f
source-git-commit: 51ff52eba117fe438d592ca886dbca25304a0d15
workflow-type: tm+mt
source-wordcount: '1022'
ht-degree: 0%

---

# 创建新推荐

在创建推荐时，您需要创建 _推荐单位_ 包含推荐的产品 _个项目_.

![推荐单位](assets/unit.png)
_推荐单位_

激活推荐单元后，Adobe Commerce将开始 [收集数据](workspace.md) 用于测量展示次数、查看次数、点击次数等。 此 [!DNL Product Recommendations] 此表显示每个推荐单位的量度，以帮助您做出明智的业务决策。

1. 在 _管理员_ 侧栏，转到 **营销** > _促销活动_ > **产品Recommendations** 以显示 _产品Recommendations_ 工作区。

1. 指定 [商店视图](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) 您希望推荐显示的位置。

   >[!NOTE]
   >
   > 必须在默认的存储区视图中创建Page Builder推荐单元，然后才可以在任何位置使用。 要了解有关使用页面生成器创建产品推荐的更多信息，请参阅 [添加内容 — 产品Recommendations](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html).

1. 单击 **创建推荐**.

1. 在 _为您的推荐命名_ 部分，输入用于内部参考的描述性名称，例如 `Home page most popular`.

1. 在 _选择页面类型_ 部分，从以下选项中选择要在其中显示推荐的页面：

   >[!NOTE]
   >
   > 将商店配置为时，“购物车”页面上不支持产品Recommendations [将产品添加到购物车后立即显示购物车页面](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/cart/cart-configuration.html#redirect-to-cart).

   * 主页
   * 类别
   * 产品详细信息
   * 购物车
   * 确认
   * [页面生成器](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html)

   您最多可以为每种页面类型创建5个有效的推荐单元，为页面生成器创建25个有效的推荐单元。 当达到限制时，页面类型将灰显。

   ![推荐名称和页面](assets/create-recommendation.png)
   _推荐名称和页面放置_

1. 在 _选择推荐类型_ 部分，指定 [推荐类型](type.md) 您希望显示在选定的页面上。 对于某些页面， [投放](placement.md) 个推荐仅限特定类型。

1. 在 _店面显示标签_ 部分，输入 [标签](placement.md#recommendation-labels) 例如，“最畅销商品”等购物者可以看到这些内容。

1. 在 _选择产品数量_ 部分，使用滑块指定要在推荐单元中显示的产品数量。

   默认为 `5`，最大值为 `20`.

1. 在 _选择投放位置_ 部分，指定推荐单元在页面上的显示位置。

   * 在主内容的底部
   * 在主内容的顶部

1. （可选）要更改推荐的顺序，请选择并移动 _选择位置_ 表格。

   此 _选择位置_ 部分显示为所选页面类型创建的所有推荐（如果有）。

   ![推荐顺序](assets/create-recommendation-select-placement.png)
   _页面上的推荐顺序_

1. （可选）在 _过滤器_ 部分， [应用过滤器](filters.md) 控制推荐单元中显示的产品。

   ![推荐过滤器](assets/create-recommendation-filter-products.png)
   _推荐产品过滤器_

1. 完成后，单击下列选项之一：

   * **另存为草稿** 以稍后编辑推荐单元。 您无法修改处于草稿状态的推荐单元的页面类型或推荐类型。

   * **激活** 以启用店面上的推荐单元。

## 就绪指示器

某些推荐类型使用来自购物者的行为数据来 [训练机器学习模型](behavioral-data.md) 以构建个性化推荐。

只需要目录数据。 无需行为数据即可实现这些目标：

* _最喜欢这个_
* _最近查看的项目_
* _视觉相似度_

基于最近六个月的店面行为数据：

* _查看了这个项目，也查看了那个项目_
* _查看了这个项目，购买了那个项目_
* _购买了此项，也购买了此项_
* _为您推荐_

基于人气的推荐类型使用最近七天的店面行为数据：

* 查看次数最多
* 购买次数最多
* 已添加到购物车
* 趋势

就绪指示器值预计会由于以下因素而波动，例如目录的总体大小、产品交互事件的数量（查看次数、添加到购物车的次数、购买次数）以及在特定时间范围内注册这些事件的SKU的百分比，如上所示。 例如，在节假日流量高峰期，就绪指示器显示的值可能高于正常流量时的值。

为了帮助您可视化每种推荐类型的培训进度， _选择推荐类型_ 部分显示每种类型的就绪性度量。 这些准备情况指标的计算基于两个因素：

* 足够的结果集大小：在大多数情况下返回的结果是否足够以避免使用 [备用建议](behavioral-data.md#backuprecs)？

* 充分的结果集多样性：返回的产品是否代表您目录中的各种产品？ 此因素的目标是避免少数产品成为整个站点中唯一推荐的项目。

基于上述因素，计算并显示就绪值。 当推荐类型的就绪值达到或高于75%时，会将该推荐类型视为准备部署。 推荐类型在就绪性至少为50%时被视为部分就绪。 当推荐类型的就绪值小于50%时，会将该推荐类型视为未准备好部署。 这些是一般准则，但根据收集数据的性质，每个具体情况可能有所不同，如上所述。

![推荐类型](assets/create-recommendation-select-type.png)
_推荐类型_

>[!NOTE]
>
>指标可能永远不会达到100%。

## 预览Recommendations {#preview}

此 _推荐的产品预览_ 将面板部署到店面时，该面板始终与推荐单元中可能显示的产品示例选项一起可用。

要在非生产环境中工作时测试推荐，您可以从获取推荐数据 [不同来源](settings.md). 这允许商家在部署到生产环境之前试验规则并预览推荐。

| 字段 | 描述 |
|---|---|
| 名称 | 产品的名称。 |
| SKU | 分配给产品的库存单位 |
| 价格 | 产品的价格。 |
| 结果类型 | 主要 — 表明收集的训练数据足以显示推荐。<br />备份 — 表明收集的训练数据不足，因此使用备份推荐来填充插槽。 转到 [行为数据](behavioral-data.md) 了解有关机器学习模型和备用推荐的更多信息。 |

在创建推荐单元时，请尝试使用页面类型、推荐类型和过滤器，以立即实时获取有关将包含的产品的反馈。 当您开始了解要显示哪些产品时，可以配置推荐单元以满足您的业务需求。

Adobe Commerce [过滤器](filters.md) 推荐，以避免在单个页面上部署多个推荐单元时显示重复的产品。 因此，预览面板中显示的产品可能与店面中显示的产品不同。

>[!NOTE]
>
> 您无法预览 `Recently viewed` 推荐类型，因为数据在管理员中不可用。
