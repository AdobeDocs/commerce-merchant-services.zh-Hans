---
title: 行为数据
description: 了解行为数据以及何时开始使用它。
exl-id: d68a97b9-1497-4603-a72c-4aaaf6e048cb
source-git-commit: 840b091638aedd3f6ac097a010d035eff997ffe2
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 0%

---

# 行为数据

某些推荐类型使用购物者的行为数据来培训机器学习模型以构建个性化推荐。 其他推荐类型仅使用目录数据，而不使用任何行为数据。 如果您想要快速开始，可以使用以下仅目录推荐类型：

- `More like this`
- `Visual similarity`

那么，您何时可以开始使用使用行为数据的推荐类型？ 视情况而定。 这称为 _冷启动_ 问题。

的 _冷启动_ 问题是衡量一个模型需要多长时间才能被视为高质量。 在产品推荐中，这意味着在网站上部署推荐单元之前，需要等待Adobe Sensei培训其机器学习模型。 这些模型拥有的数据越多，推荐就越准确和有用。 收集此数据需要时间，并会因流量而异。 由于此数据只能在生产网站上收集，因此尽早在该网站上部署数据收集符合您的最佳利益。 您可以通过 [安装和配置](install-configure.md) the `magento/production-recommendations` 模块。

下表为收集每个推荐类型足够数据所花费的时间提供了一些一般指导：

| 推荐类型 | 培训时间 | 注释 |
|---|---|---|
| 基于热门程度(`Most viewed`, `Most purchased`, `Most added to cart`) | 不同 | 取决于事件的数量 — 查看次数最为常见，因此学习速度更快；然后添加到购物车，然后购买 |
| `Viewed this, viewed that` | 需要更多培训 | 产品查看次数非常多 |
| `Viewed this, bought that`, `Bought this, bought that` | 需要最多的培训 | 购买事件是商务网站上最少见的事件，尤其是与产品查看次数相比 |
| `Trending` | 需要三天的数据才能确定受欢迎程度基准 | 趋势是与产品自身的受欢迎程度基准相比，衡量产品近期受欢迎程度的指标。 产品的趋势分数使用前台集（最近在24小时内的受欢迎程度）和后台集（72小时内的受欢迎程度基准）计算。 如果某个项目在过去24小时内比其基准受欢迎程度更受欢迎，则它会获得高趋势分数。 每个产品都有此分数，而任何时候获得最高分数的产品，都包含一组热门趋势产品。 |

可影响培训所需时间的其他变量：

- 流量越大，学习速度越快
- 某些推荐类型的培训速度比其他类型快
- Adobe Commerce每四小时重新计算一次行为数据。 Recommendations在您的网站上使用的时间越长，它们的准确度就越高。

为了帮助您可视化每种推荐类型的培训进度， [创建推荐](create.md) 页面显示就绪指示器。

在收集有关生产和机器学习模型的数据时，您可以实施 [剩余任务](implementation-workflow.md) 将推荐部署到店面时必需。 在您完成测试和配置推荐时，机器学习模型已收集并计算足够的数据来构建相关推荐，从而允许您将推荐部署到店面。

如果大多数SKU的流量（查看次数、购买的产品数、趋势）不足，则可能没有足够的数据来完成学习过程。 这可能导致管理员中的就绪指示器看起来好像卡住了。
准备情况指标旨在为商户提供另一个数据点，以便选择哪种推荐类型更适合其商店。 数字是指南，可能永远不会达到100%。

## 备用建议 {#backuprecs}

如果没有足够的输入数据来提供单位中所有请求的推荐项目，则Adobe Commerce会提供用于填充推荐单位的备用推荐。 例如，如果您部署 `Recommended for you` 推荐类型，则首次访问您网站的购物者尚未生成足够的行为数据来准确推荐个性化产品。 在这种情况下，Adobe Commerce会根据 `Most viewed` 此购物者的推荐类型。

以下推荐类型回退到 `Most viewed` 如果收集的输入数据不足，则为推荐类型：

- `Recommended for you`
- `Viewed this, viewed that`
- `Viewed this, bought that`
- `Bought this, bought that`
- `Trending`
- `Conversion (view to purchase)`
- `Conversion (view to cart)`
