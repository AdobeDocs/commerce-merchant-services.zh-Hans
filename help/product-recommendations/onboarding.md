---
title: 入门
description: 了解 [!DNL Product Recommendations].
exl-id: ad47ac39-8f6f-4765-84ad-9e3d104385db
source-git-commit: 1bc15171e4e7402d808af3631b8b6d000d4fd3f2
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 入门

的入门流程 [!DNL Product Recommendations] 需要访问服务器的命令行，并包含以下步骤。 如果您不熟悉从命令行工作，请咨询开发人员或系统集成商以寻求帮助。

- [实施工作流程](implementation-workflow.md)
- [安装和配置](install-configure.md)
- [设置](settings.md)
- [验证](verify.md)
- [暂存环境](staging-environment.md)

## 要求

- Adobe Commerce 2.4.4+
- 8.1、8.2菲律宾比索
- 编辑器2

### 支持的平台

- Adobe Commerce本地(EE):2.4.4+
- Adobe Commerce on Cloud(ECE):2.4.4+

### 页面生成器支持

[!DNL Product Recommendations] 可以作为页面生成器内容类型添加到页面。 要将页面生成器支持添加到产品Recommendations，请参阅 [安装和配置](install-configure.md).

请参阅 [[!DNL Page Builder] 集成](page-builder.md) 有关如何添加 [!DNL Product Recommendations] into [!DNL Page Builder] 内容。

## SaaS价格索引

产品推荐客户可以使用 [SaaS价格索引](../price-index/index.md)，可更快地更新价格并同步时间。

### B2B支持 {#b2bsupport}

B2B店面通常需要复杂的逻辑，以指示每个购物者或客户群的产品可见性和定价。 [!DNL Product Recommendations] now [支持](release-notes.md) 此功能通过 [类别权限](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/category-permissions.html), [共享目录](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/catalog-shared.html)和 [客户群特定定价](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html). 例如，如果您在零售客户区段中隐藏了某些类别，则该区段中的购物者将不会显示这些类别中产品的推荐。 此外，在为特定客户组和公司定义共享目录时，这些购物者仅会看到他们可以访问的产品的推荐。 所有推荐产品都会根据每个购物者的客户群组反映正确的客户群组特定价格。
