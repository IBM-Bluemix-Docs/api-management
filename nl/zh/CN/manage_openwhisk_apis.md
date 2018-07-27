---

copyright:
  years: 2017,2018
lastupdated: "2018-01-11"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 通过 {{site.data.keyword.openwhisk_short}} 操作创建 API
{: #manage_openwhisk_apis}

{{site.data.keyword.openwhisk_short}} 操作可通过由 API Management 进行管理而受益。

使用 API Management，可以将 {{site.data.keyword.openwhisk_short}} 操作作为 API 公开。定义 API 后，可以应用安全性和速率限制策略，查看 API 使用情况和响应日志，以及定义 API 共享策略。  

要创建 {{site.data.keyword.openwhisk_short}} API，请完成以下步骤：

1. 在 {{site.data.keyword.openwhisk_short}}“仪表板”中，单击 **API** 选项卡。如果已经创建了 {{site.data.keyword.openwhisk_short}} API，那么会显示 {{site.data.keyword.openwhisk_short}} API 的列表。如果您还没有任何 {{site.data.keyword.openwhisk_short}} API，那么会显示“开始使用”屏幕。 
2. 单击**创建 {{site.data.keyword.openwhisk_short}} API**。这将显示“创建 {{site.data.keyword.openwhisk_short}} API”窗口。 
3. 填写“API 信息”部分中的字段，然后单击**创建操作**。这将显示“创建操作”窗口。可创建用于为 API 定义端点、HTTPS 路径和方法的操作。
4. 在“创建操作”窗口中，填写 {{site.data.keyword.openwhisk_short}} 操作的必填字段。包含在“创建操作”窗口中的字段包括以下字段：

    * 路径 - API 所在的路径。 
    * 动词 - API 的 HTTP 方法。请从以下方法中进行选择：
	    * DELETE
		* GET
		* HEAD
		* OPTIONS
		* PATCH
		* POST
		* PUT
	* 包含操作的程序包 - 组织中现有可用的程序包，可能包含要用于此 API 的操作。有关此字段的更多信息，请参阅[使用和创建 Cloud Functions 程序包](../openwhisk/openwhisk_packages.html)。
	* 操作 - **{{site.data.keyword.Bluemix_notm}} 中提供的操作**是唯一可用的选项。
	* 响应内容类型 - 这可识别 API 返回信息的格式。您可以从以下格式中进行选择：
	    * application/json - 这是缺省格式，也是最常用的格式。
		* text/html - 该格式用于在 Web 站点上使用的响应。
		* text/plain - 该格式以纯文本提供，可在以逗号分隔的值文件中使用。
		* image/svg+xml - 当截屏是主要响应格式时，可以使用该格式。
		* 使用来自操作的“Content-Type”头 - 该格式取决于响应头中的内容类型。 
	
5. 选择**创建**以创建操作。该操作将添加到用于调用 {{site.data.keyword.openwhisk_short}} 操作表的“操作”中。
5. 填写您希望填写的其余信息。也可以日后管理 API 时添加或更新其余信息。
6. 单击**保存**。这将打开 API 的“API Management 概述”页面，并且显示刚才定义的所有信息。
7. 继续使用[管理 API](manage_apis.html) 来管理 API。
