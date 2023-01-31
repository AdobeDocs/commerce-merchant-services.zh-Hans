---
title: 常规配置
description: 配置常规设置以启用 [!DNL Store Fulfillment] 你的店。 配置全局扩展设置、用于日志记录的系统设置、数据同步和安全性。 提供关键数据以启用Adobe Commerce与商店履行服务之间的集成。
role: User, Admin
level: Intermediate
exl-id: 51dcfc95-3dd6-40d9-bd26-d8409a25f3c8
source-git-commit: c68bf177f79c37cc57b4cc5979b18e1fd4a7e17d
workflow-type: tm+mt
source-wordcount: '2541'
ht-degree: 0%

---

# 商店服务和销售配置

配置 [!DNL Store Fulfillment] 从 [!DNL Commerce] 管理员可启用扩展、指定扩展设置、配置Store Assist应用程序用户的安全设置，以及设置用于交付方法的选项。

>[!IMPORTANT]
>
>仅当您连接Adobe Commerce实例和 [!DNL Store Fulfillment] 应用程序。 请参阅 [连接商店履行](connect-set-up-service.md).

## 管理商店履行服务设置

从 [!DNL Commerce Admin Store Configuration] 菜单。

- 通过选择 **[!UICONTROL Stores > Configuration > Services > Store Fulfillment by Walmart Commerce Technologies]**.

   ![用于商店履行的管理商店服务配置](assets/store-services-admin-sf-config.png)

- 通过选择 **[!UICONTROL Store > Configuration > Sales > Delivery Methods > In-Store Pickup]**.

   ![用于商店履行的管理商店销售配置](assets/store-sales-admin-sf-deliver-config.png)

## 基本设置

<table>
<thead>
<tr>
<td><strong>字段</strong></td>
<td><strong>描述</strong></td>
<td><strong>范围</strong></td>
<td><strong>必需</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Price]</strong></td>
<td>您向客户收取的店内装货价格。 默认为零。</td>
<td>网站</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL Search Radius]</strong></td>
<td>购物者在店面结账中搜索商店取货位置时使用的半径（以公里为单位）。 搜索结果仅返回位于指定搜索半径内的存储。</td>
<td>网站</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL Displayed error message]</strong></td>
<td>当客户为无法用于店内装货的物料选择店内装货时显示的消息。 您可以根据需要自定义默认文本。
</td>
<td>存储视图</td>
<td>否</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>的 [!UICONTROL Search Radius] 仅当您配置了 [存储位置和映射设置](store-location-map-provider-setup.md) Adobe Commerce。

## 启用“商店履行”解决方案

启用 [!DNL Store Fulfillment] 解决方案，将店内和库边拾取功能添加到Adobe Commerce店面的购物和结账体验。

<table>
<thead>
<tr>
<td><strong>字段</strong></td>
<td><strong>描述</strong></td>
<td><strong>范围</strong></td>
<td><strong>必需</strong></td>
</tr>
 </thead>
 <tbody>
<tr>
<td><strong>[!UICONTROL Enabled]</strong></td>
<td>启用或禁用解决方案。 启用后，请配置和使用“存储履行”功能，并在Adobe Commerce存储与 [!DNL Store Fulfillment] 服务。 禁用后，所有“商店履行”功能都将被禁用，并且Adobe Commerce与“商店履行”服务之间没有通信。 无法处理或接收订单信息。</td>
<td>全球</td>
<td>是</td>
</tr>
</tbody>
</table>

## 添加帐户凭据

