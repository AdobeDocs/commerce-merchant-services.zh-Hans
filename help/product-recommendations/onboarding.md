---
title: 入门
description: 了解中的要求和支持平台 [!DNL Product Recommendations].
exl-id: ad47ac39-8f6f-4765-84ad-9e3d104385db
source-git-commit: 209bdf9c69ff81481d6df7cb8e8832deef13c9f4
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# 入门

的新用户引导流程 [!DNL Product Recommendations] 需要访问服务器的命令行并包含以下步骤。 如果您不熟悉如何使用命令行，请向开发人员或系统集成商寻求帮助。

- [实施工作流](implementation-workflow.md)
- [安装和配置](install-configure.md)
- [设置](settings.md)
- [验证](verify.md)
- [暂存环境](staging-environment.md)

## 要求

- Adobe Commerce 2.4.4+
- PHP 8.1、8.2
- 作曲者2

### 支持的平台

- Adobe Commerce内部部署(EE)：2.4.4+
- Adobe Commerce on Cloud (ECE) ：2.4.4+

### Page Builder支持

[!DNL Product Recommendations] 可以作为页面生成器内容类型添加到页面。 要将页面生成器支持添加到产品Recommendations，请参阅 [安装和配置](install-configure.md).

请参阅 [[!DNL Page Builder] 集成](page-builder.md) 有关如何添加的说明 [!DNL Product Recommendations] 到 [!DNL Page Builder] 内容。

### SaaS价格索引

客户可以使用产品推荐 [SaaS价格索引](../price-index/index.md)，这可以加快价格变更更新和同步时间。

### B2B支持 {#b2bsupport}

B2B店面通常需要复杂的逻辑，这些逻辑指示每个购物者或客户组的产品可见性和定价。 [!DNL Product Recommendations] 现在 [支持](release-notes.md) 此功能的实现方式： [类别权限](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/category-permissions.html)， [共享目录](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/catalog-shared.html)、和 [客户组特定的定价](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html). 例如，如果您在零售客户区段中隐藏了某些类别，则该区段中的购物者不会显示这些类别中的产品推荐。 此外，在为特定客户组和公司定义共享目录时，这些购物者只会看到他们能够访问的产品推荐。 所有推荐产品均反映根据每位购物者的客户组确定的正确客户组特定价格。

>[!NOTE]
>
>商家可使用以下工具自定义和扩展小部件或店面元素 [目录服务](../catalog-service/overview.md) Storefront API，但任何自定义都不在Adobe支持团队的覆盖范围内。
