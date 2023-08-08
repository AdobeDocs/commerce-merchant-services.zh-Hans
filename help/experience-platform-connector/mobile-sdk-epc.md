---
title: 将Adobe Experience Platform Mobile SDK与Commerce集成
description: 了解如何将Adobe Experience Platform Mobile SDK与Headless或自定义Commerce店面结合使用。
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: cae4d26d389376476b9b6a567841a847cc9c9732
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---

# 将Adobe Experience Platform Mobile SDK与Commerce集成

>[!IMPORTANT]
>
>适用于iOS的Adobe Experience Platform Mobile SDK支持iOS 11或更高版本。

集成 [Adobe Experience Platform移动SDK](https://developer.adobe.com/client-sdks/documentation/) 使用Commerce移动应用程序，商家可以发送Commerce  [事件数据](events.md) 到Experience Platform边缘。

当Commerce事件数据在边缘可用时，其他Adobe Experience Cloud应用程序可以访问该数据。 例如，您可以使用这些数据在Real-Time CDP中构建受众，然后 [使用这些受众](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html) 以个性化您的Commerce移动应用程序。

## 配置

要开始将Adobe Experience Platform Mobile SDK与Commerce结合使用，请在Experience Platform中安装和配置该SDK。 然后，在Commerce中完成配置。

### Experience Platform

1. 通过查看 [移动应用程序中的Adobe Experience Cloud教程](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/overview.html).

1. [安装和配置](https://developer.adobe.com/client-sdks/documentation/getting-started/) Experience Platform中的SDK。

   >[!NOTE]
   >
   >您在Experience Platform中创建和配置的架构与在Commerce移动设备应用程序中的应用程序代码中使用的架构相同。

### 商务

完成Experience Platform的SDK配置后，将SDK配置添加到Commerce。

1. 要通过SDK将Commerce事件数据发送到Experience Platform，您必须在应用程序代码中提供XDM架构。 此架构必须与架构匹配 [已配置](https://developer.adobe.com/client-sdks/documentation/getting-started/set-up-schemas-and-datasets/) Experience Platform中的SDK的。

以下示例显示如何跟踪 `web.webpagedetails.pageViews` 事件并设置 `identityMap` 使用“电子邮件”字段。

    ```javascript
    let stateName = &quot;luma： content： ios： us： en： home&quot;
    var xdmData： [字符串：任何] = [
    &quot;eventType&quot;： &quot;web.webpagedetails.pageViews&quot;，
    &quot;web&quot;： [
    &quot;webPageDetails&quot;： [
    &quot;pageViews&quot;： [
    &quot;value&quot;： 1
    ]，
    &quot;name&quot;： &quot;Home page&quot;
    ]
    ]
    ]
    
    let experienceEvent = ExperienceEvent(xdm： xdmData)
    Edge.sendEvent(experienceEvent： experienceEvent)
    
    // Adobe Experience Platform — 更新标识
    let emailLabel = &quot;mobileuser@example.com&quot;
    
    let identityMap： IdentityMap = IdentityMap()
    identityMap.add(item： IdentityItem(id： emailLabel)， withNamespace： &quot;Email&quot;)
    Identity.updateIdentities(with： identityMap)
    ```

1. 连接到Commerce Cloud环境。

   在您的项目构建设置中，将URL添加到Commerce GraphQL端点。 例如：

   - 调试： http://_调试_.commercesite.cloud/graphql/
   - 发行版本： http://_版本_.commercesite.cloud/graphql/

1. 要从Commerce GraphQL端点检索数据，首先使用生成项目中的必要文件和目录 [阿波罗代码生成器](https://www.apollographql.com/docs/ios/).

   1. 从您的项目目录中， [安装](https://www.apollographql.com/docs/ios/get-started#1-install-the-apollo-frameworks) 阿波罗·iOS。

   1. [初始化](https://www.apollographql.com/docs/ios/code-generation/codegen-cli/#initialize) Apollo Codegen CLI。

      这会创建 `apollo-codegen-configuration.json` 文件。

   1. 通过替换项目中的内容来生成所需的GraphQL文件和目录 `apollo-codegen-configuration.json` 文件包含以下内容：

      ```json
      {
      "schemaName" : "MagentoAPI",
      "input" : {
          "operationSearchPaths" : [
          "**/*.graphql"
          ],
          "schemaSearchPaths" : [
          "**/*.graphqls"
          ]
      },
      "output" : {
          "testMocks" : {
          "none" : {
          }
          },
          "schemaTypes" : {
          "path" : "../MagentoAPI",
          "moduleType" : {
              "swiftPackageManager" : {
              }
          }
          },
          "operations" : {
          "inSchemaModule" : {
          }
          }
      },
      "schemaDownloadConfiguration": {
          "downloadMethod": {
              "introspection": {
                  "endpointURL": "http://magento24.com/graphql/",
                  "httpMethod": {
                      "POST": {}
                  },
                  "includeDeprecatedInputValues": false,
                  "outputFormat": "SDL"
              }
          },
          "downloadTimeout": 60,
          "headers": [],
          "outputPath": "magento.graphqls"
      }
      }
      ```

   1. [Fetch](https://www.apollographql.com/docs/ios/code-generation/codegen-cli/#fetch-schema) Commerce GraphQL架构。

      确保路径到 `./apollo-codegen-config.json` 文件，其中包含对Commerce GraphQL架构的引用。

   1. [生成](https://www.apollographql.com/docs/ios/code-generation/codegen-cli/#generate) 源代码。

      确保路径到 `./apollo-codegen-config.json` 文件，其中包含生成所需文件和目录的配置信息。

   1. 新创建的内部 **GraphQLGerated** 文件夹，添加或编辑GraphQL类型。 例如，您可以添加 `DynamicBlocks.graphql` 键入以下内容：

      ```graphql
      query dynamicBlocks($input: DynamicBlocksFilterInput){
          dynamicBlocks(input: $input)
          {
              items {
                  content {
                      html
                  }
              }
          }
      }
      ```

   您现在已将Adobe Experience Platform Mobile SDK与Commerce移动应用程序集成。 事件数据从您的应用程序流向Experience Platform边缘。

要了解如何从移动Commerce应用程序中检索Real-Time CDP受众以告知购物车价格规则和动态块，请参阅 [Audience Activation](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html).
