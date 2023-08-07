---
title: ’[!DNL Product Recommendations] 发行说明
description: 的最新发行信息 [!DNL Product Recommendations] 来自Adobe Commerce的。
exl-id: 1758e688-d26f-45e7-818c-d4726338a6c3
feature: Services, Recommendations, Release Notes
source-git-commit: 91ad3b5f1fb9248685fc67071a7191dfbf6c2472
workflow-type: tm+mt
source-wordcount: '1144'
ht-degree: 0%

---

# [!DNL Product Recommendations] 发行说明

发行说明包含以下更新 [!DNL Product Recommendations] 模块：

* [!DNL Product Recommendations] 隐含： `magento/product-recommendations`
* 中的页面生成器支持 [!DNL Product Recommendations] （可选）模块： `magento/module-page-builder-product-recommendations`
* 的视觉相似性推荐类型支持 [!DNL Product Recommendations] （可选）模块： `magento/module-visual-product-recommendations`

为当前的主要发行版本提供支持。 提供了旧版本的发行说明以供参考。
发行说明包括：

![新建](../assets/new.svg) 新增功能
![修复](../assets/fix.svg) 修复和改进功能
![错误](../assets/bug.svg) 已知问题

请参阅开发人员文档以 [了解产品兼容性](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).

## 托管服务更新

这些说明描述了在未发布版本控制版本或对托管服务的改进的情况下发布的更新。

+++托管服务更新

_2023年7月18日_

![新建](../assets/new.svg) 产品Recommendations现在具有GraphQL [`recommendations`](https://developer.adobe.com/commerce/webapi/graphql/schema/product-recommendations/queries/recommendations/) 查询。

_2023年4月25日_

![新建](../assets/new.svg) Recommendations客户现在可以利用的产品 [SaaS价格索引](../price-index/index.md).

+++

## 当前主要版本

### 5.0.0个magento/product-recommendations

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新建](../assets/new.svg) 更新了产品Recommendations以支持Adobe Commerce 2.4.6。
![新建](../assets/new.svg) 这是一个主版本发行版本。 [编辑](install-configure.md#update) 根 `composer.json` 您的项目的文件。

#### 已知限制

* 此 `websiteCode` 如果值包含下划线(_)，则错误返回该值。

### 先前版本

+++4.0.1和之前的版本

### magento/product-recommendations的4.0.1

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![修复](../assets/fix.svg) 以前，当显示货币转换为非默认货币时，产品Recommendations会显示错误。 现在可以正常切换货币。

### magento/product-recommendations的4.0.0

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新建](../assets/new.svg) 已添加 [就绪指示器](create.md) 以帮助您可视化每个推荐类型的培训进度。
![新建](../assets/new.svg) 这是一个主版本发行版本。 [编辑](install-configure.md#update) 根 `composer.json` 您的项目的文件。 此版本还要求您在安装和配置Product Recommendations时提供两个API密钥： [生产密钥和沙盒密钥](../landing/saas.md).

#### 已知限制

* 此 `websiteCode` 如果值包含下划线(_)，则错误返回该值。

### 3.3.7 magento/product-recommendations

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新建](../assets/new.svg) 添加了PHP 8.1支持
![新建](../assets/new.svg) 改进了图像大小调整，以便在参考显示模板中可以更一致地处理图像大小调整

### 3.3.6的magento/product-recommendations

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新建](../assets/new.svg) 已优化 [!DNL Product Recommendations] 通过明确列出依赖关系进行中继

### 3.3.5的magento/product-recommendations

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新建](../assets/new.svg) 已添加 [B2B支持](onboarding.md#b2bsupport) 在产品Recommendations中
![新建](../assets/new.svg) 已将新信息源添加到 [同步目录数据](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) 到Commerce Services （通过命令行）

### 3.3.3的magento/product-recommendations

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新建](../assets/new.svg) 已添加新的 [推荐类型](type.md)：转化（查看到购物车）、转化（查看到购买）和最近查看。 这些新推荐类型可在 `magento/product-recommendations` 模块3.2.2及更高版本。
![修复](../assets/fix.svg) 修复了Fastly Web应用程序防火墙(WAF)错误地阻止Cookie的问题
![修复](../assets/fix.svg) 修复了分配给非默认商店视图的产品未显示在 _Recommendations产品预览_ 为特定商店视图创建推荐时的面板
![修复](../assets/fix.svg) 修复了页面生成器中的某些推荐单元名称阻止推荐单元显示在店面的问题

### 3.3.2的magento/product-recommendations

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![修复](../assets/fix.svg) 修复了缺少B2B支持的依赖关系

### 3.3.1的magento/product-recommendations

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新建](../assets/new.svg) 添加了对B2B客户组定价的支持。 当您设置 [价格筛选器](filters.md) 在推荐单位上，登录的B2B客户会看到所显示产品的客户组定价集。

