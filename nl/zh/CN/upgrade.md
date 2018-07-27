---

copyright:
  years: 2017, 2018
lastupdated: "2018-01-10"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 访问更多 API Management 功能
{: #upgrade}

通过随 {{site.data.keyword.Bluemix}} API 一起提供的 API Management 功能，您可以对调用速率、OAuth 和视图分析进行有限的控制。您可通过升级到 {{site.data.keyword.apiconnect_full}} 服务，掌握对 API 的更大管理控制权。{{site.data.keyword.apiconnect_short}} 服务提供了安全策略的更多选项，以及对速率限制的更大控制权。除此之外，您还能配置完全可定制的开发者门户网站，这样您就可以对 API 进行社交化，并参与开发者社区。其他优势包括：
* 生命周期管理
* 组合 API
* Web Service 集成
* 协议调解
* 通过模式生成 API
* 微服务开发

迁移到 {{site.data.keyword.apiconnect_short}} 服务非常容易，您不必重新创建通过 API Management 管理的任何 API。您可以自动或手动迁移 API。

## 自动将 API 迁移到 {{site.data.keyword.apiconnect_short}}
{: #auto_migrate_api}

如果决定升级到 {{site.data.keyword.apiconnect_short}}，那么需要通过对要迁移的 API 类型选择并完成以下过程，从而将 API 从 API Management 迁移到 {{site.data.keyword.apiconnect_short}} 服务：

### Cloud Functions API

1. 在 {{site.data.keyword.Bluemix_notm}} 菜单中选择**功能**以查看 Cloud Functions。

2. 在“功能”列表的导航中，选择 **API**。

3. 选择要迁移的功能 API 的名称。

4. 在导航中选择**定义**。

5. 在 *API 定义文件*部分中，选择 **API 定义文件** > **导出到 API Connect** > **导出 API**。如果已经有现有的 {{site.data.keyword.apiconnect_short}} 服务，那么会自动将 API 迁移到现有服务。如果尚未配置 {{site.data.keyword.apiconnect_short}} 服务，那么会通过免费的轻量套餐自动添加该服务，然后迁移 API。如果实例供应失败，请完成[手动将 API 迁移到 {{site.data.keyword.apiconnect_short}}](#man_migrate_api) 中的步骤以手动将其迁移到新服务。 

6. 关闭原始 API 的屏幕之前，请禁用**公开受管 API** 滑块。这可以防止任何人对旧版本的端点执行操作。

### Cloud Foundry API

1. 在 {{site.data.keyword.Bluemix_notm}}“仪表板”中打开现有 Cloud Foundry API 源代码。 

2. 在导航菜单中选择 **API Management**。

3. 在导航中选择**定义**。

4. 选择 **API 定义文件** > **导出到 API Connect** > **导出 API**。如果已经有现有的 {{site.data.keyword.apiconnect_short}} 服务，那么会自动将 API 迁移到现有服务。如果尚未配置 {{site.data.keyword.apiconnect_short}} 服务，那么会通过免费的轻量套餐自动添加该服务，然后迁移 API。如果实例供应失败，请完成[手动将 API 迁移到 {{site.data.keyword.apiconnect_short}}](#man_migrate_api) 中的步骤以手动将其迁移到新服务。
   
5. 内容已迁移到 {{site.data.keyword.apiconnect_short}} 实例后，选择提供用于访问所迁移版本的链接。**重要信息：**为了防止运行 API 的多个实例出现问题，请确保在原始版本的 API 中禁用*管理 API* 滑块。

6. 在导航中选择 **API** 选项卡。

7. 选择**草稿**以查看新的 API。

## 手动将 API 迁移到 {{site.data.keyword.apiconnect_short}}
{: #man_migrate_api}

如果将 API 迁移到 {{site.data.keyword.apiconnect_short}} 服务的过程未正确完成，请完成以下步骤以手动进行迁移：

1. 打开 API。
	1. 登录到 {{site.data.keyword.Bluemix_notm}}。
	2. 对于 Cloud Foundry 应用程序： 
		1. 在“菜单”中选择**仪表板**。
		2. 选择要迁移的 Cloud Foundry 应用程序的名称。
		3. 在导航中选择 **API Management**。
	3. 对于 Cloud Functions 操作： 
		1. 在“菜单”中选择**功能**。
		2. 在导航中选择 **API**。
		3. 选择要迁移的 API 的名称。
2. 为 API Management 中的 API 下载 Swagger 文档。
    1. 在导航中选择**定义**。
	2. 选择 **API 定义文件**。
    3. 根据文件类型，选择**导出 YAML** 或**导出 JSON**，以下载 API 的定义。文件会下载到 downloads 文件夹中。
3. 创建并准备 {{site.data.keyword.apiconnect_short}} 实例。 
	1. 转至导航中的 **API** 以过滤服务。
	2. 选择 API Connect 服务。 
    3. 通过 {{site.data.keyword.Bluemix_notm}} 目录，创建 {{site.data.keyword.apiconnect_short}} 服务的实例。
	4. 选择套餐。轻量套餐是免费选项。
	5. 选择**创建**以创建实例。
4. 通过完成以下步骤，将 Swagger 文档导入到 {{site.data.keyword.apiconnect_short}} 实例：
	1. 在 {{site.data.keyword.apiconnect_short}} 服务仪表板中，选择菜单中的**浏览至...(>>)** > **草稿**。
	2. 选择 API 选项卡。
	3. 选择 **+添加** > **从文件或 URL 导入 API**。
	4. 找到并选择从 API Management 下载的 Swagger 文件。选择**打开**。
	5. 选择**导入**以将 API 导入到 {{site.data.keyword.apiconnect_short}} 服务。
5. 为了防止因运行 API 的多个实例而导致的问题，请确保在原始版本的 API 中禁用*管理 API* 滑块。

您的 API 在 {{site.data.keyword.apiconnect_short}} 服务实例中可用。 

## 发布 API

通过完成以下步骤，可以继续发布 API：

1. 创建目录。
	1. 选择 **+添加**以创建目录。
	2. 输入目录的显示名称和名称，然后选择**添加**。
	3. 选择已创建的目录。
2. 指定 API 的设置。
    1. 选择**创建产品**。
	2. 为产品指定名称。
	2. 选择已创建的产品以查看其设置。
	3. 为 API 设置速率限制。
	4. 为 API 设置层。
3. 根据需要，为 API 添加端点。
    1. 选择该 API。
	2. 选择“组合”选项卡。
	3. 添加端点（如果尚未指定）。
	
 迁移 API 后，您可以通过打开 {{site.data.keyword.apiconnect_short}} 服务磁贴以及通过 {{site.data.keyword.Bluemix_notm}}“仪表板”来访问所有 API Management 功能。 

