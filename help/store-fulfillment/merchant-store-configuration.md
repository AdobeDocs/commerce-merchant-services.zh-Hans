---
title: 商家商店配置
description: 将增强的Inventory management源设置为商户商店。
role: User, Admin
level: Intermediate
exl-id: 7c3444d0-5ecb-4ac1-aa81-e48eea290f5d
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '1206'
ht-degree: 0%

---

# 商户商店（源）配置

此解决方案通过为商家使用面向操作的功能扩展库存来源，增强了原生Inventory management功能。

- 添加商店位置的地理坐标
- 将源指定为 [!DNL Store Pickup Location] 并指定可用的配送功能（收货商店、发货商店）
- 指定可用的取车选项（店内或路边）、自定义的取车说明和其他信息，以便向客户传达取车详细信息和说明

条款 _源_ 和 _商家商店位置_ 可互换使用。 所有记录都是库存来源，但来源也可以是商家商店位置，具体取决于配置设置。

从管理员管理商户商店配置： **[!UICONTROL Stores > Inventory > Sources >  Edit Source]**.

>[!NOTE]
>
>在设置过程中，可能必须在创建源或更新现有源之后刷新缓存。

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
<td>商户商店位置的纬度坐标。 此必需信息用于店面体验中的位置搜索和地图放置。 该值必须与存储区的确切地址匹配才能通过验证。</td>
<td>全局</td>
<td>是</td>
</tr>
<tr>
<td><strong>[!UICONTROL Longitude]</strong></br><code>Base Attribute: Longitude</code></td>
<td>商户商店位置的纵向坐标。 此必需信息用于店面体验中的位置搜索和地图放置。 该值必须与存储区的确切地址匹配才能通过验证。</td>
<td>全局</td>
<td>是</td>
</tr>
<tr>
<td><strong>[!UICONTROL Use as Pickup Location]</br></strong><code>Base Attribute: is_pickup_location_active</code></td>
<td>将源指定为可用的商店代答位置。 此设置确定是否同步源并向访客显示。</td>
<td>全局</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship to Store]</strong><br><code>Extension Attribute: allow_ship_to_store</code></td>
<td>在源级别配置收货到存储功能。 有关更多信息，请参阅[常规配置](enable-general.md)选项， <strong>[!UICONTROL Enable Ship To Store]
</tr>
<tr>
<td><strong>[!UICONTROL Latitude]</strong></br><code>Base Attribute: latitude</code></td>
<td>商户商店位置的纬度坐标。 此必需信息用于店面体验中的位置搜索和地图放置。 该值必须与存储区的确切地址匹配才能通过验证。</td>
<td>全局</td>
<td>是</td>
</tr>
<tr>
<td><strong>[!UICONTROL Longitude]</strong></br><code>Base Attribute: Longitude</code></td>
<td>商户商店位置的纵向坐标。 此必需信息用于店面体验中的位置搜索和地图放置。 该值必须与存储区的确切地址匹配才能通过验证。</td>
<td>全局</td>
<td>是</td>
</tr>
<tr>
<td><strong>[!UICONTROL Use as Pickup Location]</br></strong><code>Base Attribute: is_pickup_location_active</code></td>
<td>将源指定为可用的商店代答位置。 此设置确定是否同步源并向访客显示。</td>
<td>全局</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship to Store]</strong></br> <code>Extension Attribute: [!DNL allow_ship_to_store]</code></td>
<td>在源级别配置收货到存储功能。 有关更多信息，请参阅[常规配置](enable-general.md)选项， <strong>[!UICONTROL Enable Ship To Store]</strong>.</td>
<td>全局</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship From Store]</strong></br><code>Extension Attribute: [!DNL use_as_shipping_source]</code></td>
 <td>在源级别配置发货商店功能。 有关更多信息，请参阅[常规配置](enable-general.md)选项， [!UICONTROL Enable Ship From Store].</td>
