---

copyright:
  years: 2017
lastupdated: "2017-07-25"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 使用 API Management CLI 运行命令
{: #apim-cli-over}

您可以使用 {{site.data.keyword.Bluemix_notm}} API Management CLI 通过命令行来完成可以使用 {{site.data.keyword.Bluemix_notm}} 图形用户界面完成的一些相同任务。这些命令可以在终端窗口中单独输入，也可以在脚本中按顺序调用。
{:shortdesc}

## 先决条件
{: #apim-cli-script-prereq}

要能够使用 API Management CLI，您必须已完成以下步骤：

* 获取 [Bluemix 标识](../../admin/adminpublic.html#signing-up-for-bluemix){: new_window}。 
* 下载并安装 [Bluemix 命令行](../../cli/reference/bluemix_cli/index.html#getting-started){: new_window}。
* 安装 {{site.data.keyword.Bluemix_notm}} [API Management 命令行插件](../../cli/reference/bluemix_cli/index.html#install_plug-in){: new_window}。
* [登录](../../cli/reference/bluemix_cli/bx_cli.html){: new_window}到 {{site.data.keyword.Bluemix_notm}} 命令行。

## API 的样本 CLI 命令序列

以下步骤演示了从向 API 添加网关到从 API 中除去网关的一整套 API Management 命令：

1. 登录到 {{site.data.keyword.Bluemix_notm}} 
    ```
    bluemix login -a https://api.ng.bluemix.net -c account_ID (1) -u username -p password
    ```
    {:codeblock}
    使用命令行界面登录到您的缺省 {{site.data.keyword.Bluemix_notm}} 组织。

2. 显示 API
    ```
    bluemix apim apis
    ```
    {:codeblock}
    显示缺省组织中的 API。

3. 创建 API
    ```
    bluemix apim api-create --name <API_NAME> --file <path_to_Swagger_file>
    ```
    {:codeblock}
    使用 Swagger 文件通过您在 {{site.data.keyword.Bluemix_notm}} 组织中指定的 API 创建受管 API。

4. 更新现有 API 定义
    ```
    bluemix apim api-update --name <API_NAME> --file <path_to_new_Swagger_file>
    ```
    {:codeblock}
    使用新的 Swagger 文件定义替换指定的 API 的现有定义。

5. 公开 API
    ```
    bluemix apim api-expose --name <API_NAME>
    ```
    {:codeblock}
    公开 API。

6. 共享 API
    ```
    bluemix apim api-share --name <API_NAME>
    ```
    {:codeblock}
    与 {{site.data.keyword.Bluemix_notm}} 组织外部的其他人共享 API。

7. 停止公开 API
    ```
    bluemix apim api-unexpose --name <API_NAME>
    ```
    {:codeblock}
    停止在 {{site.data.keyword.Bluemix_notm}} 组织外部共享 API。

8. 显示 API 的密钥
    ```
    bluemix apim keys --name <API_NAME>
    ```
    {:codeblock}
    显示与 API 关联的密钥（如有）。

9. 停止共享 API
    ```
    bluemix apim api-unshare --name <API_NAME>
    ```
    {:codeblock}
    停止共享 API。
	
10. 除去 API
    ```
    bluemix apim api-delete --name <API_NAME>
    ```
    {:codeblock}
    从 API 中除去网关。系统不再对其进行管理。
    重要信息：如果删除 Cloud Foundry API，基本 Cloud Foundry 应用程序仍会保留在 {{site.data.keyword.Bluemix_notm}} 服务中，但不再对其进行管理。删除的 OpenWhisk API 会除去各个 OpenWhisk 操作之间的所有交互。在删除 OpenWhisk API 后，如果想再次使用该 API，必须加以重新创建。
    
有关 API Management 命令及其选项的完整列表，请参阅[命令行界面命令](../../cli/plugins/api-management-cliplugin/index.html)。

