---

copyright:
  years: 2017, 2018
lastupdated: "2018-06-26"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 存取其他 API Management 特性
{: #upgrade}

{{site.data.keyword.Bluemix}} API 所提供的 API 管理功能可讓您有限地控制呼叫率、OAuth 及視圖分析。升級為 {{site.data.keyword.apiconnect_full}} 服務，就可以具有 API 的更高管理控制權。{{site.data.keyword.apiconnect_short}} 服務提供更多安全原則選項，並且具有比率限制的更高控制權。除此之外，您將可以配置完整可自訂的「開發人員入口網站」以將 API 社交化，並使用開發人員社群。其他好處包括：
* 生命週期管理
* 複合 API
* Web 服務整合
* 通訊協定調解
* 從綱目產生 API
* 微服務開發

移轉至 {{site.data.keyword.apiconnect_short}} 服務十分簡單，而且您不需要重建任何使用 API Management 所管理的 API。您可以自動或手動移轉 API。

## 自動將 API 移轉至 {{site.data.keyword.apiconnect_short}}
{: #auto_migrate_api}

如果您決定升級至 {{site.data.keyword.apiconnect_short}}，則需要針對所移轉的 API 類型選取並完成下列程序，以將 API 從 API Management 移轉至 {{site.data.keyword.apiconnect_short}} 服務。


### Cloud Functions API

1. 選取 {{site.data.keyword.Bluemix_notm}} 功能表中的**函數**，以檢視您的 Cloud Functions。

2. 在「函數」清單中，選取導覽中的 **API**。

3. 選取您要移轉的「函數 API」名稱。

4. 在導覽中，選取**定義**。

5. 在「API 定義檔」區段中，選取 **API 定義檔** > **在 API Connect 開啟** > **繼續**。若您已有現有的 {{site.data.keyword.apiconnect_short}} 服務，則它會自動將 API 移轉為現有的服務。如果您還未配置 {{site.data.keyword.apiconnect_short}} 服務，則它會自動使用免費的 Lite 方案來新增服務並移轉 API。如果您的實例無法佈建，請完成[手動將 API 移轉為 {{site.data.keyword.apiconnect_short}}](#man_migrate_api) 中的步驟，以手動將其移轉為新的服務。 

6. 關閉原始 API 的畫面之前，請停用**公開受管理 API** 的調節器。這可以防止任何人作用於舊版本的端點。

### Cloud Foundry API

1. 在「{{site.data.keyword.Bluemix_notm}} 儀表板」中，開啟您的現有 Cloud Foundry API 來源。 

2. 選取導覽功能表中的 **API Management**。

3. 在導覽中，選取**定義**。

4. 選取 **API 定義檔** > **在 API Connect 開啟** > **繼續**。若您已有現有的 {{site.data.keyword.apiconnect_short}} 服務，則它會自動將 API 移轉為現有的服務。如果您還未配置 {{site.data.keyword.apiconnect_short}} 服務，則它會自動使用免費的 Lite 方案來新增服務並移轉 API。如果您的實例無法佈建，請完成[手動將 API 移轉為 {{site.data.keyword.apiconnect_short}}](#man_migrate_api) 中的步驟，以手動將其移轉為新的服務。
   
5. 在已將內容移轉為 {{site.data.keyword.apiconnect_short}} 實例之後，請選取所提供的鏈結來存取已移轉的版本。
    **重要事項：** 為了防止多個 API 實例執行發生問題，請確定在原始的 API 版本中停用*管理 API* 調節器。

6. 在導覽中，選取 **API** 標籤。

7. 選取**草稿**，以檢視您的新 API。

## 手動將 API 移轉至 {{site.data.keyword.apiconnect_short}}
{: #man_migrate_api}

若將 API 移轉至 {{site.data.keyword.apiconnect_short}} 服務的過程未正確地完成，請完成下列步驟來手動移轉它：

1. 開啟您的 API。
	1. 登入 {{site.data.keyword.Bluemix_notm}}。
	2. 若為 Cloud Foundry 應用程式： 
		1. 選取功能表中的**儀表板**。
		2. 選取您要移轉的 Cloud Foundry 應用程式名稱。
		3. 選取導覽中的 **API Management**。
	3. 若為 Cloud Functions 動作： 
		1. 選取功能表中的**函數**。
		2. 在導覽中，選取 **API**。
		3. 選取您要移轉的 API 名稱。
2. 從 API Management 下載 API 的 Swagger 文件。
    1. 在導覽中，選取**定義**。
	2. 選取 **API 定義檔**。
    3. 根據您的檔案類型，選取**匯出 YAML** 或**匯出 JSON**，以下載 API 的定義。檔案會下載到您的下載資料夾。
3. 建立及準備 {{site.data.keyword.apiconnect_short}} 實例。 
	1. 移至導覽中的 **API**，以過濾服務。
	2. 選取 API Connect 服務。 
    3. 從 {{site.data.keyword.Bluemix_notm}} 型錄中，建立 {{site.data.keyword.apiconnect_short}} 服務的實例。
	4. 選取方案。Lite 方案是免費的選項。
	5. 選取**建立**，以建立實例。
4. 完成下列步驟，以將 Swagger 文件匯入至 {{site.data.keyword.apiconnect_short}} 實例：
	1. 從 {{site.data.keyword.apiconnect_short}} 服務儀表板中，選取功能表中的**導覽至... (>>)** > **草稿**。
	2. 選取 API 標籤。
	3. 選取 **+新增** > **從檔案或 URL 匯入 API**。
	4. 尋找並選取您已從 API Management 下載的 Swagger 檔案。選取**開啟**。
	5. 選取**匯入**，以將 API 匯入至 {{site.data.keyword.apiconnect_short}} 服務。
5. 為了防止因執行多個 API 實例所導致的問題，請確定在原始的 API 版本中停用*管理 API* 調節器。

您的 API 可在 {{site.data.keyword.apiconnect_short}} 服務實例中取得。 

## 發佈 API

您可以透過完成下列步驟來繼續發佈 API：

1. 建立「型錄」。
	1. 選取 **+新增**，以建立型錄。
	2. 輸入型錄的「顯示名稱」及名稱，然後選取**新增**。
	3. 選取您已建立的型錄。
2. 指定 API 的設定。
    1. 選取**建立產品**。
	2. 指定產品的名稱。
	2. 選取您已建立來檢視其設定的產品。
	3. 設定 API 的比率限制。
	4. 設定 API 的層級。
3. 新增 API 的端點（必要的話）。
    1. 選取 API。
	2. 選取「組合」標籤。
	3. 新增端點（如果尚未指定）。
	
 在您移轉 API 之後，可以存取所有 API Management 特性，方法是開啟 {{site.data.keyword.apiconnect_short}} 服務磚，以及透過「{{site.data.keyword.Bluemix_notm}} 儀表板」。
 

