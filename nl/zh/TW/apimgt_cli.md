---



copyright:

  years: 2017
lastupdated: "2017-06-26"

---


{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}

# Bluemix API Management 指令
{: #apimgt_cli}

版本：1.0.0

您可以安裝 {{site.data.keyword.Bluemix_notm}} API Management 指令行介面 (CLI) 外掛程式，使用 Scripting 針對您的 API 完成一般管理動作。下列資訊列出附於 API Management CLI 外掛程式的指令，包括其名稱、選項、用法、必要條件、說明及範例。
{:shortdesc}

**附註：** **必要條件**列出使用該指令之前所需的動作。沒有必要動作的指令會列出**無**。否則，必要條件可能包括下列一個以上的動作：

**附註：** 您可以使用簡短格式的 Bluemix 指令；例如，`bx apim` 為 `bluemix apim` 的簡短格式。

使用下表中的索引來參照經常使用的 API Management 指令。

<table summary="API Management 指令。">
<caption>表格 1. API Management 指令</caption>
 <thead>
 <th colspan="5">API Management 指令</th>
 </thead>
 <tbody>
 <tr>
 <td>[bluemix apim help](apimgt_cli.html#apim_help)</td>
 <td>[bluemix apim api](apimgt_cli.html#apim_api)</td>
 <td>[bluemix apim apis](apimgt_cli.html#apim_apis)</td>
 <td>[bluemix apim api-create](apimgt_cli.html#apim_api-create)</td>
 <td>[bluemix apim api-delete](apimgt_cli.html#apim_api-delete)</td>
 <td>[bluemix apim api-expose](apimgt_cli.html#apim_api-expose)</td>
 <td>[bluemix apim api-share](apimgt_cli.html#apim_api-share)</td>
 <td>[bluemix apim api-unexpose](apimgt_cli.html#apim_api-unexpose)</td>
 <td>[bluemix apim api-unshare](apimgt_cli.html#apim_api-unshare)</td>
 <td>[bluemix apim api-update](apimgt_cli.html#apim_api-update)</td>
 <td>[bluemix apim keys](apimgt_cli.html#apim_keys)</td>
 </tr>
 </tbody>
 </table>
 
  
## API Management 說明
{: #apim_help}
顯示 API Management CLI 第一層內建指令及受支援名稱空間的一般說明，或者特定內建指令或名稱空間的說明。

### 語法

```
bluemix apim help <object-action>
```
{: codeblock}

### 指令選項

   <dl>
   <dt>object-action（選用）</dt>
   <dd>顯示說明的指令。若未指定，則會顯示 API Management CLI 的一般說明。</dd>
   </dl>

### 範例

顯示 API Management CLI 的一般說明：

```
bluemix apim help
```

顯示 `api-create` 指令的說明：

```
bluemix apim help api-create
```



## bluemix apim api
{: #apim_api}
顯示受管理 API 的內容。

### 語法
```
bluemix apim api --name <API_NAME> [--swagger]
```
{: codeblock}

### 必要旗標
   <dl>
   <dt>--name</dt>
   <dd>指定受管理 API 的名稱</dd>
   </dl>


### 指令選項
   <dl>
   <dt>--swagger</dt>
   <dd>在輸出中顯示 Open API 定義文件中的資訊</dd>
   </dl>

### 輸出

此指令會輸出列出有關指定 API 的下列資訊的表格：

   <dl>
     <dt>名稱</dt>
	 <dd>API 的名稱。</dd>
	 <dt>類型</dt>
	 <dd>API 的類型。有效的項目為 <em>whisk</em>、<em>cf-apps</em> 或 <em>user-defined</em></dd>
	 <dt>受管理</dt>
	 <dd>若值為 true 時，則表示該端點已發現，但未在閘道上公開。</dd>
	 <dt>已公開</dt>
	 <dd>指出 API 在閘道上是作用中的 (<em>true</em>)，還是非作用中的 (<em>false</em>)。
	 <dt>共用</dt>
	 <dd>指出 API 在您的 Bluemix 組織之外是共用的 (<em>true</em>)，還是非共用的 (<em>false</em>)。</dd>
	 <dt>受管理 URL</dt>
	 <dd>指定共用版 API 的位置。</dd>
   </dl>

   
### 範例

顯示名為 cloudfound1 之 API 的內容：

```
bluemix apim api cloudfound1
```

顯示名為 api2 之 API 的內容及定義檔內容：

```
bluemix apim api api2 --swagger
```


## bluemix apim apis
{: #apim_apis}


列出在已識別的端點伺服器上可用且識別的 API。

### 語法
```
bluemix apim apis [--api-provider <API_PROVIDER>][--exposed][--shared]
```
{: codeblock}

### 指令選項

附註：若未指定任何選項，則會傳回所有 API 的資訊。
   <dl>
   <dt>--api-provider </dt>
   <dd>只會傳回您在此指定的 API 類型。有效的選項為 <em>whisk</em>（若為 Openwhisk API）、<em>cf-apps</em>（若為 Cloud Foundry 應用程式 API），以及 <em>user-defined</em>（若為未與 Openwhisk 或 Cloud Foundry 相關聯的 API）。</dd>
   <dt>--exposed</dt>
   <dd>只會傳回公開的 API。</dd>
   <dt>--shared</dt>
   <dd>只會傳回在您的 {{site.data.keyword.Bluemix_notm}} 組織之外共用的 API。</dd>
   </dl>

### 輸出

此指令會輸出列出有關指定 API 的下列資訊的表格：

   <dl>
     <dt>名稱</dt>
	 <dd>API 的名稱。</dd>
	 <dt>類型</dt>
	 <dd>API 的類型。有效的項目為 <em>whisk</em>、<em>cf-apps</em> 或 <em>user-defined</em></dd>
	 <dt>受管理</dt>
	 <dd>若值為 true 時，則表示該端點已發現，但未在閘道上公開。</dd>
	 <dt>已公開</dt>
	 <dd>指出 API 在閘道上是作用中的 (<em>true</em>)，還是非作用中的 (<em>false</em>)。
	 <dt>共用</dt>
	 <dd>指出 API 在您的 Bluemix 組織之外是共用的 (<em>true</em>)，還是非共用的 (<em>false</em>)。</dd>
	 <dt>受管理 URL</dt>
	 <dd>指定共用版 API 的位置（若該 API 已公開）。若該 API 未公開，則值為 <em>undefined</em>。</dd>
   </dl>


### 範例

傳回端點管理程式上可用的所有 API：

```
bluemix apim apis 
```

傳回可用的所有 OpenWhisk API：

```
bluemix apim apis --api-provider whisk
```

## bluemix apim api-create
{: #apim_api-create}


透過匯入其 Swagger 檔案，將現有的未受管理 API 變為受管理 API。

### 語法

```
bluemix apim api-create --name <API_NAME> --file <PATH_TO_OPEN_API_DEFINITION_FILE> --provider cf-apps [--expose]
```
{: codeblock}

### 必要旗標

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>指定您要管理的 API 名稱。</dd>
   <dt>--file</dt>
   <dd>提供 Open API 定義檔（YAML 或 JSON 格式）的路徑。</dd>
   <dt>--provider</dt>
   <dd>指定您正在建立的 API 類型。附註：這個的唯一有效項目為 <em>cf-apps</em>。
   </dl>

### 指令選項

   <dl>
   <dt>--expose</dt>
   <dd>在建立端點之後自動公開該端點。</dd>
   </dl>

### 輸出

此指令輸出下列資訊：
* 已順利建立
* 錯誤（含錯誤的說明）

### 範例

管理名為 apinumber1 且具有名為 reservations1 之 yaml 定義檔的 Cloud Foundry API：

```
bluemix apim api-create --name apinumber1 --file ~/dev/apis/reservations1.yaml --provider cf-apps
```

管理稱為 cfapi 且具有名為 definition1 之 json 定義檔的 Cloud Foundry 應用程式：

```
bluemix apim api-create --name cfapi --file ~/dev/apis/definition1.json --provider cf-apps
```

## bluemix apim api-delete
{: #apim_api-delete}

從資料庫移除受管理 API。

### 語法

```
bluemix apim api-delete --name <API_NAME> --confirm
```
{: codeblock}

### 必要旗標

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>指定您要刪除的 API 名稱。**重要事項：** 刪除 Cloud Foundry API 會從受管理狀態移除 API，但不會刪除 Cloud Foundry 應用程式。刪除 OpenWhisk API 會刪除整個 API，且必須在刪除它之後重新加以建立。</dd>
   <dt>--confirm</dt>
   <dd>確認指令應在未提供確認提示的情況下完成。</dd>
   </dl>


### 輸出

此指令輸出下列資訊：
* 已順利刪除
* 錯誤（含錯誤的說明）

### 範例

刪除 Cloud Foundry API cloudapi1：

```
bluemix apim api-delete --name cloudapi1 --confirm
```


## bluemix apim api-expose
{: #apim_api-expose}

讓受管理 API 可以被我的 {{site.data.keyword.Bluemix_notm}} 組織內的其他人看到。

### 語法
```
bluemix apim api-expose --name <API_NAME>
```
{: codeblock}

### 必要旗標

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>指定您要公開的 API 名稱。</dd>
   </dl>

### 輸出

此指令輸出下列資訊：
* 已順利公開
* 錯誤（含錯誤的說明）

### 範例

使用我的 {{site.data.keyword.Bluemix_notm}} 組織公開名為 cloudfound1 的 Cloud Foundry API：

```
bluemix apim api-expose --name cloudfound1
```


## bluemix apim api-share
{: #apim_api-share}


讓受管理 API 可以被我的 {{site.data.keyword.Bluemix_notm}} 組織外的其他人看到。

### 語法
```
bluemix apim api-share --name <API_NAME>
```
{: codeblock}

### 必要旗標

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>指定您要共用的 API 名稱。</dd>
   </dl>

### 輸出

此指令輸出下列資訊：
* 已順利共用
* 錯誤（含錯誤的說明）

### 範例

在我的 {{site.data.keyword.Bluemix_notm}} 組織之外共用名為 cloudfound1 的 Cloud Foundry API：
```
bluemix apim api-share --name cloudfound1
```


## bluemix apim api-unexpose
{: #apim_api-unexpose}


讓可被 {{site.data.keyword.Bluemix_notm}} 組織內其他人看到的受管理 API 不再被其他人看到。

### 語法
```
bluemix apim api-unexpose --name <API_NAME>
```
{: codeblock}

### 必要旗標

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>指定您要從 {{site.data.keyword.Bluemix_notm}} 組織中其他人可以看到之處移除的 API 名稱。</dd>
   </dl>

### 輸出

此指令輸出下列資訊：
* 已順利未公開
* 錯誤（含錯誤的說明）

### 範例

從我的 {{site.data.keyword.Bluemix_notm}} 組織的其他成員的視圖移除名為 openwhisk1 的 OpenWhisk API：

```
bluemix apim api-unexpose --name openwhisk1
```


## bluemix apim api-unshare
{: #apim_api-unshare}


從可見之處移除可以被我的 {{site.data.keyword.Bluemix_notm}} 組織外的其他人看到的受管理 API。

### 語法
```
bluemix apim api-unshare --name <API_NAME>
```
{: codeblock}

<strong>必要標示</strong>：

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>指定您要停止共用的 API 名稱。</dd>
   </dl>

### 輸出

此指令輸出下列資訊：
* 已順利解除共用
* 錯誤（含錯誤的說明）

### 範例

在我的 {{site.data.keyword.Bluemix_notm}} 組織之外停止共用名為 cloudfound1 的 Cloud Foundry API：

```
bluemix apim api-unshare --name cloudfound1
```



## bluemix apim api-update
{: #apim_api-update}


透過取代其定義檔來更新受管理 API 的設定。重要事項：這是將 API 中的現有定義完全取代為新檔中的定義。會從定義中移除現有檔案中存在之新檔中的任何空項目或遺漏項目。

### 語法
```
bluemix apim api-update --name <API_NAME> --file <NEW_OPEN_API_DEFINITION_FILE>
```
{: codeblock}

### 必要旗標

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>指定您要更新的 API 名稱。</dd>
   <dt>--file</dt>
   <dd>提供取代 Open API 定義檔（YAML 或 JSON 格式）的路徑。</dd>
   </dl>

### 輸出

此指令輸出下列資訊：
* 已順利更新
* 錯誤（含錯誤的說明）


### 範例

使用名稱為 definition1.json 的定義檔來更新名為 whiskapi1 的 OpenWhisk API：

```
bluemix apim api-update --name whiskapi1 --filePath ~/path/definitions/definition1.json
```


## bluemix apim keys
{: #apim_api-keys}


顯示與受管理 API 相關聯的金鑰內容。

### 語法
```
bluemix apim api-keys --name <API_NAME> --bluemix|--external
```
{: codeblock}

### 必要旗標

   <dl>
   <dt>--name <i>API_NAME</i></dt>
   <dd>指定您要公開的 API 名稱。</dd>
   <dt>--bluemix</dt>
   <dd>列出指定 API 的 {{site.data.keyword.Bluemix_notm}} API 金鑰。</dd>
   <dt>--external</dt>
   <dd>列出指定 API 的外部 API 金鑰。</dd>
   </dl>

### 輸出

指令會輸出列出有關指定 API 的下列資訊的表格：


   <dl>
     <dt>金鑰名稱</dt>
	 <dd>API 金鑰的名稱。</dd>
	 <dt>金鑰類型</dt>
	 <dd>API 金鑰的類型。有效的項目為 <em>bluemix</em> 及 <em>external</em>。</dd>
	 <dt>用戶端 ID</dt>
	 <dd>使用金鑰識別的用戶端名稱。</dd>
	 <dt>提供的密碼</dt>
	 <dd>指出是否為 API 提供 API 密碼。可能值為 <em>true</em>（若有密碼時），以及 <em>false</em>（若沒有密碼時）。
   </dl>


### 範例

傳回與名為 cloudfound1 之 API 相關聯的所有外部金鑰。

```
bluemix apim --name cloudfound1 --external
```

傳回容許我的 {{site.data.keyword.Bluemix_notm}} 組織內的人員可以看到我的 myapi1 API 的金鑰。

```
bluemix apim --name myapi1 --bluemix 
```
 
