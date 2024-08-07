---
title: 行为数据
description: 了解行为数据以及何时可以开始使用它。
exl-id: d68a97b9-1497-4603-a72c-4aaaf6e048cb
source-git-commit: 840b091638aedd3f6ac097a010d035eff997ffe2
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 0%

---

# 行为数据

某些推荐类型使用购物者的行为数据来训练机器学习模型，以构建个性化推荐。 其他推荐类型仅使用目录数据，不使用任何行为数据。 如果要快速启动，可以使用以下仅目录推荐类型：

- `More like this`
- `Visual similarity`

那么，您何时可以开始使用使用使用行为数据的推荐类型？ 视情况而定。 这称为&#x200B;_冷启动_&#x200B;问题。

_Cold Start_&#x200B;问题是对模型需要训练多少时间才能被视为高品质的度量。 在产品推荐中，这相当于等待Adobe Sensei培训其机器学习模型，然后再在您的网站上部署推荐单元。 这些模型拥有的数据越多，推荐就越准确和有用。 收集此类数据需要时间，并且会因流量而异。 由于此数据只能在生产网站上收集，因此请尽早将数据收集部署在该网站上，这符合您的最大利益。 您可以通过[安装和配置](install-configure.md) `magento/production-recommendations`模块来完成此操作。

下表针对为每种推荐类型收集足够数据所花费的时间提供了一般性指导：

| 推荐类型 | 训练时间 | 注释 |
|---|---|---|
| 基于热门程度(`Most viewed`， `Most purchased`， `Most added to cart`) | 不同 | 取决于事件数量 — 查看次数最常见，因此学习速度更快；然后添加到购物车，再购买 |
| `Viewed this, viewed that` | 需要更多培训 | 产品查看量非常大 |
| `Viewed this, bought that`，`Bought this, bought that` | 需要最多的培训 | 购买事件是商业网站上最罕见的事件，尤其是与产品查看次数相比 |
| `Trending` | 需要三天的数据来建立热门程度基线 | 趋势是衡量产品受欢迎程度与其自身受欢迎程度基线相比的近期动向。 产品的趋势分数是使用前景集（过去24小时内的最近热门程度）和背景集（过去72小时内的热门程度基线）计算的。 如果某个项目在过去24小时内变得比其基准受欢迎度高得多，则会获得高趋势得分。 每个产品都有此分数，而无论何时最高的分数都包含最热门的产品集。 |

可能影响培训所需时间的其他变量：

- 更高的流量有助于更快的学习
- 某些推荐类型的训练速度比其他推荐类型快
- Adobe Commerce每四小时重新计算一次行为数据。 在您的网站上使用它们的时间越长，Recommendations就越准确。

为了帮助您可视化每个推荐类型的培训进度，[创建推荐](create.md)页面会显示就绪指示器。

在收集生产数据和训练机器学习模型的同时，您可以实施将推荐部署到店面所需的[剩余任务](implementation-workflow.md)。 在您完成测试和配置推荐后，机器学习模型已经收集和计算了足够的数据来构建相关推荐，因此您可以将推荐部署到店面。

如果大多数SKU的流量（查看次数、购买的产品、趋势）不足，则可能没有足够的数据来完成学习过程。 这可能会导致管理员中的就绪指示器看上去卡住。
就绪指示器旨在为商家提供另一个数据点，以便选择哪种推荐类型更适合他们的商店。 这些数字可作为指引，可能永远不会达到100%。

## 备用建议 {#backuprecs}

如果没有足够的输入数据来在一个单元中提供所有请求的推荐项，Adobe Commerce将提供备用推荐以填充推荐单元。 例如，如果您将`Recommended for you`推荐类型部署到主页，则您网站上的首次购物者未生成足够的行为数据来准确推荐个性化产品。 在这种情况下，Adobe Commerce会根据`Most viewed`推荐类型向此购物者显示项目。

如果收集的输入数据不足，则以下推荐类型回退到`Most viewed`推荐类型：

- `Recommended for you`
- `Viewed this, viewed that`
- `Viewed this, bought that`
- `Bought this, bought that`
- `Trending`
- `Conversion (view to purchase)`
- `Conversion (view to cart)`