<table>
<tr>
<td><strong>字段</strong></td>
<td><strong>描述</strong></td>
<td><strong>范围</strong></td>
<td><strong>必需</strong></td>
</tr>
<tr>
<td><strong>[!UICONTROL Environment]</strong></td>
<td>选择 <i>[!UICONTROL Sandbox]</i> 或 <i>[!UICONTROL Production]</i><br></br>选择 [!UICONTROL Sandbox] 允许在测试环境中与履行服务进行通信。<br></br>选择 [!UICONTROL Production] 允许在实时环境中与履行服务进行通信。<br></br>系统会为您为每个环境提供一组凭据，并且可以在同一安装中管理这两个凭据集。 <br></br>在验证连接之前保存凭据。</td>
<td>全球</td>
<td>是</td>
</tr>
<tr>
<td><strong>[!UICONTROL API Server URL]</strong></td>
<td>指向Walmart Store Fulfilment API端点的URL。 这必须是载入过程中提供的完全限定的URL。 存储履行客户会收到沙盒URL和生产URL。 添加值时，请确保复制并粘贴完整的URL，包括尾随斜杠“/”。</td>
<td>全球</td>
<td>是</td>
</tr>
<tr>
<td><strong>[!UICONTROL Token Auth Server URL]</strong></td>
<td>指向Walmart Store Fulfilment Authentication端点的URL。 值必须是在载入过程中提供的完全限定的URL。 您将收到沙盒URL和生产URL。 添加值时，请确保复制并粘贴完整的URL，包括尾随斜杠“/”。</td>
<td>全球</td>
<td>是</td>
</tr>
<tr>
<td><strong>[!UICONTROL Merchant Id]</strong></td>
<td>您在载入过程中提供的唯一商户（租户）ID。 此ID用于传送订单，以确保您的商家商店收到订单。</td>
<td>全球</td>
<td>是</td>
</tr>
<tr>
<td><strong>[!UICONTROL Consumer Id]</strong></td>
<td>在载入过程中提供的唯一集成ID。 此ID用于验证Adobe Commerce与存储履行服务之间的所有通信</td>
<td>全球</td>
<td>是</td>
</tr>
<tr>
<td><strong>[!UICONTROL Consumer Secret]</strong></td>
<td>载入过程中提供的唯一集成密钥。 此密钥用于验证Adobe Commerce与存储实现服务之间的所有通信。</td>
<td>全球</td>
<td>是</td>
</tr>
</table>

配置 [!UICONTROL Account Credentials]，选择 <strong>[!UICONTROL Validate Credentials]</strong> 首次验证并建立与存储实现服务的连接。

## 配置日志记录

日志文件中提供了存储实现服务的日志 `var/log/walmart-bopis.log`.

要求系统管理员配置您的环境以允许异常处理，以便可以通过防火墙或缓存捕获与API相关的异常。

由于应用程序日志文件可以快速增长，因此仅在需要时为应用程序启用短时间的日志记录 — 例如，当对 [!DNL Commerce] 订单。 此配置可防止生产环境中由于大型日志文件而导致的响应时间问题。

>[!TIP]
>
>对于Adobe Commerce本地安装，请要求系统管理员为 `var/log/walmart-bopis.log` 文件以最小化大小。 有关Adobe Commerce内部部署安装，请参阅 [日志旋转](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html#server-settings) 在 _Adobe Commerce安装指南_. 有关云基础架构项目的Adobe Commerce，请参阅 [查看和管理日志](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html).

<table>
<thead>
<tr>
<td><strong>字段</strong></td>
<td><strong>描述</strong></td>
<td><strong>范围</strong></td>
<td><strong>必需</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Debug Mode]</strong></td>
<td>调试模式用于增加集成中已记录的活动。 禁用后，不会记录任何调试信息。 启用后，将记录所有调试信息 <br></br>可在文件中找到所有已记录的数据： <pre>var/log/walmart-bopis.log</pre>
<td>全球</td>
<td>否</td>
</tr>
</tbody>
</table>

## 管理订单同步

配置设置以管理订单同步的错误处理，在订单领料期间用于条形码扫描的目录属性，以及配置商店履行队列的订单批大小。

您可以在管理员(
<strong>[!UICONTROL System > Tools > Store Fulfillment Queue]</strong>)。

### 同步错误管理

<table>
<tr>
<td><strong>字段</strong></td>
<td><strong>描述</strong></td>
<td><strong>范围</strong></td>
<td><strong>必需</strong></td>
</tr>
<tr>
<td><strong>[!UICONTROL Retry Critical Error]</strong></td>
<td>指定在发生严重错误后对记录同步操作的重试尝试。<br></br>每当集成无法从履行服务获得正面响应时，都会出现严重错误。 当服务关闭或发送的订单数据出错时，可能会发生这种情况。<br></br>达到重试阈值后，该项目将保留在队列中，但不会再次处理。 查看 <strong>[!UICONTROL System > Tools > Store Fulfillment Queue]</strong> 在管理员中管理。 要对持续出现故障的项目进行故障诊断，请联系您的客户经理。</td>
<td>全球</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Error Notification Email]</strong></td>
<td>启用错误通知，以在 [!UICONTROL Retry Critical Error Threshold] 达到订单。 通知包含有关该错误的所有可用详细信息。</td>
<td>全球</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL Send Error Notification Email To]</strong></td>
<td>错误通知的收件人电子邮件地址列表（以逗号分隔）。</td>
<td>全球</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL Order Sync Exception Email Template]</strong></td>
<td>指定用于通知收件人订单同步错误的电子邮件模板。 提供了默认模板。 它不支持自定义。</td>
<td>存储视图</td>
<td>否</td>
</tr>
</table>

