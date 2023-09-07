---
title: '[!DNL Store Fulfillment by Walmart Commerce Technologies] 发行说明'
description: “查看发行说明，了解所有 [!DNL Store Fulfillment by Walmart Commerce Technologies] 版本发布。”
role: Admin, User, Leader
feature: Shipping/Delivery, Release Notes
exl-id: 04dcec10-fff8-483d-a2c1-4b58e063e0f0
source-git-commit: db1d5523f48f5686c2a28c7dfb7b1175238b37cf
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 1%

---

# 发行说明

以下发行说明介绍了的初始版本 [!DNL Store Fulfillment Services by Walmart Commerce Technologies] 并包括：

![新建](../assets/new.svg) 新增功能
![修复的问题](../assets/fix.svg) 修复和改进功能
![已知问题](../assets/bug.svg) 已知问题

请参阅 [即将发布的版本](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/schedule.html) 了解发布计划和支持。

请参阅 [产品可用性](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html) 以了解哪些Adobe Commerce版本支持此扩展。

## v1.5.0

*2023年8月3日*

[!BADGE 支持]{type=Informative tooltip="支持"}[Adobe Commerce 2.4.4到2.4.6](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html)，包括2.4.6-p1、2.4.5-p3和2.4.4-p4安全修补程序版本

此版本包含以下更新：

![新建](../assets/fix.svg) 更新了扩展以支持 [Adobe Commerce安全修补程序版本](https://experienceleague.adobe.com/docs/commerce-operations/release/notes/security-patches/overview.html) 2.4.6-p1、2.4.5-p3和2.4.4-p4。

![新建](../assets/new.svg)<!-- WMTP-918 --> 添加了对 [异步发送](sales-emails.md) 销售电子邮件的配置选项。 升级到版本1.5.0的商家可以选择立即发送电子邮件（默认）或异步发送。

![新建](../assets/new.svg)<!-- WMTP-916--> 已更新 [源配置](merchant-store-configuration.md) 支持国际电话号码格式。

![新建](../assets/new.svg) 添加了逻辑，以防止退款金额超过剩余金额或开票金额。

![新建](../assets/new.svg)<!-- WMTP-882 --> 已替换 `google.map.LatLng` 对象的JSON文本，用于支持与旧版本的 [!DNL Google Maps].

![修复的问题](../assets/fix.svg)<!-- WMTP- --> 更新了用于创建 `[!DNL Available for Store Pickup]` 和 `[!DNL Available for Home Delivery]` 产品属性，以防止属性类别冲突。

![修复的问题](../assets/fix.svg)<!-- WMTP-915 --> 修复了在加载和保存某些实体时导致无休止循环的兼容性问题。

![修复的问题](../assets/fix.svg)<!-- WMTP-921 --> 修复了导致无法正常工作的问题 [!DNL Ship to Store] 将项目从产品详细信息页面(PDP)添加到购物车时触发的报价验证。

![修复的问题](../assets/fix.svg)<!-- WMTP- 932 --> 修复了一个结账问题，该问题允许客户为不符合主页交付条件的项目选择主页交付方法。

![修复的问题](../assets/fix.svg) 安装更新：

- <!-- WMTP-880--> 修复了在安装时导致返回错误网站代码的问题 [!DNL Store Fulfillment] 扩展。

- <!-- WMTP-878--> 修复了SKU整数的一个问题，该问题要求在安装期间将数据类型转换为字符串类型。

![修复的问题](../assets/fix.svg)<!-- WMTP-915--> 修复了因缺少签入错误代码导致的故障。

![修复的问题](../assets/fix.svg)<!-- WMTP-932 --> 修复了与分配操作期间部分拒绝相关的错误。

![新建](../assets/new.svg)<!-- WMTP-953 --> 更新了Cancel API端点，以将status参数用作可选对象。

![新建](../assets/new.svg)<!-- WMTP-960 --> 改进了Dispense API端点的日志记录详细信息。

## v1.4.0

*2023年4月13日*

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/fix.svg) [!DNL Store Fulfillment] 为现在 [兼容 [!DNL Adobe Commerce] 2.4.4至2.4.6](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).


## v1.3.0

*2023年2月27日*

[!BADGE 支持]{type=Informative tooltip="支持"}

此版本包含以下更新：

![新建](../assets/fix.svg)<!-- WMTP-795 --> 添加了通过将系统配置设置的默认范围从网站更改为全局来禁用特定站点的商店履行解决方案的功能。

## v1.2.0

*2022年9月27日*

[!BADGE 支持]{type=Informative tooltip="支持"}

此版本包含以下更新：

![新建](../assets/fix.svg) [!DNL Store Fulfillment] 为现在 [兼容 [!DNL Adobe Commerce] 2.4.4至2.4.5](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).


## v1.1.0

*2022年7月15日*

[!BADGE 支持]{type=Informative tooltip="支持"}

稳定性：正式发布

![新建](../assets/fix.svg)<!-- WMTP-731 --> 简化了 [签入体验配置](check-in-experience-setup.md) 添加默认汽车造型和模型选择，获得商店助手应用程序。 在以前的版本中，商家必须手动配置汽车厂牌和车型选择。

## v1.0.0

*2022年3月4日*

[!BADGE 支持]{type=Informative tooltip="支持"}

稳定性：正式发布

## 商店协助应用程序

有关Store Assist应用程序新版本的信息，请参阅 [Apple App Store](https://apps.apple.com/us/app/store-assist-by-walmart/id1609281539){target="_blank"} or [Google Play store](https://play.google.com/store/apps/details?id=com.walmart.faas.storeassist){target="_blank"}.
