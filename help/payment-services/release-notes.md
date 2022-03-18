---
title: '"[!DNL Payment Services] 发行说明"'
description: 查看发行说明，了解有关 [!DNL Payment Services] 版本。
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
source-git-commit: eb8fdba65b4b64730d0ad4fa6e0c9b64bdadc7df
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 发行说明

以下发行说明介绍了 [!DNL Payment Services] 包括：

![新建](../assets/new.svg) 新增功能
![修复的问题](../assets/fix.svg) 修复和改进功能
![已知问题](../assets/bug.svg) 已知问题

## v1.0.0

![新建](../assets/new.svg)<!-- Issue PAY-2127 --> 正式发布。 [支付服务](https://marketplace.magento.com/magento-payment-services.html) 现在与Adobe Commerce和Magento Open Source版本2.4.0到2.4.3-p1兼容。

![新建](../assets/new.svg)<!-- Issue PAY-124 --> 的 [!DNL Payment Services] Adobe Commerce和Magento Open Source的扩展可以安装 [Adobe Commerce云基础架构](install.md#magento-commerce-cloud) 或 [本地](install.md#on-premises) 实例。 这些方法需要使用命令行接口。

![新建](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] 支持 [沙盒帐户](onboard.md#enable-sandbox-testing) 允许商家在测试模式下评估扩展。

![新建](../assets/new.svg)<!-- Issue PAY-666 --> 商家可以 [配置Payment Services](configure-admin.md) 扩展，具有基本付款行为（例如将身份验证捕获一起，以及在沙盒或生产环境之间切换）。

![新建](../assets/new.svg)<!-- Issue PAY-780 --> 购物者可以 [!DNL Payment Services] 或者你通过电话接下命令 [创建整个订单](create-order.md) 在管理员中。

![新建](../assets/new.svg)<!-- Issue PAY-1856 --> [!DNL Payment Services] 为商户提供全面的报表，以便您能够清楚地了解商店订单和付款情况。

![新建](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] 支持适合任何商户的分层定价（基于TPV）。

![新建](../assets/new.svg)<!-- Issue PAY-1443 --> 可以自定义PayPal按钮的外观以及 [支付服务](https://devdocs.magento.com/payment-services/customize-buttons-messaging.html) 扩展。

![已知问题](../assets/bug.svg)<!-- Issue PAY-2473 --> 使用 [编辑器键值不正确](https://support.magento.com/hc/en-us/articles/4406603542541) 在安装扩展期间，会阻止用户 [身份验证](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) 正确 `MAGEID`.

![已知问题](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] [报告](https://support.magento.com/hc/en-us/articles/4406114741517) 付款和订单付款状态可能无法立即同步。

![已知问题](../assets/bug.svg)<!-- Issue PAY-2475 --> [PayPal沙盒帐户](https://support.magento.com/hc/en-us/articles/4406954952461) 表示 [!DNL Payment Services] 无法验证。
