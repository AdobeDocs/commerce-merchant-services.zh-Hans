---
title: 应用程序设置
description: '“设置 [!DNL Store Assist] 应用程序管理端到端商店的在线购买履行工作流程和流程，可以按商店订单提货。” '
role: User, Admin
level: Intermediate
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# 应用程序设置

Store Assist是由Walmart Commerce Technologies提供支持的“按实施即服务”(FaaS)平台应用程序。 该应用程序提供商店内实施功能来处理 [!DNL buy online], [!DNL pick up in store] （桶装）订单。

该应用程序接收所有订单和客户信息（从订单详细信息到提取时间），并通过移动设备将相关数据在线存储。 借助“商店辅助”，商店关联人员可以查看客户订购了哪些项目，更快地挑选正确的项目，并为店内或店内提货客户设置已履行订单。

Store Associates使用Store Assist [!UICONTROL Pick], [!UICONTROL Stage], [!UICONTROL Handoff]和 [!UICONTROL Orders] 要完成以下管理投放和切换流程：

- 分配订单交货日期和时间
- 客户到达商店时收到订单提货通知
- 为客户切换提交订单
- 跟踪其分配的商店位置中所有订单的订单状态

请参阅 [存储协助履行工作流](store-assist-modules.md) 了解有关Store Assist应用程序的更多信息。


## 配置Store Assist应用程序

Store Assist应用程序需要两种类型的配置：

- Adobe Commerce管理员配置设置 [从Adobe Commerce管理系统设置管理用户帐户、用户角色和资源权限](user-setup.md).

- 用于自定义商店辅助应用程序界面的前端配置设置和其他设置，包括：

   - **为Store Assist应用程序添加品牌** — 使用公司徽标和颜色自定义应用程序用户界面

   - **更新默认说明** — 自定义在“商店辅助”界面中为“挑选”、“暂存”、“切换”和“订单”模块显示的说明，以便您的关联人员确切了解在完成过程的每个步骤中要执行的操作。

   - **本地化** — 选择应用程序的可用语言，选择日期和时间格式，选择默认测量单位，选择默认货币

   - **非活动时间** — 指定应用程序在注销之前必须处于非活动状态的时间

   - **从商店取消** — 指定是否可以从商店取消订单以及哪些角色具有取消权限

   - **订单清理窗口** — 指定在重新库存之前，挑库单在计划装货时间之前在暂存状态中停留的时间（例如三天）。

   - 自定义所有应用程序说明（挑选、暂存、分手）

   - **领料通知** — 如果希望在下订单后开始领料推送通知，请设置

   - **签入通知** — 如果希望在客户签入/正在等待X分钟/或根本没有通知后收到推送通知，请设置

   - **切换过程** — 启用客户签名，在交付订单前启用检查客户ID的提示

   - **在切换时启用项目拒绝**

   与沃尔玛商务技术客户服务团队合作，为商店辅助应用程序完成前端配置。

## 应用程序下载和安装

完成Store Assist应用程序配置后，Store Associates可以在其移动设备上下载并安装Store Assist应用程序并登录。

- 从下载Store Assist应用程序 [AppleApp Store](https://apps.apple.com/us/app/store-assist-by-walmart/id16092815390) 或者Google Play店。

- Store Associates需要以下信息才能登录：

   - 与您的商店辅助帐户关联的公司名称

   - 存储Assist帐户凭据 — 其帐户的用户名和密码凭据。
   Adobe Commerce管理员可以为具有 [店内取货](merchant-store-configuration.md#pickup-location-configuration) 在“管理员存储”设置中启用。