### 订单同步

<table>
<thead>
<tr>
<td><strong>字段</strong></td>
<td><strong>描述</strong></td>
<td><strong>范围</strong></td>
<td><strong>必需</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Barcode Source]</strong></td>
<td>目录属性，用于存储商位置中相应项目的可扫描代码。<br></br>如果您现有的商家位置只有一个，则可能使用UPC代码，而电子商务渠道则会按SKU标识产品。 如果这是您的方案，请选择包含UPC代码的目录属性。<br></br>此设置可确保发送到您的商店列表项目的订单具有正确的标识符，以便商店关联人员能够在挑库过程中准确扫描项目。<br></br>如果您不确定，请在发运和领料部门与您的履行联系人联系，以确定应发送的属性。 如果当前未将Adobe Commerce产品属性包含在数据库中，您可能需要向该属性集中添加相应的属性。</td>
<td>网站</td>
<td>是</td>
</tr>
<tr>
<td><strong>[!UICONTROL Barcode Type]</strong></td>
<td>目录属性，用于存储商位置中相应项目的条形码源。<br></br>此设置可确保发送到您的商店列表项目的订单具有正确的标识符，以便商店关联人员能够在挑库过程中准确扫描项目。 这些选项包括 — SKU、UPC、GTIN、UPCA、EAN13、UPCE0、DISA、UAB、CODABAR、Price Embedded UPC。<br></br>如果不确定，请选择与 [!UICONTROL Barcode Source] 属性。 商店关联仍然可以手动匹配其挑库列表中的项目。</td>
<td>网站</td>
<td>是</td>
</tr>
<tr>
<td><strong>[!UICONTROL Max Number of Items]</strong></td>
<td>一次要从商店履行队列发送的最大项目数。<br></br>BOPIS订单会定期分批发送到履行服务。 利用此设置，可控制批的大小。<br></br>默认值为100项。 根据您的订单量和容量，您可能需要向上或向下调整此值。</td>
<td>全球</td>
<td>否</td>
</tr>
</tbody>
</table>

## 启用“商店履行”发运选项

配置“商店履行”发运选项，以确定Adobe Commerce商店的店内提货和家庭送货选项的可用性。

### 收货方商店

<table>
<thead>
<tr>
<td><strong>字段</strong></td>
<td><strong>描述</strong></td>
<td><strong>范围</strong></td>
<td><strong>必需</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Enable Ship To Store]</strong></td>
<td>收货地点设置基于您现有的收货地点功能。 如果您使用Inventory management，或者如果可以通过商店到商店的库存转移来接受并履行在商家地点没有库存的订单，则将此选项设置为“是”。<br></br>如果您不支持“收货地点”选项或不希望提供该选项，请将设置为“否”。 禁用后，目录中商店的库存为零的项目，或该位置下方的项目 [!DNL Out of Stock Threshold]，不提供店内提货选项。<br></br>这是一个全球性设置，可以按商户位置进行调整。</td>
<td>全球</td>
<td>否</td>
</tr>
</tbody>
</table>

### 从商店发货

<table>
<thead>
<tr>
<td><strong>字段</strong></td>
<td><strong>描述</strong></td>
<td><strong>范围</strong></td>
<td><strong>必需</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Enable Ship From Store]</strong></td>
<td>在您的商户商店中启用或禁用“家庭送货”选项。 启用后，您的商家商店位置将与与您网站关联的库存中其他分配来源一起被考虑。<br></br>在标准Inventory management服务中， [!DNL Ship from Store] is选项是固有的，无法禁用。 使用“商店履行”解决方案，您可以打开或关闭该解决方案。<br></br>这是全局设置。 您还可以根据商家位置和产品调整此设置。</td>
<td>全球</td>
<td>否</td>
</tr>
</tbody>
</table>


## 管理商店履行应用程序使用帐户和权限

配置商店履行应用程序用户帐户和密码安全性以及双重身份验证的设置。

### App Security

<table>
<thead>
<tr>
<td><strong>字段</strong></td>
<td><strong>描述</strong></td>
<td><strong>范围</strong></td>
<td><strong>必需</strong></td>
</tr>
 </thead>
 <tbody>