### 3.3.0的magento/product-recommendations

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新建](../assets/new.svg) 增加了对Adobe客户端数据层的支持，以便跨Adobe Commerce功能和服务标准化行为数据收集。 请参阅 [readme](https://github.com/adobe/magento-storefront-event-collector/blob/main/README.md) 了解更多信息。

### 3.2.6的magento/product-recommendations

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![修复](../assets/fix.svg) 修复了JavaScript模式错误
![修复](../assets/fix.svg) 修复了Fastly Web应用程序防火墙(WAF)错误地阻止Cookie的问题

### 3.2.5的magento/product-recommendations

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新建](../assets/new.svg) 将Magento服务重命名为 [Commerce服务](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) 并提高了管理员的可用性

### 3.2.4的magento/product-recommendations

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![修复](../assets/fix.svg) 修复了为产品属性编制索引时出现“无法检索可配置产品选项数据”错误

### 3.2.3的magento/product-recommendations

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![修复](../assets/fix.svg) 修复了目录同步期间的“无法检索可配置产品选项数据”错误
![修复](../assets/fix.svg) 修复了在启用“将存储代码添加到URL”配置时存储代码设置不正确的问题
![修复](../assets/fix.svg) 改进了对Admin Panel配置更改的检测，以确保这些更改反映在目录同步数据中

### 3.2.2的magento/product-recommendations

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新建](../assets/new.svg) 添加了以下功能 [预览推荐结果](create.md) 在创建时。 这可能需要您将模块更新到最新版本。
![新建](../assets/new.svg) 添加了以下功能 [监控和管理](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) 管理员的目录同步过程。
![新建](../assets/new.svg) 已添加 [过滤器](filters.md) 控制推荐中显示的产品。
![新建](../assets/new.svg) 添加了 [视觉相似度](type.md#visualsim) 推荐类型。

### 用于页面生成器的magento/module-page-builder-product-recommendations的1.2.1

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新建](../assets/new.svg) 添加了对3.2.0+版本的 `magento/product-recommendations` 模块

### 3.1.0的magento/product-recommendations

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新建](../assets/new.svg) 添加了以下功能 [重新同步](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) 通过命令行将目录添加到SaaS服务。
![新建](../assets/new.svg) 添加了对数据库表前缀的支持
![修复](../assets/fix.svg) 删除了PHP 7.1支持

### 3.0.8的magento/product-recommendations

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![修复](../assets/fix.svg) 修复了在配置模块之前发送用于数据收集的事件，从而导致流量无效的问题

### 3.0.6的magento/product-recommendations

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新建](../assets/new.svg) **(Beta)** 包括支持新的 [视觉相似度](type.md#visualsim) 推荐类型。

### magento/module-visual-product-recommendations的1.0.0

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新建](../assets/new.svg) **(Beta)** [视觉相似度](type.md#visualsim). 使用 _视觉相似度_ 推荐类型，您可以将推荐单元部署到产品详细信息页面，该页面显示与正在查看的产品视觉上类似的产品。

### 3.0.5的magento/product-recommendations

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![修复](../assets/fix.svg) 修复了在目录导出期间可能发生的“无法检索产品选项数据”错误。
![修复](../assets/fix.svg) 中的货币符号 _收入_ 上的列 _产品Recommendations_ 功能板现在可正确反映配置的基本货币。

### 3.0.4的magento/product-recommendations

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![修复](../assets/fix.svg) 添加了对Adobe Commerce 2.4.0的支持

### 3.0.3的magento/product-recommendations

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![修复](../assets/fix.svg) 改进了店面模板中的符号实施

### 用于页面生成器的magento/module-page-builder-product-recommendations的1.0.4

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新建](../assets/new.svg) 在编辑Page Builder内容类型时添加了产品推荐名称

### 3.0.2 magento/product-recommendations

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新建](../assets/new.svg) 在Page Builder中选择推荐单元时，在网格中添加了状态列
![修复](../assets/fix.svg) 修复了产品和图像URL中的http/https协议不正确的问题

### 3.0.1的magento/product-recommendations

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

这是一个主版本发行版本。 [编辑](install-configure.md#update) 项目的根composer.json文件。

![新建](../assets/new.svg) Fetch [!DNL Product Recommendations] 来自备用SaaS数据空间。 这允许您在其他非生产环境中使用产品环境中计算的产品推荐。 [切换SaaS数据空间](settings.md) 进一步描述了此功能。

![修复](../assets/fix.svg) 修复了使用uBlock Origin禁止购物者结账的问题
![修复](../assets/fix.svg) 修复了发送无关的添加到购物车事件的问题

### 用于页面生成器的magento/module-page-builder-product-recommendations的1.0.3

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新建](../assets/new.svg) Page Builder支持。 通过页面生成器集成，您可以将推荐单元准确并粒度地放置在页面生成器创作内容上的任意位置。 您还可以设置标题和推荐单位本身的样式。 转到 [页面生成器](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) 以了解更多信息。

### 2.0.0的magento/product-recommendations

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新建](../assets/new.svg) 正式发布！

+++

## 文档

要了解有关 [!DNL Product Recommendations] 和 [!DNL Product Recommendations] 开发：

* [用户指南](overview.md)
* [开发人员文档](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/development-overview.html)
