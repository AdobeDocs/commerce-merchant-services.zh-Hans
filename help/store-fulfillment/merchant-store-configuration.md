---
title: 商户商店配置
description: '设置可增强Inventory management源作为商户商店。 '
role: User, Admin
level: Intermediate
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '1209'
ht-degree: 0%

---

# 商户商店（来源）配置

此解决方案通过为商户扩展面向操作的库存源来增强本机Inventory management功能。

- 为商店位置添加地理坐标
- 将源指定为 [!DNL Store Pickup Location] 和指定可用的发运能力（收货方商店、发货方商店）
- 指定可用的拾取选项（店内或库边）、自定义拾取说明以及其他信息，以便向客户传递拾取详细信息和说明

术语 _来源_ 和 _商家商店位置_ 可互换使用。 所有记录都是库存来源，但来源也可以是商户商店位置，具体取决于配置设置。

从管理员管理商家商店配置： **[!UICONTROL Stores > Inventory > Sources >  Edit Source]**.

>[!NOTE]
>
>在设置过程中，可能需要在创建源或更新现有源后刷新缓存。

## **常规**

<table>
<tbody>
<tr>
<th>字段</th>
<th>描述</th>
<th>范围</th>
<th>必需</th>
</tr>
<tr>
<td><strong>[!UICONTROL Latitude]</strong></br><code>Base Attribute: latitude</code></td>
<td>商家商店位置的纬度坐标。 在店面体验的位置搜索和地图放置时，会使用此必需信息。 值必须与存储的确切地址匹配才能通过验证。</td>
<td>全球</td>
<td>是</td>
</tr>
<tr>
<td><strong>[!UICONTROL Longitude]</strong></br><code>Base Attribute: Longitude</code></td>
<td>商家商店位置的纵向坐标。 在店面体验的位置搜索和地图放置时，会使用此必需信息。 值必须与存储的确切地址匹配才能通过验证。</td>
<td>全球</td>
<td>是</td>
</tr>
<tr>
<td><strong>[!UICONTROL Use as Pickup Location]</br></strong><code>Base Attribute: is_pickup_location_active</code></td>
<td>将源指定为可用的商店提货位置。 此设置确定是否同步源并向访客显示源。</td>
<td>全球</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship to Store]</strong><br><code>Extension Attribute: allow_ship_to_store</code></td>
<td>在源级别配置送货到存储功能。 有关更多信息，请参阅[常规配置](enable-general.md)选项， <strong>[!UICONTROL Enable Ship To Store]
</tr>
<tr>
<td><strong>[!UICONTROL Latitude]</strong></br><code>Base Attribute: latitude</code></td>
<td>商家商店位置的纬度坐标。 在店面体验的位置搜索和地图放置时，会使用此必需信息。 值必须与存储的确切地址匹配才能通过验证。</td>
<td>全球</td>
<td>是</td>
</tr>
<tr>
<td><strong>[!UICONTROL Longitude]</strong></br><code>Base Attribute: Longitude</code></td>
<td>商家商店位置的纵向坐标。 在店面体验的位置搜索和地图放置时，会使用此必需信息。 值必须与存储的确切地址匹配才能通过验证。</td>
<td>全球</td>
<td>是</td>
</tr>
<tr>
<td><strong>[!UICONTROL Use as Pickup Location]</br></strong><code>Base Attribute: is_pickup_location_active</code></td>
<td>将源指定为可用的商店提货位置。 此设置确定是否同步源并向访客显示源。</td>
<td>全球</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship to Store]</strong></br> <code>Extension Attribute: [!DNL allow_ship_to_store]</code></td>
<td>在源级别配置送货到存储功能。 有关更多信息，请参阅[常规配置](enable-general.md)选项， <strong>[!UICONTROL Enable Ship To Store]</strong>.</td>
<td>全球</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship From Store]</strong></br><code>Extension Attribute: [!DNL use_as_shipping_source]</code></td>
 <td>在源级别配置发货 — 商店功能。 有关更多信息，请参阅[常规配置](enable-general.md)选项， [!UICONTROL Enable Ship From Store].</td>
