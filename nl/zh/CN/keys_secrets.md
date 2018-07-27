---

copyright:
  years: 2017
lastupdated: "2017-11-09"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 管理密钥和私钥
{: #keys_secrets}

通过 API Management 来管理 API 时，您可以使用密钥和私钥来控制对 API 的访问权。

## 创建密钥和私钥
{: #create_key_secret}

要向 API 添加密钥，请完成以下步骤：

1. 打开 Cloud Foundry 应用程序或 OpenWhisk API（如果尚未打开）。

2. 在导航中选择 *API Management*。

3. 选择“共享和密钥”选项卡以访问该应用程序或 API 的密钥。*注：直到第一次保存应用程序或 API 时，才会看到这些选项卡。*

4. 确保**公开受管 API** 滑块设置为*开启*位置。必须公开 API 后，您才能分配密钥。

5. 为有权访问 {{site.data.keyword.Bluemix_notm}} 组织的客户创建密钥。
  1. 在*在 {{site.data.keyword.Bluemix_notm}} 组织内共享*部分中，选择**创建 API 密钥 +**。这将自动创建密钥和私钥并填入正确的字段中。您无法更新此密钥或此类型密钥的私钥。 
  2. 输入密钥和私钥的名称以帮助您识别。例如，输入将使用它的客户的名称。
  3. 选择**保存**以保存新密钥。
  4. 可以根据需要重复步骤 *a* 到 *c* 来添加更多密钥。在此部分中，每个 API 最多可以有 5 个密钥。

6. 为不属于 {{site.data.keyword.Bluemix_notm}} 组织的客户创建密钥。
  1. 在*在 {{site.data.keyword.Bluemix_notm}} 组织外部共享*部分中，选择**创建 API 密钥 +**。这将自动创建密钥并填入正确的字段中。此类型密钥初始不会显示任何私钥。您无法更新此密钥。 
  2. 输入密钥的名称以帮助您识别。例如，输入将使用它的客户的名称。
  3. 可选：如果要向密钥添加私钥，请针对要向其添加私钥的密钥，选择 **API 门户网站链接**，然后选择**设置 API 私钥**。
  4. 选择**保存**以保存新密钥。
  5. 可以根据需要重复步骤 *a* 到 *d* 来添加更多密钥。在此部分中，每个 API 最多可以有 5 个密钥。
在选择“共享和密钥”选项卡时，会列出用于 API 的密钥。

## 在 API 调用中指定密钥和私钥
{: #spec_key_secret}

仅当您的客户在调用头中包含正确的密钥和/或私钥时，才能调用 API。要调用 API，客户必须在 API 调用中包含密钥和私钥，如以下示例中所示：
```
curl --request PUT \
  --url https://appidtest.mybluemix.net/ \
  --header 'accept: application/json' \
  --header 'content-type: application/json' \
  --header 'x-ibm-client-secret: add_secret_here' \
  --data '{"id":999999999999999}'
```
{: codeblock}
其中，*add_secret_here* 将替换为正确密钥的私钥。 

## 删除 API 密钥
{: #delete_key}

在某些时候，您需要除去密钥。或许是使用您的 API 的客户创建了自己的 API，而不再需要您的 API。为了确保所有客户都不再使用您的 API，您可以删除相应密钥。要从服务中删除密钥，请完成以下步骤：

1. 打开 Cloud Foundry 应用程序或 OpenWhisk API（如果尚未打开）。

2. 在导航中选择 *API Management*。

3. 选择*共享和密钥*选项卡。

4. 找到要删除的密钥。提示：将密钥命名为容易识别的名称，此时就会很有用。

5. 选择要删除的密钥旁边的“选项”图标（三个垂直点）。 

6. 选择**删除密钥**。

7. 确认删除以除去密钥。
