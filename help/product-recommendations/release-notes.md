---
title: 发行说明
description: 的最新发行信息 [!DNL Product Recommendations] 从Adobe Commerce。
exl-id: 1758e688-d26f-45e7-818c-d4726338a6c3
source-git-commit: bd1cf8a3b4740594cf6b8678d899d771a886cb2e
workflow-type: tm+mt
source-wordcount: '957'
ht-degree: 0%

---

# 发行说明

发行说明包含以下更新 [!DNL Product Recommendations] 模块：

* 自2021年3月起， [!DNL Product Recommendations] 现在支持 [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/) 店面。
* [!DNL Product Recommendations] 元包： `magento/product-recommendations`
* 中的页面生成器支持 [!DNL Product Recommendations] （可选）模块： `magento/module-page-builder-product-recommendations`
* 对的可视相似度推荐类型支持 [!DNL Product Recommendations] （可选）模块： `magento/module-visual-product-recommendations`

发行说明包括：

* ![新建](../assets/new.svg)  — 新增功能
* ![修复](../assets/fix.svg)  — 修复和改进功能

请参阅开发人员文档，以 [了解产品兼容性](https://devdocs.magento.com/release/availability.html).

## Adobe Commerce 2.3.x和2.4.x

### 4.0.0 of magento/product-recommendations

* ![新建](../assets/new.svg)  — 已添加 [就绪指标](create.md) 以帮助您可视化每个推荐类型的培训进度。
* ![新建](../assets/new.svg)  — 这是一个主要版本。 您必须 [编辑](install-configure.md#update) 根 `composer.json` 文件。 此版本还要求您在安装和配置产品Recommendations时提供两个API密钥： [生产密钥和沙盒密钥](../landing/saas.md).

### 已知限制

* 的 `websiteCode` 如果值包含下划线(_)，则会错误返回该值。

### magento/product-recommendations的3.3.7

* ![新建](../assets/new.svg)  — 添加了PHP 8.1支持
* ![新建](../assets/new.svg)  — 改进了图像大小调整，以便在参考显示模板中处理不同大小的图像时更一致

### magento/product-recommendations的3.3.6

* ![新建](../assets/new.svg)  — 已优化 [!DNL Product Recommendations] 元包，方法是明确列出依赖项

### magento/product-recommendations的3.3.5

* ![新建](../assets/new.svg)  — 已添加 [B2B支持](onboarding.md#b2bsupport) 在产品中Recommendations
* ![新建](../assets/new.svg)  — 向 [同步目录数据](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-catalog-sync.html) 到Commerce Services

### magento/product-recommendations的3.3.3

* ![新建](../assets/new.svg)  — 新增 [推荐类型](type.md):转化（查看到购物车）、转化（查看到购买）和最近查看。 在 `magento/product-recommendations` 模块3.2.2及更高版本。
* ![修复](../assets/fix.svg)  — 修复了Fastly的Web应用程序防火墙(WAF)错误地阻止Cookie的问题
* ![修复](../assets/fix.svg)  — 修复了分配给非默认商店视图的产品未在 _Recommendations产品预览_ 面板
* ![修复](../assets/fix.svg)  — 修复了页面生成器中的某些推荐单元名称阻止推荐单元在店面上显示的问题

### magento/product-recommendations的3.3.2

* ![修复](../assets/fix.svg)  — 修复了B2B支持缺失的依赖项

### magento/product-recommendations的3.3.1

* ![新建](../assets/new.svg)  — 增加了对B2B客户群定价的支持。 当您设置 [价格筛选](filters.md) 在推荐单元上，已登录的B2B客户将看到所显示产品的客户组定价集。

### magento/product-recommendations的3.3.0

* ![新建](../assets/new.svg)  — 增加了对Adobe客户端数据层的支持，以标准化跨Adobe Commerce功能和服务的行为数据收集。 请参阅 [readme](https://github.com/adobe/magento-storefront-event-collector/blob/main/README.md) 以了解更多。

### magento/product-recommendations的3.2.6

* ![修复](../assets/fix.svg)  — 修复了JavaScript模式错误
* ![修复](../assets/fix.svg)  — 修复了Fastly的Web应用程序防火墙(WAF)错误地阻止Cookie的问题

### magento/product-recommendations的3.2.5

* ![新建](../assets/new.svg)  — 将Magento服务重命名为 [商务服务](https://docs.magento.com/user-guide/system/saas.html) 并提高了管理员的可用性

### magento/product-recommendations的3.2.4

* ![修复](../assets/fix.svg)  — 修复了在索引产品属性时出现的“无法检索可配置产品选项数据”错误

### magento/product-recommendations的3.2.3

* ![修复](../assets/fix.svg)  — 修复了目录同步期间出现的“无法检索可配置产品选项数据”错误
* ![修复](../assets/fix.svg)  — 修复了在启用“将存储代码添加到URL”配置时，存储代码设置不正确的问题
* ![修复](../assets/fix.svg)  — 改进了对管理面板配置更改的检测，以确保这些更改反映在目录同步数据中

### magento/product-recommendations的3.2.2

* ![新建](../assets/new.svg)  — 添加了 [预览推荐结果](create.md) 创建时。 这可能需要您将模块更新到最新版本。
* ![新建](../assets/new.svg)  — 添加了 [监控和管理](https://docs.magento.com/user-guide/system/catalog-sync.html) 管理员的目录同步过程。
* ![新建](../assets/new.svg)  — 已添加 [过滤器](filters.md) 以控制在推荐中显示的产品。
* ![新建](../assets/new.svg)  — 添加了 [视觉相似度](type.md#visualsim) 推荐类型。

### 页面生成器的magento/module-page-builder-product-recommendations的1.2.1

* ![新建](../assets/new.svg)  — 添加了对3.2.0及更高版本的 `magento/product-recommendations` 模块

### magento/product-recommendations的3.1.0

* ![新建](../assets/new.svg)  — 添加了 [重新同步](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-catalog-sync.html) 通过命令行将目录添加到SaaS服务。
* ![新建](../assets/new.svg)  — 添加了对数据库表前缀的支持
* ![修复](../assets/fix.svg)  — 删除了PHP 7.1支持

### magento/product-recommendations的3.0.8

* ![修复](../assets/fix.svg)  — 修复了在配置模块之前为数据收集发送事件，导致流量无效的问题

### magento/product-recommendations的3.0.6

* ![新建](../assets/new.svg) - **（测试版）** 包括对新 [视觉相似度](type.md#visualsim) 推荐类型。

### 1.0.0 magento/module-visual-product-recommendations

* ![新建](../assets/new.svg) - **（测试版）** [视觉相似度](type.md#visualsim). 使用 _视觉相似度_ 推荐类型中，您可以将推荐单元部署到产品详细信息页面，该页面显示与所查看产品视觉上相似的产品。

### magento/product-recommendations的3.0.5

* ![修复](../assets/fix.svg)  — 修复了在目录导出过程中可能发生的“无法检索产品选项数据”错误。
* ![修复](../assets/fix.svg)  — 货币符号(位于 _收入_ 列 _产品Recommendations_ 功能板现在可正确反映已配置的基本货币。

### magento/product-recommendations的3.0.4

* ![修复](../assets/fix.svg)  — 添加了对Adobe Commerce 2.4.0的支持

### magento/product-recommendations的3.0.3

* ![修复](../assets/fix.svg)  — 改进了店面模板中的符号实施

### 页面生成器的magento/module-page-builder-product-recommendations的1.0.4

* ![新建](../assets/new.svg)  — 在编辑页面生成器内容类型时添加了产品推荐名称

### 3.0.2 magento/product-recommendations

* ![新建](../assets/new.svg)  — 在页面生成器中选择推荐单位时，在网格上添加了状态列
* ![修复](../assets/fix.svg)  — 修复了产品和图像URL中的http/https协议不正确的问题

### magento/product-recommendations的3.0.1

这是一个主要版本。 您必须 [编辑](install-configure.md#update) 您项目的根composer.json文件。

* ![新建](../assets/new.svg)  — 获取 [!DNL Product Recommendations] 从备用SaaS数据空间。 这允许您在其他非生产环境中使用在产品环境中计算的产品推荐。 [切换SaaS数据空间](settings.md) 对此功能的进一步描述。

* ![修复](../assets/fix.svg)  — 修复了使用uBlock Origin的购物者禁止结帐的问题
* ![修复](../assets/fix.svg)  — 修复了发送无关的添加到购物车事件的问题

### 页面生成器的magento/module-page-builder-product-recommendations的1.0.3

* ![新建](../assets/new.svg)  — 页面生成器支持。 通过页面生成器集成，您可以准确、细致地将推荐单元放置在页面生成器创作内容的任意位置。 您还可以设置标题和推荐单元本身的样式。 转到 [页面生成器](https://docs.magento.com/user-guide/cms/page-builder-add-recommendations.html) 以了解更多信息。

### magento/product-recommendations的2.0.0

* ![新建](../assets/new.svg)  — 正式发布！

## 文档

详细了解 [!DNL Product Recommendations] 和 [!DNL Product Recommendations] 开发：

* [用户指南](overview.md)
* [开发人员文档](https://devdocs.magento.com/recommendations/product-recs.html)
