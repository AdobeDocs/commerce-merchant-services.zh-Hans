---
title: 派息报告
description: 使用“支付”报表可以完全透明地记录支付金额、已处理数量以及财务对账的交易级别详细报告。
role: User
level: Intermediate
exl-id: f3f99474-cd28-4c8f-b0ea-dca8e014b108
source-git-commit: 4fc2b3bdf9f319337939905bca2b9525985702d4
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 0%

---

# 派息报告

[!DNL Payment Services] 表示 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 提供全面的报表，以便您能够清楚地了解商店的订单和付款情况。

![财务报表视图](assets/reports-view.png)

“付款”报表一目了然地显示全面的付款信息，使您对付款金额、已处理数量和财务对账交易级别的详细报告完全透明。

您不必打开多个视图来交叉引用订单和付款或调节帐户。 [!DNL Payment Services] 表示 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 使您能够从一个位置执行所有这些操作，即支付报告，以便您能够高效查看和管理您的支付。

请参阅管理员的“支付”报表中关联的商务订单和交易ID、交易金额、每笔交易的付款方法等。

您可以下载.csv文件格式的支付交易记录，以用于现有会计或订单管理软件。

>[!NOTE]
>
>此表中显示的数据按降序排序(`DESC`) `TRANS DATE`. 的 `TRANS DATE` 是事务处理的启动日期和时间。

## 可用性

在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.

![管理员中的支付交易](assets/payouts-report.png)

## 选择数据源

在“支付”报表视图中，您可以选择数据源 — _[!UICONTROL Live]_或 [!UICONTROL Sandbox]_ — 您希望查看其报告结果。

![数据源选择](assets/datasource.png)

如果 _[!UICONTROL Live]_是选定的数据源，则可以查看实时商店的报表信息。 如果 [!UICONTROL Sandbox]_是选定的数据源，您可以看到沙盒环境的报表信息。

数据源选择的工作方式如下：

* 如果您没有处于实时模式的任何存储，则数据源选择将默认为 _[!UICONTROL Sandbox]_.
* 如果您在实时模式下有任何存储（一个或多个），则数据源选择将默认为 _[!UICONTROL Live]_.
* 报表导出始终遵循数据源选择。

要为订单付款状态报表选择数据源，请执行以下操作：

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. 单击 **[!UICONTROL Data source]** 选择 _[!UICONTROL Live]_或 [!UICONTROL Sandbox]_.

   报表结果会根据所选的数据源重新生成。

## 查看交易记录

默认情况下，网格中会显示30天的交易。

在搜索中返回或在默认的30天交易记录中显示的行数显示在“支付”视图网格上方，并与“交易日期日历选择器”筛选器一起显示。

向左和向右滚动以查看 [每个支付交易的信息](#column-descriptions) 日报表中，包括交易日期、参考ID、发票编号和付款方法详细信息。

### 自定义交易时间范围

在“付款”视图中，您可以通过输入特定日期或从日期选取器中选择日期范围，自定义要查看的付款交易记录的时间范围：

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. 单击交易日期日历选择器过滤器。
1. 选择适用的日期范围。
1. 在网格中查看指定日期的付款状态。

## 显示和隐藏列

默认情况下，“派款”报表显示大多数可用的信息列。 但是，您可以自定义在报表中看到的列。

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Payouts]**.
1. 单击 _列设置_ 图标(![列设置图标](assets/column-settings.png))。
1. 要自定义在报表中看到的列，请勾选或取消选中列表中的列。

   “付款”报表将立即显示您在“列”设置菜单中所做的任何更改。 列首选项将会保存，并且在您离开报表视图时保持有效。

## 下载交易记录

