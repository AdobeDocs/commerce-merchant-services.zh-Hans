---
title: '[!DNL Live Search]最佳实践'
description: 了解在商店中实施 [!DNL Live Search] 的最佳实践。
role: Admin, Developer
exl-id: 69b2c2a6-c8a9-4640-8d2b-08fcd7a96034
source-git-commit: ba2b798f2e7d5716be0d1686359ac8382f6cf8e4
workflow-type: tm+mt
source-wordcount: '2426'
ht-degree: 0%

---

# 最佳实践

本文可帮助商家增强其网站搜索功能，确保提供无缝且高效的购物者体验，从而最大限度地提高转化率。 通过遵循概述的策略，您可以了解如何实施高级搜索功能，并不断改进搜索工具以使Adobe Commerce [!DNL Live Search]获得最佳性能。

有几个关键因素决定了搜索结果的关联性和有效性：

- 结构良好的产品数据确保搜索算法能够有效地将产品与查询相匹配。 低质量的产品数据会导致相关搜索结果较低。 要直接影响促销策略的成功，请执行以下操作：
   - 将正确的属性设置为可搜索属性及其相应的权重。
   - 确保这些属性中的数据相关。
- 设计良好的搜索体验与客户建立了信任，并让他们相信自己会找到所需的内容。
- 搜索规则至关重要，因为它们可以根据热门程度、新到达次数、促销标准或任何其他促销策略来提高某些产品的可见性，以满足您的业务需求。
- 多面向导航让购物者能够优化搜索并快速获得相关结果。

要管理[!DNL Live Search]，请在Adobe[!DNL Commerce]管理员中转到&#x200B;**营销** > *SEO和搜索* > **[!DNL Live Search]**。 

## 优化搜索功能

在本节中，您将了解如何使用自动完成等功能来优化搜索功能，从而提供购物者类型、同义词和拼写形式的实时建议，以确保购物者能够找到产品（即使他们使用不同的单词），Facet允许购物者缩小搜索结果范围，而搜索重定向会将购物者从搜索查询自动重定向到特定页面。

### 自动完成

自动完成（也称为提前键入或自动建议）是一种交互式搜索功能，可在购物者输入搜索词时动态地向购物者显示建议。 这有助于购物者根据自己的意见提供实时建议，从而快速轻松地找到产品。

[!DNL Live Search] [[!DNL popover]](storefront-popover.md)小组件启用自动完成搜索选项以建议常用产品。 购物者键入每个字符后，弹出窗口将更新为建议的产品和排名最前的搜索结果的缩略图图像。

当用户键入两个字符后，[!DNL Live Search]开始返回结果。 对于部分匹配，每个单词的最大字符数为20。 “键入时搜索”查询中的字符数无法配置。

了解有关[弹出框](storefront-popover.md)小组件的更多信息。

### 同义词和拼写错误