<tr>
<td><strong>[!UICONTROL User Session Lifetime]</strong></td>
<td>存储关联用户会话在自动注销之前保持活动状态的时间范围（以秒为单位）。 有效值介于60到31536000之间。</td>
<td>全球</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL Maximum Login Failures to Lockout Account]</strong></td>
<td>指定在将存储关联锁定到其帐户之外之前允许的失败登录尝试次数。<br></br>要禁用帐户锁定，请将值设置为0。</td>
<td>全球</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL Lockout Time (minutes)]</strong></td>
<td>登录失败后锁定帐户的分钟数。</td>
<td>全球</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL Force Password Change]</strong></td>
<td><em>[!UICONTROL Yes]</em>:要求用户在设置帐户后更改其密码。<br></br><em>[!UICONTROL No]</em>:建议用户在设置帐户后更改密码。</td>
<td>全球</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL Password Lifetime]</strong></td>
<td>在所需密码更改前密码保持有效的天数。 将留空以禁用此选项。</td>
<td>全球</td>
<td>否</td>
</tr>
</tbody>
</table>

### 双重身份验证

<table>
<thead>
<tr>
<td><strong>字段</strong></td>
<td><strong>描述</strong></td>
<td><strong>范围</strong></td>
<td><strong>必需</strong></td>
</tr>
 </thead>
 <tbody>
<tr>
<td><strong>[!UICONTROL APP User 2FA]</strong></td>
<td>启用或禁用存储关联的双重身份验证。 当启用时，提示存储关联提供由验证提供者生成的一次性密码。</td>
<td>全球</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL APP 2FA Policy]</strong></td>
<td>设置双重身份验证的实施策略。<br></br><strong>[!UICONTROL Optional]</strong>:如果未设置提供程序，则存储关联可以绕过双重身份验证。<br></br><strong>[!UICONTROL Mandatory]</strong>:需要存储关联才能完成双重身份验证。</td>
<td>全球</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL 2FA Providers]</strong></td>
<td>选择一个或多个身份验证提供商服务以提供商店关联。 要设置双重身份验证和身份验证，商店关联商必须从其移动设备上安装的可用提供商之一安装身份验证应用程序。</td>
<td>全球</td>
<td>否</td>
</tr>
</tbody>
</table>

## 投放方法

通过扩展本机Adobe Commerce进行存储实现工作 [!DNL In-Store Delivery] 功能。 安装扩展后，您可以使用以下添加到管理员的扩展设置配置商店内交付方法。

- **店内提货** — 结帐过程中店内交付的选件选项这是BOPIS订单的最常见交付方案。

- **[!UICONTROL Curbside pick up]** — 提供选项，供客户在商店位置暂停，并由商店关联商将订单交付给他们。

通过选择 <strong>[!UICONTROL Stores > Configuration > Sales > Delivery Methods > In-Store Pickup]</strong>.

>[!NOTE]
>
>有关配置店内投放选项的其他信息，请参阅 [店内投放](https://docs.magento.com/user-guide/shipping/shipping-in-store-delivery.html) 在 _Adobe Commerce用户指南_.


### 投放方法配置

使用店内交货方法，客户可以在结帐期间选择一个来源作为提货地点。

<table>
<thead>
<tr>
<td><strong>字段</strong></td>
<td><strong>描述</strong></td>
<td><strong>范围</strong></td>
<td><strong>必需</strong></td>
</tr>
 </thead>
 <tbody>
<tr>
<td><strong>[!UICONTROL Enable In-Store Pickup]</strong></td>
<td>对于选择商店提货的客户，在结帐期间可启用或禁用店内提货选项。 禁用店内提取后，不显示选项。<br></br>此全局设置适用于所有零售商店位置。 启用后，您可以在零售商店位置有选择地禁用该功能。</td>
<td>网站</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Curbside Pickup]</strong></td>
<td>在结帐过程中，为选择商店提货的客户启用或禁用购物车提货选项。<br></br>此全局设置适用于所有零售商店位置。 启用后，您可以在零售商店位置有选择地禁用该功能。</td>
<td>网站</td>
<td>否</td>
</tr>
</tbody>
</table>

### 投放方法标题配置