您可以下载一个.csv文件，其中包含“付款”视图网格中显示的所有交易记录。

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. [自定义交易的日期范围时间范围](#customize-transactions-timeframe).
1. 单击 _下载_ (![](assets/icon-download.png))图标。

付款交易记录以.csv格式下载。

## 交易信息

“支付”视图显示网格中显示的每项交易的详细信息。

### 列描述

付款报告包括以下信息。

| 列 | 描述 |
| ------------ | -------------------- |
| [!UICONTROL Provider] | 支付提供商 |
| [!UICONTROL Provider trans] | 交易ID |
| [!UICONTROL Trans date] | 事务处理的启动日期和时间 |
| [!UICONTROL Type] | 交易类型 — *[!UICONTROL PAYMENT]*, *[!UICONTROL AUTH]*, *[!UICONTROL BONUS]*, *[!UICONTROL CHARGEBACK]*, *[!UICONTROL CORRECTION]*, *[!UICONTROL CURRENCY_CONVERSATION]*, *[!UICONTROL DEPOSIT]*, *[!UICONTROL DISBURSEMENT]*, *[!UICONTROL DISPUTE]*, *[!UICONTROL FEES]*, *[!UICONTROL HOLD]*, *[!UICONTROL HOLD_RELEASE]*, *[!UICONTROL INCENTIVES]*, *[!UICONTROL OTHERS]*, *[!UICONTROL RECOUP]*, *[!UICONTROL REFUND]*, *[!UICONTROL REVERSAL]*, *[!UICONTROL WITHDRAWAL]* <br> <br>请参阅 [交易类型](#transaction-types) 以了解更多信息。 |
| [!UICONTROL Status] | 交易的当前状态 — *[!UICONTROL SUCCESS]*, *[!UICONTROL DENIED]*, *[!UICONTROL PENDING]* |
| [!UICONTROL Code] | 表示信用(*CR*)或借项(*DR*) |
| [!UICONTROL Reference ID] | 与此事件相关的原始交易ID |
| [!UICONTROL Invoice] | 交易的发票ID（每张订单一张） |
| [!UICONTROL Commerce order] | 商务订单ID <br> <br>查看相关 [订购信息](https://docs.magento.com/user-guide/sales/orders.html){target=&quot;_blank&quot;}，单击ID。 |
| [!UICONTROL Commerce trans] | 商务交易ID <br> <br>查看相关 [交易信息](https://docs.magento.com/user-guide/sales/transactions.html){target=&quot;_blank&quot;}，单击ID。 |
| [!UICONTROL Pay method] | 信用卡类型 — *[!UICONTROL BANK]*, *[!UICONTROL PAYPAL]*, *[!UICONTROL CREDIT_CARD]* — 和关联的卡提供商(例如 *签证* 或 *万事达*) |
| [!UICONTROL Trans amt] | 交易金额 |
| [!UICONTROL Cur] | 交易金额的货币单位 |
| [!UICONTROL Pending] | 尚未支付的金额 |
| [!UICONTROL Cur] | 待定金额的货币单位 |
| [!UICONTROL Seller amt] | 转入或转出客户的资金数额 <br> <br>从卖方帐户移出的基金显示短划线(-)前缀。 |
| [!UICONTROL Cur] | 卖方金额的货币单位 |
| [!UICONTROL Partner fee] | 与交易相关的合作伙伴费用 <br> <br>从合作伙伴费用帐户移出的基金会显示短划线(-)前缀。 |
| [!UICONTROL Cur] | 合作伙伴费用的货币单位 |
| [!UICONTROL Prov fees] | 与交易相关的费用 <br> <br>从提供商的费用帐户移出的资金显示短划线(-)前缀。 |
| [!UICONTROL Cur] | 提供商费用的货币单位 |
| [!UICONTROL Fee %] | 作为费用收取的交易金额的百分比 |
| [!UICONTROL Fixed fee] | 固定的提供商费用金额 |
| [!UICONTROL Chbk fee] | 与交易关联的拖欠款项费用 <br> <br>短划线(-)前缀表示拖欠费用已冲销。 |
| [!UICONTROL Cur] | 按存储容量使用计费费用的货币单位 |
| [!UICONTROL Hold amt] | 搁置或解除保留的金额 <br> <br>短划线(-)前缀表示暂挂基金正在发放。 |
| [!UICONTROL Cur] | 暂挂金额的货币单位 |
| [!UICONTROL Recoup amt] | 从收回帐户扣除的金额 <br> <br>从收回帐户中移出的资金显示短划线(-)前缀。 |
| [!UICONTROL Cur] | 收回金额的货币单位 |

### 交易类型

在支付交易中可以记录这些交易类型。

| 报表 | 描述 |
| ------------ | -------------------- |
| [!UICONTROL PAYMENT] | 为订单在买方和卖方之间转移的货币 |
| [!UICONTROL AUTH] | 授权和授权撤消交易 |
| [!UICONTROL BONUS] | — |
| [!UICONTROL CHARGEBACK] | 按存储容量使用计费和按存储容量使用计费费用冲销交易 |
| [!UICONTROL CORRECTION] | — |
| [!UICONTROL CURRENCY_CONVERSION] | — |
| [!UICONTROL DEPOSIT] | — |
| [!UICONTROL DISBURSEMENT] | — |
| [!UICONTROL DISPUTE] | — |
| [!UICONTROL FEES] | 合作伙伴费用、支付费用和费用转回交易 |
| [!UICONTROL HOLD] | — |
| [!UICONTROL HOLD_RELEASE] | — |
| [!UICONTROL INCENTIVES] | — |
| [!UICONTROL OTHERS] | — |
| [!UICONTROL RECOUP] | 从银行或亏损帐户中扣除 |
| [!UICONTROL REFUND] | — |
| [!UICONTROL REVERSAL] | — |
| [!UICONTROL WITHDRAWAL] | — |