默认情况下，实时搜索会管理错误拼写。 您可以设置同义词，以包含购物者可能使用的与目录中指定单词不同的单词。 您不希望因为某人正在寻找“沙发”而失去销售，而您的产品却被列为“沙发”。 您可以通过输入客户可能用于查找产品的所有词来捕获广泛的搜索词。 您可以[将同义词设置为单向或双向](synonyms-add.md#step-2-define-the-synonym-by-type)以改进结果。

#### 优化同义词的提示

- 将品牌名称和缩写映射到其全名，例如“HP”映射到“Hewlett-Packard”，将常用产品昵称映射到“iPhone”映射到“Apple iPhone”。
- 包括特定行业的术语和购物者可能互换使用的术语，例如“运动鞋”和“跑鞋”。
- 根据新的搜索趋势、产品添加和购物者行为定期更新同义词列表。
- 通过分析搜索结果和购物者反馈来测试同义词映射的有效性。 优化映射以提高准确性和相关性。

了解有关同义词的更多信息：

- [同义词的类型](synonyms-type.md)
- [创建同义词](synonyms-add.md)
- [管理同义词](synonyms-manage.md)
- [语言支持](settings.md#language)

### Facet

过滤器和彩块化功能是[!DNL Commerce]网站的关键组件，旨在通过允许购物者缩小搜索结果范围并更有效地查找产品来增强购物者体验。 此功能通过应用特定标准来帮助购物者对数量庞大的商品目录进行排序，从而使购物过程更快、更容易、更令人满意。 通过实施有效、对购物者友好的过滤器和彩块化，您可以帮助客户快速高效地找到他们所需的内容，最终提高满意度和转化率。

要将产品属性设置为Facet，它必须设置以下[属性](facets-add.md#step-1-add-a-facet)：

- **[!UICONTROL Use in Search]** -  `Yes`
- **[!UICONTROL Use in Layered Navigation]** -  `Filterable (with results)`
- **[!UICONTROL Use in Search Results Layered Navigation]** -  `Yes`

#### 优化彩块化的提示

- 确定产品最相关且最有用的属性，如标题、类别、品牌、价格范围、颜色和大小，并将它们设置为[动态Facet](facets-type.md)。 
- 设置和排序在您的目录范围内一致且与您的产品高度相关的产品属性，以提高关联性和过滤功能，从而帮助购物者。
- 确保Facet标签易于理解并在整个站点中以一致的方式命名。 例如，使用“价格范围”而不是“成本”。
- 避免让购物者不知所措，将小面的数量限制在最重要的方面。 太多选项可能会导致决策疲劳。 默认情况下，[!DNL Live Search]限制为最多100个配置为Facet的属性，并在每个Facet中返回30个存储段。 了解有关[方面限制](boundaries-limits.md#facets)的更多信息。 
- 允许购物者同时选择多个筛选条件以优化结果。 例如，允许购物者同时选择“红色”和“蓝色”颜色。
- 在每个Facet选项旁边显示可用产品的数量，以便让购物者了解他们可期待的搜索结果。
- 实施可折叠的Facet部分以保持接口干净且可管理，尤其是在移动设备上。
- 允许购物者轻松重置单个Facet或所有选定的过滤器以启动新搜索。

了解有关Facet的更多信息：

- [彩块化的类型](facets-type.md)
- [添加Facet](facets-add.md)
- [管理Facet](facets-manage.md) （编辑、固定Facet、删除、发布）
- [价格刻面](settings.md#price-faceting)

### 搜索重定向

搜索重定向允许您自动将购物者从搜索查询重定向到特定页面。 搜索重定向可以改善购物者体验并引导客户查看最相关的内容，例如产品页面、类别、登陆页面或一组量身定制的搜索结果。 搜索重定向有助于简化购物体验，并确保购物者能够快速高效地找到他们想要的东西。

设置搜索重定向的推荐用例：

- **热门产品或类别** — 当购物者搜索常用或热门术语时，将他们重定向到特定的产品页面或类别。 例如，搜索“iPhone”可能会直接重定向到iPhone类别页面或特定的模型页面。

- **促销活动** — 在促销活动或销售期间，将相关搜索词重定向到突出显示特殊优惠或特色产品的登陆页面。

- **品牌搜索** — 当购物者搜索品牌名称时，将它们重定向到该品牌的专用页面，其中列出了该品牌的所有产品。

- **产品停产** — 如果某个产品停产，您可以将对该产品的搜索重定向到相似的产品或该产品的新版本。

始终测试搜索重定向，以确保它们正常运行并导向最相关的页面。 持续监控其性能并根据需要进行调整。

了解如何[管理搜索重定向](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search-terms)。

## 改进搜索结果相关性

此部分讨论如何通过实施有效的搜索规则并使用产品元数据来确保准确而详细的属性可搜索来改进搜索结果相关性。

### 图像

确保可配置产品的子产品具有具有正确角色的图像。 拥有父产品或子产品可能会导致搜索结果没有图像。

>[!NOTE]
>
>搜索结果中的图像可能会因搜索词而异。 如果搜索词确定子产品更相关，则将使用子产品的图像，而不是父产品的图像。

### 搜索规则

要优化转化率和收入，您必须实施有效的搜索规则。 通过[搜索促销](rules.md)，根据销售数据、库存水平和促销活动调整产品排名。

制定一个经过深思熟虑的缺省搜索规则至关重要。 您的[默认规则](rules.md#default-rule)决定了搜索结果最初如何排序并显示给购物者，从而增强他们的整体体验并提高购买的可能性。 定期监控和调整此规则可确保它继续有效地满足购物者的需求和业务目标。

#### 优化搜索规则的提示

- 固定或提升具有高销量或近期销售活动的产品。
- 优先考虑具有高评级和正面评价的产品。
- 确保库存商品排名较高。
- 稍微优先处理利润率较高的产品，而不影响其相关性。
- 突出显示正在销售或属于特殊促销的产品。
- 通过使用促销期间的日期范围，在促销期间或销售期间自动设置搜索规则。
- 使用[智能排名](rules-add.md#intelligent-ranking)（例如“为您推荐”、“查看次数最多”等），根据每位购物者的行为定制搜索结果。 要定制购物者行为，必须确保正确实施事件。 对于Luma商家，活动是现成可用的。 对于Headless或自定义实施，您必须根据特定需求[实施事件](events.md)。

了解有关搜索规则的更多信息：

- [促销工作区](rules-workspace.md#set-the-scope)
- [要求](rules.md#requirements)
- [默认搜索规则](rules.md#default-rule)
- 管理搜索规则
   - [创建](rules-add.md)
   - [编辑、查看、删除](rules-manage.md)
- 数据收集
   - [[!DNL Live Search]个事件](events.md)
   - [Adobe Commerce事件收集器](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/)
   - [GitHub Commerce事件](https://github.com/adobe/commerce-events/tree/main/examples) 

### 利用产品元数据

确保[将准确而详细的产品属性设置为可搜索](workspace.md#set-attributes-as-searchable)。 请注意，默认情况下，SKU、名称和类别属性是可搜索的，不能从搜索中排除。 为获得最佳结果，请勿在SKU中使用空格。

要增加搜索相关性，请为每个可搜索属性分配一个权重。 权重较高的属性在搜索结果中应显示在较高的位置。 按相关性排序受多个标准影响，例如搜索权重。 这意味着，有时搜索权重较低的属性仍可以比搜索权重较高的属性具有更大的相关性。 其他标准可以包括任何给定属性中的匹配数、找到的搜索词的位置以及搜索词之前和之后的整体文本结构。

确保每个产品在每个可搜索属性内都包含相关内容。 如果属性包含大量内容，则建议不要将属性设置为可搜索，因为这样可能会降低搜索结果的相关性。

了解有关搜索的产品属性的更多信息：

- [将属性设置为可搜索](workspace.md#set-attributes-as-searchable)
- [为属性分配权重](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search-results#weighted-search)

## 监控搜索结果

要使用[!DNL Live Search]优化搜索结果，请监控相关关键绩效指标(KPI)（如独特查询、平均点击位置、点进率、转化率和零结果率），以了解购物者如何与您的搜索功能进行交互。 此数据可指导您定期更新和优化搜索规则。

您可以在[!DNL Live Search] [性能工作区](performance.md)中监视这些KPI，您可以在其中找到以下量度： 

- **唯一搜索** — 在您的[!DNL Commerce]网站上执行的不同搜索查询计数。 每个唯一搜索仅计数一次，即使同一购物者或不同购物者多次重复搜索也是如此。 此量度可帮助您了解客户使用的搜索词的多样性，并让您深入了解购物者想要的产品或信息。 跟踪唯一搜索允许您：

   - 识别热门搜索趋势和经常搜索的项目。
   - 检测产品目录或内容中的潜在差距。
   - 通过添加[同义词](synonyms.md)、创建或更新搜索规则优化您的搜索功能。

- **平均点击位置** — 指示购物者在您的网站上执行搜索查询后点击的搜索结果的平均位置。 此量度可让您深入了解搜索结果的相关性和有效性。

  较低的平均点击位置（接近1）表示购物者会快速找到相关结果，这表示您的搜索策略有效。 它有助于您了解购物者的行为以及他们愿意滚动多远才能找到所需的产品。 如果平均点击位置很高，则可能表示最相关的结果未出现在顶部，这要求对搜索策略进行审查和优化。

- **点进率(CTR)** — 测量执行搜索查询后点击搜索结果的购物者百分比。 CTR高表明搜索结果与购物者相关，并且很有吸引力，因为他们会单击找到的结果。 监测CTR有助于确定需要改进的方面。 低CTR可能表明搜索结果与购物者意图不匹配，从而提示需要优化搜索规则、增强产品数据或改进结果呈现。

- **转化率** — 表明您的搜索功能在推动销售和实现业务目标方面的有效性。 它反映了搜索功能在满足购物者需求和促进顺畅购物体验方面的整体有效性。 高转化率表示您的搜索结果高度相关且具有说服力，可引导购物者完成购买。 如果转化率很低，则可能会建议搜索相关性、产品可用性或购物者从搜索到购买的总体旅程中存在的问题。

- **零结果** — 测量[!DNL Commerce]网站上未返回任何结果的搜索查询百分比。 此量度对于了解购物者搜索不成功的频率至关重要，它可以帮助您洞察产品目录或搜索设置中的潜在差距。 较高的零销售率会让购物者感到沮丧，导致糟糕的购物体验和潜在的客户流失。 它可以指示购物者正在搜索目录中的缺失产品或类别，从而指导库存和产品列表决策。

  要降低零结果率，您可以：

   - 提供替代或相关搜索词，例如[同义词](synonyms.md)，但找不到完全匹配的搜索词。
   - 通过设置搜索重定向，在搜索未产生结果时为购物者提供相关或替代建议。
   - 定期查看零结果查询以确定模式并对产品目录和搜索设置进行必要的调整。

- **热门结果** — 可以通过使搜索结果与购物者的偏好和行为保持一致，显着增强搜索结果。

您可以使用此量度数据，并通过以下方式优化搜索功能：

- 实施规则以自动在搜索结果中对热门产品进行较高排名。 可以优先考虑经常点击或购买的产品，使其显示在顶部。 手动整理特定搜索查询的热门产品列表，并确保突出显示这些项目。
- 突出显示当前热门或最近人气飙升的产品。 这在季节性活动、节假日或促销期间特别有效。 要实现此目的，请在设置搜索规则时，使用更符合您的用例和业务需求的智能排名。
- 突出显示热门过滤器或彩块化（如果购物者经常按特定品牌或价格范围进行过滤），通过固定这些彩块化并将它们相应地排序，使这些选项更加突出。
- 当搜索产生零结果时，使用热门结果数据来建议具有高购物者参与度的替代产品或相关类别。
- 分析热门搜索词和产品数据以识别重要关键词。 使用这些关键字优化产品可搜索属性以提高搜索相关性。
- 定期分析结果数据以了解不断变化的趋势、购物者偏好和行为、识别热门搜索词以及检测问题。 使用此反馈循环不断优化和改进您的搜索规则和产品

要获取[!DNL Live Search]报表中的正确数据，必须确保正确实施事件。 对于Luma商家，活动是现成可用的。 对于Headless或自定义实施，您必须根据特定需求[实施事件](events.md)。