<td>全球</td>
<td>否</td>
</tr>
<tr>
<td>全球</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship From Store]</strong><code>Extension Attribute: [!DNL use_as_shipping_source]</code></td><td></td><td></td><td></td></tr></tbody></table>



| **字段** | **描述** | **范围** | **必需** |
|--------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Latitude]**</br>`Base Attribute: latitude` | 商家商店位置的纬度坐标。 在店面体验的位置搜索和地图放置时，会使用此必需信息。 值必须与存储的确切地址匹配才能通过验证。 | 全球 | 是 |
| **[!UICONTROL Longitude]**</br>`Base Attribute: Longitude` | 商家商店位置的纵向坐标。 在店面体验的位置搜索和地图放置时，会使用此必需信息。 值必须与存储的确切地址匹配才能通过验证。 | 全球 | 是 |
| **[!UICONTROL Use as Pickup Location]**</br>`Base Attribute:[!DNL is_pickup_location_active]` | 将源指定为可用的商店提货位置。 此设置确定是否同步源并向访客显示源。 | 全球 | 否 |
| **[!UICONTROL Enable Ship to Store]**</br>`Extension Attribute: [!DNL allow_ship_to_store]` | 在源级别配置送货到存储功能。 有关更多信息，请参阅 [常规配置](enable-general.md) 选项， **[!UICONTROL Enable Ship To Store]**. | 全球 | 否 |
| **[!UICONTROL Enable Ship From Store]**</br>`Extension Attribute: [!DNL use_as_shipping_source]` | 在源级别配置发货 — 商店功能。 有关更多信息，请参阅 [常规配置](enable-general.md) 选项， [!UICONTROL Enable Ship From Store] | 全球 | 否 |

{style=&quot;table-layout:auto&quot;}

## 拾取位置配置

| **字段** | **描述** | **范围** | **必需** |
|-----------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Allow In-Store Pickup]**</br>`Extension Attribute: [!DNL store_pickup_enabled]` | 两个取货选项之一。 [!DNL In-Store Pickup] 指允许客户进入商户商店位置以检索其订单的功能。 </br></br>启用后，可能会在结帐期间向客户显示此选项。 </br></br>此选项还会将全局配置覆盖为 [!UICONTROL Enable In-store Pickup] 在 [!UICONTROL Delivery Method] 表示 [!UICONTROL In-store Pickup] | 全球 | 否 |
| **店内提取说明**</br>`Extension Attribute: store_pickup_instructions` | 在 **准备在商店中取货** 电子邮件通知。 | 全球 | 否 |
| **允许策划**</br>`Extension Attribute: curbside_enabled` | 两个取货选项之一。 库边交货允许客户将其车辆停放在商店位置的指定地点。 在此方案中，商店关联会将订单交付给客户。 </br></br>启用后，可在结帐期间向客户显示此选项。 此外，在签到过程中，可能会要求客户描述他们的车辆和停车位。 </br></br>此选项还会将全局配置覆盖为 **启用曲线拾取** 在 **投放方法** 表示 **店内取货** | 全球 | 否 |
| **[!UICONTROL Curbside Instructions]**</br>`Extension Attribute: curbside_instructions` | 在 [!UICONTROL Order Ready For Pickup in Store] 电子邮件通知。 | 全球 | 否 |
| **[!UICONTROL Estimated Pickup Lead Time]**</br>`Extension Attribute: pickup_lead_time` | 接收、接收和准备接收订单前需要的分钟数。 </br></br>此信息用于显示网站上向客户发出订单的预计时间。</br></br> 设置此选项将覆盖 **预计提货提前期** 为 **投放方法** 在 **店内取货** 配置。 | 全球 | 否 |
| **[!UICONTROL Estimated Pickup Time Label]**</br>`Extension Attribute: pickup_time_label` | 标签，显示在订单准备就绪后等待接收的分钟数。</br></br> 自定义此标签时，可使用代码%1插入 **预计提货提前期**.</br></br> 设置此选项将覆盖 [!UICONTROL Estimated Pickup Time Label] 为 [!UICONTROL Delivery Method] 在 [!UICONTROL In-store Pickup]. | 全球 | 否 |