<td>全局</td>
<td>否</td>
</tr>
<tr>
<td>全局</td>
<td>否</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship From Store]</strong><code>Extension Attribute: [!DNL use_as_shipping_source]</code></td><td></td><td></td><td></td></tr></tbody></table>



| **字段** | **描述** | **范围** | **必需** |
|--------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Latitude]**</br>`Base Attribute: latitude` | 商户商店位置的纬度坐标。 此必需信息用于店面体验中的位置搜索和地图放置。 该值必须与存储区的确切地址匹配才能通过验证。 | 全局 | 是 |
| **[!UICONTROL Longitude]**</br>`Base Attribute: Longitude` | 商户商店位置的纵向坐标。 此必需信息用于店面体验中的位置搜索和地图放置。 该值必须与存储区的确切地址匹配才能通过验证。 | 全局 | 是 |
| **[!UICONTROL Use as Pickup Location]**</br>`Base Attribute:[!DNL is_pickup_location_active]` | 将源指定为可用的商店代答位置。 此设置确定是否同步源并向访客显示。 | 全局 | 否 |
| **[!UICONTROL Enable Ship to Store]**</br>`Extension Attribute: [!DNL allow_ship_to_store]` | 在源级别配置收货到存储功能。 欲了解更多信息，请参见 [常规配置](enable-general.md) 选项， **[!UICONTROL Enable Ship To Store]**. | 全局 | 否 |
| **[!UICONTROL Enable Ship From Store]**</br>`Extension Attribute: [!DNL use_as_shipping_source]` | 在源级别配置发货商店功能。 欲了解更多信息，请参见 [常规配置](enable-general.md) 选项， [!UICONTROL Enable Ship From Store] | 全局 | 否 |

{style="table-layout:auto"}

## 取车地点配置

| **字段** | **描述** | **范围** | **必需** |
|-----------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Allow In-Store Pickup]**</br>`Extension Attribute: [!DNL store_pickup_enabled]` | 两个取车选项之一。 [!DNL In-Store Pickup] 是指允许客户输入商家商店位置以检索其订单的功能。 </br></br>启用后，可在结帐期间向客户显示此选项。 </br></br>此选项还会将全局配置覆盖到 [!UICONTROL Enable In-store Pickup] 已在 [!UICONTROL Delivery Method] 对象 [!UICONTROL In-store Pickup] | 全局 | 否 |
| **店内取货说明**</br>`Extension Attribute: store_pickup_instructions` | 在以下位置向客户发送可自定义的消息： **可供店内取货的订单** 电子邮件通知。 | 全局 | 否 |
| **允许路边**</br>`Extension Attribute: curbside_enabled` | 两个取车选项之一。 路边交付允许客户将其车辆停放在商户商店位置的指定位置。 在此方案中，订单由商店关联交付给客户。 </br></br>启用后，可在结帐期间向客户显示此选项。 此外，在办理登记入住手续时，客户可能需要描述自己的车辆和停车场。 </br></br>此选项还会将全局配置覆盖到 **启用路边取车** 已在 **投放方法** 对象 **店内取货** | 全局 | 否 |
| **[!UICONTROL Curbside Instructions]**</br>`Extension Attribute: curbside_instructions` | 在以下位置向客户发送可自定义的消息： [!UICONTROL Order Ready For Pickup in Store] 电子邮件通知。 | 全局 | 否 |
| **[!UICONTROL Estimated Pickup Lead Time]**</br>`Extension Attribute: pickup_lead_time` | 接收、领料和准备领料订单之前所需的分钟数。 </br></br>此信息用于在网站上向客户显示订单提货的估计时间。</br></br> 设置此选项将覆盖的全局配置 **估计的装货提前期** 已为 **投放方法** 在 **店内取货** 配置。 | 全局 | 否 |
| **[!UICONTROL Estimated Pickup Time Label]**</br>`Extension Attribute: pickup_time_label` | 显示订单准备好提取之前所经过分钟数的标签。</br></br> 在自定义此标签时，您可以使用代码%1插入 **估计的装货提前期**.</br></br> 设置此选项将覆盖的全局配置 [!UICONTROL Estimated Pickup Time Label] 已为 [!UICONTROL Delivery Method] 在 [!UICONTROL In-store Pickup]. | 全局 | 否 |