<table>
<thead>
<tr>
<th><strong>字段</strong></th>
<th><strong>描述</strong></th>
<th><strong>范围</strong></th>
<th><strong>必需</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>主页投放标题</strong></td>
<td>在产品、购物车和结帐区域中指定“主页递送”选项要显示的标题。 送货上门是指Adobe Commerce的标准送货功能 — 从仓库、承运人或直接到客户提供的送货地址。 </br></br>此标签不影响所选装运承运人的装运方法标签。</td>
<td>存储视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>主页投放描述</strong></td>
<td>一个可选描述，每当向客户显示主页投放标题时，该描述都会显示。 大多数情况下，描述是用于传达您的投放承诺的静态消息。 一些示例：</br><code>Same-day shipping on orders by 4</code></br></br><code>Ships within 2 business days</code></td>
<td>存储视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>存储拾取标题</strong></td>
<td>向客户显示交货选项并提供店内装货时，将显示此标签。 </br></br>您可以自定义此标签，该标签显示在产品、购物车和结帐区域。</td>
<td>存储视图</td>
<td>否</td>
</tr>
<td><strong>存储装货说明</strong></td>
<td>只要显示“商店提货标题”，您就可以选择包含描述。 此静态消息有助于改善与商店取货体验相关的客户通信。 一些示例：</br></br><code>Get it today for free!</code></br></br><code>Ready for pickup in an hour!</code></td>
<td>存储视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>店内提货标题</strong></td>
<td>启用“店内提货”后，此标题将作为“商店提货”交付选项显示给客户。 您可以自定义其标签。</td>
<td>存储视图</td>
<td>否</td>
</tr>
<tr>
<tr>
<td><strong>曲边拾取标题</strong></td>
<td>启用“库边提货”后，该选项会以“商店提货”交货选项的类型显示给客户。 您可以在此处自定义其标签。</td>
<td>存储视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>店内提取说明</strong></td>
<td>在您的零售店准备好提货后，会通过电子邮件通知客户。 如果客户已选择 [!DNL In-Store Pickup] 在结帐过程中，您可以在此处自定义取货说明。 </br></br>这是适用于所有零售商店位置的全局设置。 您还可以在零售商店位置级别自定义相关说明。</td>
<td>存储视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>曲线拾取说明</strong></td>
<td>指定自定义订单提货指令，以在客户电子邮件通知中包含对策提货订单的提示。 </br></br>这是适用于所有零售商店位置的全局设置。 您还可以在零售商店位置级别自定义相关说明。</td>
<td>存储视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>预计提货提前期</strong></td>
<td>在收到、履行并准备接收订单之前需要的分钟数。 在为“商店提货”交付选项选择零售商店位置时，会向客户显示此信息。 这是一个全局设置，适用于所有零售商店位置。 您还可以在零售商店位置级别自定义提前期。</td>
<td>存储视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>预计提货时间标签</strong></td>
<td>显示订单可供客户装货之前的预计时间。 当客户为 [!DNL In-Store Pickup] 投放选项。 </br></br>自定义此标签时，您可以使用代码 <code>%1</code> 插入 <strong>预计提货提前期</strong>. 例如：</br></br><code>Ready for Pickup in %1 minutes.</code></br></br>这是适用于所有零售商店位置的全局设置。 您还可以在零售商店位置级别自定义提前期。</br></br><code>Ready for Pickup in %1 minutes.</code></br></br></td>
<td>存储视图</td>
<td>否</td>
<tr>
<td><strong>提货时间免责声明</strong></td>
<td>在工具提示中产品页面上显示的内容，其中列出了存储时间、假日、意外关闭等</td>
<td>存储视图
</td>
<td>否
</td>
</tr>
</tbody></table>

### 库存可用性标题配置

<table>
<thead>
<tr>
<th><strong>字段</strong></th>
<th><strong>描述</strong></th>
<th><strong>范围</strong></th>
<th><strong>必需</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>库存</strong></td>
<td>当客户使用零售商店货位时，将显示每个位置的当前项目的库存可用性。 </br></br>您可以自定义 <em>[!UICONTROL in-stock]</em> 此处为状态标签。</br></br></td>
<td>存储视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>缺货</strong></td>
<td>当客户使用零售商店货位时，每个位置都会显示任何当前项目的库存可用性。</td>
<td>存储视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>部分库存</strong></td>
<td>当客户使用零售商店货位时，每个位置都会显示任何当前项目的库存可用性。 </br></br>您可以自定义 <em>[!UICONTROL partially in-stock]</em> 此处为状态标签。</br></br></td>
<td>存储视图</td>
<td>否</td>
</tr>
</tbody></table>