### **开始时间**

| **字段** | **描述** | **范围** | **必需** |
|------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Location Timezone]**</br>`Extension Attribute: timezone` | 商家商店位置的时区。 对于每天，设置开始和结束时间。</br></br>这些设置用于优化估计的提货时间和履行服务报告。 | 全球 | 是 |
| **[!UICONTROL Opening Hours]**</br>`Internal Attribute: inventory_source_opening_hours_dynamic_rows` | 商家商店位置的工作时间。 </br></br>此信息可用于优化估计的拾取时间和履行服务报告。 | 全球 | 是 |

### 配置签入体验界面选项



| **字段** | **描述** | **范围** | **必需** |
|---------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Use Parking Spots]**</br>`Extension Attribute: parking_spots_enabled` | 指定商家商店位置是否具有用于库边装货的指定停车位。 </br></br>启用后，您可以配置可用的停车位。 | 全球 | 否 |
| **[!UICONTROL Is Parking Spot a Mandatory Field?]**</br>`Extension Attribute: parking_spot_mandatory` | 指定在购物体验期间是否需要客户的停车位标识。</br></br>如果启用，则提示客户在到达时指定其停车位。 如果禁用，客户可以跳过此输入。 | 全球 | 否 |
| **[!UICONTROL Parking Spots List]**</br> `Internal Attribute: inventory_source_parking_spot_dynamic_rows` | 这家商店位于商店，可供客人在商店内购物。 使用提供的界面命名每个点。</br></br> 您无需为每个停车位点命名，只需为库边指定地点。 例如，您可能有A-G行的停车位，但只有A行的前8个点指定用于库边装货。 在这种情况下，您可以定义8个点；例如：A1、A2、A3等。 | 全球 | 否 |
| **[!UICONTROL Allow "Other" Parking Spot Field]**</br>`Extension Attribute: custom_parking_spot_enabled` | 启用此设置后，客户便可在签入期间描述其停车地点。 | 全球 | 否 |
| **[!UICONTROL Use Car Color]**</br>`Extension Attribute: use_car_color` | 指定是否在签入期间支持从客户收集车辆颜色。 </br></br> 可用的选择 [!UICONTROL Car Color] 在管理员中配置 [签入体验的系统设置](check-in-experience-setup.md). | 全球 | 否 |
| **[!UICONTROL Is Car Color a Mandatory Field?]**</br>`Extension Attribute: car_color_mandatory` | 指定在签入期间是否需要客户使用车辆颜色标识。</br></br>如果启用，系统会提示客户在到达时指定车辆的颜色。 如果禁用，客户可以跳过此输入。 | 全球 | 否 |
| **[!UICONTROL Use Car Make]** </br>`Extension Attribute: use_car_make` | 指定是否在签入期间支持从客户收集车辆制造。</br></br> 可用的选择 [!UICONTROL Car Make] 在管理员中配置 [签入体验的系统设置](check-in-experience-setup.md). | 全球 | 否 |
| **[!UICONTROL Is Car Make a Mandatory Field?]**</br>`Extension Attribute: car_make_mandatory` | 指定在签入期间是否需要客户进行车辆识别。</br></br>如果启用，系统会提示客户在到达时指定其车辆的型号。 如果禁用，客户可以跳过此输入。 | 全球 | 否 |
| **[!UICONTROL Use Additional Information]**</br> `Extension Attribute: use_additional_information` | 指定在签入期间是否支持从客户收集其他信息。 | 全球 | 否 |
| **[!UICONTROL Is Additional Information a Mandatory Field?]**</br>`Extension Attribute: additional_information_mandatory` | 指定在签入期间是否需要客户的其他信息。 </br></br>如果启用，系统会提示客户在到达时输入其他信息。 如果禁用，客户可以跳过此输入。 | 全球 | 否 |







