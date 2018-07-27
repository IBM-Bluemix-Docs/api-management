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

# 使用 API Management CLI 執行指令
{: #apim-cli-over}

您可以使用 {{site.data.keyword.Bluemix_notm}} API Management CLI，以指令行完成部分以 {{site.data.keyword.Bluemix_notm}} 圖形使用者介面可完成的相同作業。指令可以在終端機視窗中個別輸入，也可以在 Script 中按順序進行呼叫。
{:shortdesc}

## 必要條件
{: #apim-cli-script-prereq}

在可以使用 API Management CLI 之前，您必須已完成下列步驟：

* 取得 [Bluemix ID](../../admin/adminpublic.html#signing-up-for-bluemix){: new_window}。 
* 下載並安裝 [Bluemix 指令行](../../cli/reference/bluemix_cli/index.html#getting-started){: new_window}。
* 安裝 {{site.data.keyword.Bluemix_notm}} [API Management 指令行外掛程式](../../cli/reference/bluemix_cli/index.html#install_plug-in){: new_window}。
* [登入](../../cli/reference/bluemix_cli/bx_cli.html){: new_window}到 {{site.data.keyword.Bluemix_notm}} 指令行。

## API 指令的範例 CLI 序列

下列步驟示範從將閘道新增至 API 到從 API 中移除閘道的全程 API Management 指令：

1. 登入 {{site.data.keyword.Bluemix_notm}} 
    ```
    bluemix login -a https://api.ng.bluemix.net -c account_ID (1) -u username -p password
    ```
    {:codeblock}
    使用指令行介面將您登入您的預設 {{site.data.keyword.Bluemix_notm}} 組織。

2. 顯示您的 API
    ```
    bluemix apim apis
    ```
    {:codeblock}
    在您的預設組織中顯示 API。

3. 建立 API
    ```
    bluemix apim api-create --name <API_NAME> --file <path_to_Swagger_file>
    ```
    {:codeblock}
    使用 Swagger 檔案，從您在 {{site.data.keyword.Bluemix_notm}} 組織指定的 API 中建立受管理 API。

4. 更新現有 API 定義
    ```
    bluemix apim api-update --name <API_NAME> --file <path_to_new_Swagger_file>
    ```
    {:codeblock}
    取代您以新 Swagger 檔案定義指定之 API 的現有定義。

5. 公開 API
    ```
    bluemix apim api-expose --name <API_NAME>
    ```
    {:codeblock}
    公開 API。

6. 共用 API
    ```
    bluemix apim api-share --name <API_NAME>
    ```
    {:codeblock}
    與您的 {{site.data.keyword.Bluemix_notm}} 組織之外的其他人共用 API。

7. 停止公開 API
    ```
    bluemix apim api-unexpose --name <API_NAME>
    ```
    {:codeblock}
    停止在您的 {{site.data.keyword.Bluemix_notm}} 組織之外共用 API。

8. 顯示 API 的金鑰
    ```
    bluemix apim keys --name <API_NAME>
    ```
    {:codeblock}
    顯示與您的 API 相關聯的金鑰（若有任何的話）。

9. 停止共用 API
    ```
    bluemix apim api-unshare --name <API_NAME>
    ```
    {:codeblock}
    停止共用 API。
	
10. 移除 API
    ```
    bluemix apim api-delete --name <API_NAME>
    ```
    {:codeblock}
    從 API 移除閘道。它不再受管理。
    重要事項：若刪除 Cloud Foundry API，則基本 Cloud Foundry 應用程式會留在 {{site.data.keyword.Bluemix_notm}} 服務中，但是它不再受管理。遭刪除的 OpenWhisk API 會移除個別 OpenWhisk 動作之間的所有互動。刪除 OpenWhisk API 之後，如果您想再次使用它，則必須重新加以建立。
    
如需 API Management 指令及其選項的完整清單，請參閱[指令行介面指令](../../cli/plugins/api-management-cliplugin/index.html)。

