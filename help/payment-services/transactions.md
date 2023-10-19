---
title: 事务报表
description: 使用事务报表可以查看事务授权率和事务趋势。
role: User
level: Intermediate
exl-id: dd1d80f9-5983-4181-91aa-971522eb56fa
source-git-commit: 91acc6e1dfd142caca77c0dc9ba55da34f75dd60
workflow-type: tm+mt
source-wordcount: '1274'
ht-degree: 0%

---

# 事务报表

[!DNL Payment Services] 对象 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 提供全面的报表，以便您清楚地了解商店的交易、订单和付款。

![交易报表](assets/transactions-report.png){width="700" zoomable="yes"}

“交易”报表提供了交易授权率和负交易趋势的可见性，因此您可以有效地监控存储设备的运行状况，并提前发现和处理任何交易问题。

有关在店面下单的订单及其付款方式、结果、付款回应代码等，请参阅单个交易记录。

交易报告中提供的信息仅供商家使用。 请勿与客户或其他潜在欺诈者共享此信息。 交易信息可用于绕过安全检查或下单导致拖缺款项。

您可以下载.csv文件格式的“交易”报表，以便在现有的会计或订单管理软件中使用。

>[!NOTE]
>
>如果没有，则无法查看财务报表 [已载入和激活的实时模式](production.md#enable-live-payments) 对象 [!DNL Payment Services].

## 交易报表视图

“事务处理”报表视图在“付款服务”的“事务处理”视图中可用。 它包括有关您商店交易的所有可用信息。

在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**查看详细的表格“事务处理”报告视图。

![交易报表视图](assets/transactions-report-detail.png){width="600" zoomable="yes"}

您可以根据本主题中的部分对此视图进行配置，以便最好地呈现您希望查看的数据。

请参阅链接的商务订单和提供商交易ID、交易金额、每笔交易的支付方式等，所有这些都包含在此报表中。

并非所有支付方式都提供相同的信息粒度。 例如，信用卡交易提供响应、AVS和CCV代码，以及“交易”报表中卡的最后四位数字；而PayPal智能按钮不提供。

您可以 [下载事务](#download-transactions) CSV文件格式，用于现有会计或订单管理软件。

### 选择数据源

在交易报表视图中，您可以选择数据源 — **[!UICONTROL Live]** 或 **[!UICONTROL Sandbox]** — 要查看其报告结果。

![数据源选择](assets/datasource.png){width="300" zoomable="yes"}

如果 _[!UICONTROL Live]_是选定的数据源，则可以查看使用的商店的报表信息 [!DNL Payment Services] 在生产模式下。 如果_[!UICONTROL Sandbox]_ 是选定的数据源，您可以看到沙盒模式的报表信息。

数据源选择的工作方式如下所示：

* 如果您没有任何使用 [!DNL Payment Services] 在生产模式下，数据源选择默认为 _[!UICONTROL Sandbox]_.
* 如果您有任何商店（一个或多个）使用 [!DNL Payment Services] 在生产模式下，数据源选择默认为 _[!UICONTROL Live]_.
* 报表导出始终遵循数据源选择。

要为选择数据源，请执行以下操作 [!UICONTROL Transactions] 报告：

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**.
1. 单击 **[!UICONTROL Data source]** 并选择 **[!UICONTROL Live]** 或 **[!UICONTROL Sandbox]**.

   报表结果会根据所选数据源重新生成。

### 自定义日期时间范围

从“事务处理”报表视图中，通过选择特定日期可以自定义要查看的事务处理的时间范围。 默认情况下，网格中显示30天的事务处理。

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**.
1. 单击 **[!UICONTROL Transaction dates]** 日历选择器过滤器。
1. 选择适用的日期范围。
1. 在网格中查看指定日期的事务。

### 筛选报表信息

从“事务”报表视图中，您可以通过选择筛选条件来筛选要查看的状态结果。

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**.
1. 单击 **[!UICONTROL Filter]** 选择器。
1. 切换 _[!UICONTROL Transaction Result]_选项，用于查看仅选定订单交易记录的报表结果。
1. 选择 _[!UICONTROL Card Type]_以查看所选信息卡类型的报告结果。 当付款处理器无法识别卡类型时，将显示包含更多信息的工具提示。
1. 选择 _[!UICONTROL Card Brand]_用于查看选定卡片品牌的报告结果。 当支付处理器无法识别卡品牌时，将显示包含更多信息的工具提示。
1. 切换 _[!UICONTROL Payment Method]_选项，用于仅查看选定付款方法的报表结果。
1. 输入 _最小订单金额_ 或 _最大订单金额_ 以便在该订单金额范围内查看报表结果。
1. 输入 _[!UICONTROL Order ID]_搜索特定事务处理。
1. 输入 _[!UICONTROL Card Last Four Digits]_以搜索特定的信用卡或借记卡。
1. 单击 **[!UICONTROL Hide filters]** 以隐藏筛选器。

### 显示和隐藏列

默认情况下，“事务处理”报表会显示所有可用的信息列。 但是，您可以自定义您在报表中看到的列。

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**.
1. 单击 **[!UICONTROL Column settings]** 图标 ![列设置图标](assets/column-settings.png){width="20" zoomable="yes"}.
1. 要自定义您在报表中看到的列，请选中或取消选中列表中的列。

   事务报表会立即显示您在“列设置”菜单中所做的任何更改。 列首选项已保存，如果您离开报表视图，这些首选项将保持有效。

### 更新报表数据

“事务处理”报表视图显示 _[!UICONTROL Last updated]_显示上次更新报告信息的时间戳。 默认情况下，事务报表数据每三小时自动刷新一次。

您还可以手动强制刷新报表数据以查看最新的报表信息。

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**.
1. 单击 _刷新_ 图标(![刷新图标](assets/refresh-button-med.png){width="20" zoomable="yes"})。

   事务报表数据会进行刷新，并且 *[!UICONTROL Update complete]* 确认即会出现，网格中会显示最新信息。

### 下载交易记录

您可以下载一个.csv文件，其中包含事务视图网格中显示的所有事务，无论您查看的是默认的30天事务还是自定义的时间范围。

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Transactions]**.
1. 如果您希望查看过去30天以外的其他时间范围内的事务， [自定义状态的日期范围时间范围](#customize-dates-timeframe).
1. 单击 _下载_ ![下载图标](assets/icon-download.png){width="20" zoomable="yes"} 图标。

您的交易将以.csv格式下载。

### 列描述

事务报表包含以下信息。

| 列 | 描述 |
| ------------ | -------------------- |
| [!UICONTROL Order ID] | 商业订单ID（仅包含成功交易的值，对于拒绝的交易为空）<br> <br>查看相关内容 [订单信息](https://docs.magento.com/user-guide/sales/orders.html){target="_blank"}中，单击ID。 |
| [!UICONTROL Provider Transaction ID] | 由付款提供商提供的交易ID；仅包含成功交易的值，并包含拒绝交易的短划线。 |
| [!UICONTROL Transaction Date] | 交易日期时间戳 |
| [!UICONTROL Payment Method] | 具有品牌和卡类型详细信息的交易的支付方法。 请参阅 [信息卡类型](https://developer.paypal.com/docs/api/orders/v2/#definition-card_type) 有关更多信息；适用于Payment Services 1.6.0及更高版本 |
| [!UICONTROL Card Last Four Digits] | 用于交易记录的信用卡或借记卡的最后四位数字 |
| [!UICONTROL Result] | 交易的结果 — *[!UICONTROL OK]* （成功交易）， *[!UICONTROL Rejected by Payment Provider]* （被PayPal拒绝）， *[!UICONTROL Rejected by Bank]* （被发卡银行拒绝） |
| [!UICONTROL Response Code] | 提供来自付款提供商或银行的拒绝原因的错误代码；请参阅可能的响应代码列表和描述 [`Rejected by Bank` 状态](https://developer.paypal.com/docs/api/orders/v2/#definition-processor_response) 和 [`Rejected by Payment Provider` 状态](https://developer.paypal.com/api/rest/reference/orders/v2/errors/). |
| [!UICONTROL AVS Code] | 地址验证服务代码；付款请求的处理器响应信息。 请参阅 [可能的代码列表和描述](https://developer.paypal.com/docs/api/orders/v2/#definition-processor_response) 以了解更多信息。 |
| [!UICONTROL CVV Code] | 信用卡和借记卡的卡验证值代码；请参阅 [可能的代码列表和描述](https://developer.paypal.com/docs/api/orders/v2/#definition-processor_response) 以了解更多信息。 |
| [!UICONTROL Amount] | 交易记录的订单金额 |
| [!UICONTROL Currency] | 交易记录中用于订单的货币 |
| [!UICONTROL Type] | [付款操作](../payment-services/production.md#set-payment-services-as-payment-method) 交易 — `Authorize` 或 `Authorize and Capture` |

### 错误响应代码

此 _响应代码_ 列显示与事务处理相关的特定错误或成功代码。 您可能会看到的一些常见错误代码包括：

* `PAYMENT_DENIED` — 交易被贝宝拒绝，因为它涉嫌欺诈。
* `INTERNAL_SERVER_ERROR` — 交易被PayPal拒绝，并发生PayPal服务器错误。 可以重试事务。
* `INSTRUMENT_DECLINED`—PayPal根据所选的支付方式拒绝了客户。 可以使用其他支付方式重试交易。
* `9500` — 由于涉嫌欺诈，关联银行拒绝了该交易。
* `5120` — 关联银行拒绝了交易，因为客户没有足够的资金用于付款。
* `5650` — 关联银行拒绝了交易，因为该银行要求强大的客户身份验证([3DS](security.md#3ds))。

失败交易的详细错误响应代码可用于2023年6月1日以后的交易。 对于2023年6月1日之前发生的交易，将显示部分报表数据。