### **营业时间**

| **字段** | **描述** | **范围** | **必需** |
|------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Location Timezone]**</br>`Extension Attribute: timezone` | 商家存储位置的时区。 对于每一天，设置开始和结束时间。</br></br>这些设置用于优化预计取车时间和履行服务报表。 | 全局 | 是 |
| **[!UICONTROL Opening Hours]**</br>`Internal Attribute: inventory_source_opening_hours_dynamic_rows` | 商家商店位置的营业时间。 </br></br>此信息可用于优化估计的取车时间，以及在履行服务报告中。 | 全局 | 是 |

### 配置签入Experience界面选项



| **字段** | **描述** | **范围** | **必需** |
|---------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Use Parking Spots]**</br>`Extension Attribute: parking_spots_enabled` | 指定商户商店位置是否具有指定路边取车的停车位。 </br></br>启用后，您可以配置可用的停车位。 | 全局 | 否 |
| **[!UICONTROL Is Parking Spot a Mandatory Field?]**</br>`Extension Attribute: parking_spot_mandatory` | 指定客户在购物体验期间是否需要停车位识别。</br></br>如果启用，则提示客户在到达时指定其停车位。 如果禁用，客户可以跳过此输入。 | 全局 | 否 |
| **[!UICONTROL Parking Spots List]**</br> `Internal Attribute: inventory_source_parking_spot_dynamic_rows` | 这家商铺位置提供路边取车的停车位。 使用提供的界面为每个点命名。</br></br> 你不需要给每个停车场命名，只需要给指定路边停车场命名。 例如，您可能有A-G行停车可用，但只有A行的前8个地点被指定用于路边取车。 在此方案中，您可以定义8个位置；例如：A1、A2、A3等。 | 全局 | 否 |
| **[!UICONTROL Allow "Other" Parking Spot Field]**</br>`Extension Attribute: custom_parking_spot_enabled` | 启用后，此设置允许客户在登记入住期间描述其停车场。 | 全局 | 否 |
| **[!UICONTROL Use Car Color]**</br>`Extension Attribute: use_car_color` | 指定是否支持在登记入住期间从客户收集车辆颜色。 </br></br> 可用的选择 [!UICONTROL Car Color] 在管理员中配置 [签入体验的系统设置](check-in-experience-setup.md). | 全局 | 否 |
| **[!UICONTROL Is Car Color a Mandatory Field?]**</br>`Extension Attribute: car_color_mandatory` | 指定客户在登记入住期间是否需要车辆颜色标识。</br></br>如果启用，则提示客户在到达时指定其车辆的颜色。 如果禁用，客户可以跳过此输入。 | 全局 | 否 |
| **[!UICONTROL Use Car Make]** </br>`Extension Attribute: use_car_make` | 指定在登记入住期间是否支持从客户处收集车辆。</br></br> 可用的选择 [!UICONTROL Car Make] 在管理员中配置 [签入体验的系统设置](check-in-experience-setup.md). | 全局 | 否 |
| **[!UICONTROL Is Car Make a Mandatory Field?]**</br>`Extension Attribute: car_make_mandatory` | 指定客户在登记入住期间是否需要车辆制造标识。</br></br>如果启用，则系统会提示客户在到达时指定其车辆的厂牌。 如果禁用，客户可以跳过此输入。 | 全局 | 否 |
| **[!UICONTROL Use Additional Information]**</br> `Extension Attribute: use_additional_information` | 指定在签入期间是否支持从客户收集其他信息。 | 全局 | 否 |
| **[!UICONTROL Is Additional Information a Mandatory Field?]**</br>`Extension Attribute: additional_information_mandatory` | 指定客户在签入期间是否需要其他信息。 </br></br>如果启用，则提示客户在到达时输入附加信息。 如果禁用，客户可以跳过此输入。 | 全局 | 否 |
