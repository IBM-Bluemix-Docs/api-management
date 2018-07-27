---



copyright:

  years: 2017
lastupdated: "2017-06-26"

---


{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}

# Bluemix API Management コマンド
{: #apimgt_cli}

バージョン: 1.0.0

{{site.data.keyword.Bluemix_notm}} API Management コマンド・ライン・インターフェース (CLI) プラグインをインストールすると、スクリプトによって API に対して一般的な管理アクションを実行できます。以下の情報では、API Management CLI プラグインに含まれるコマンドを、名前、オプション、使用法、前提条件、説明、および例を含めてリストします。
{:shortdesc}

**注:** **前提条件**には、コマンドを使用する前に必要なアクションがリストされています。前提条件となるアクションのないコマンドでは、**なし**とリストされています。それ以外の場合、前提条件には以下のアクションのうちの 1 つ以上が含まれます。

**注:** 短形式の Bluemix コマンドを使用できます。例えば、`bx apim` は `bluemix apim` の短形式です。

以下の表の索引を使用して、使用頻度の高い API Management コマンドを参照してください。

<table summary="API Management コマンド">
<caption>表 1. API Management コマンド</caption>
 <thead>
 <th colspan="5">API Management コマンド</th>
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
 
  
## API Management ヘルプ
{: #apim_help}
API Management CLI の第 1 レベルの組み込みコマンドとサポートされている名前空間に関する一般ヘルプ、または特定の組み込みコマンドもしくは名前空間に関するヘルプを表示します。

### 構文

```
bluemix apim help <object-action>
```
{: codeblock}

### コマンド・オプション

   <dl>
   <dt>object-action (オプション)</dt>
   <dd>ヘルプを表示する対象のコマンド。指定しない場合は、API Management CLI の一般ヘルプが表示されます。</dd>
   </dl>

### 例

以下は、API Management CLI の一般ヘルプを表示します。

```
bluemix apim help
```

以下は、`api-create` コマンドのヘルプを表示します。

```
bluemix apim help api-create
```



## bluemix apim api
{: #apim_api}
管理対象 API のプロパティーを表示します。

### 構文
```
bluemix apim api --name <API_NAME> [--swagger]
```
{: codeblock}

### 必須フラグ
   <dl>
   <dt>--name</dt>
   <dd>管理対象 API の名前を指定します。</dd>
   </dl>


### コマンド・オプション
   <dl>
   <dt>--swagger</dt>
   <dd>Open API 定義文書からの情報を出力に表示します。</dd>
   </dl>

### 出力

このコマンドは、指定された API に関して以下の情報をリストするテーブルを出力します。

   <dl>
     <dt>Name</dt>
	 <dd>API の名前。</dd>
	 <dt>Type</dt>
	 <dd>API のタイプ。有効なエントリーは、<em>whisk</em>、<em>cf-apps</em>、または <em>user-defined</em> です。</dd>
	 <dt>Managed</dt>
	 <dd>値が true である場合、エンドポイントが検出されたが、ゲートウェイで公開されていないことを示します。</dd>
	 <dt>Exposed</dt>
	 <dd>API がゲートウェイでライブであるか (<em>true</em>)、ライブではないか (<em>false</em>) を示します。
	 <dt>Shared</dt>
	 <dd>API が Bluemix 組織の外部で共有されているか (<em>true</em>)、共有されていないか (<em>false</em>) を示します。</dd>
	 <dt>Managed URL</dt>
	 <dd>API の共有バージョンのロケーションを示します。</dd>
   </dl>

   
### 例

以下は、cloudfound1 という名前の API のプロパティーを表示します。

```
bluemix apim api cloudfound1
```

以下は、api2 という API のプロパティーおよび定義ファイルの内容を表示します。

```
bluemix apim api api2 --swagger
```


## bluemix apim apis
{: #apim_apis}


識別されたエンドポイント・サーバー上で識別された使用可能な API をリストします。

### 構文
```
bluemix apim apis [--api-provider <API_PROVIDER>][--exposed][--shared]
```
{: codeblock}

### コマンド・オプション

注: オプションが指定されない場合、すべての API の情報が返されます。
   <dl>
   <dt>--api-provider </dt>
   <dd>ここで指定したタイプの API のみを返します。有効なオプションは、<em>whisk</em> (Openwhisk API)、<em>cf-apps</em> (Cloud Foundry アプリ API)、および <em>user-defined</em> (Openwhisk にも Cloud Foundry にも関連付けられていない API) です。</dd>
   <dt>--exposed</dt>
   <dd>公開されている API のみを返します。</dd>
   <dt>--shared</dt>
   <dd> {{site.data.keyword.Bluemix_notm}} 組織の外部で共有されている API のみを返します。</dd>
   </dl>

### 出力

このコマンドは、指定された API に関して以下の情報をリストするテーブルを出力します。

   <dl>
     <dt>Name</dt>
	 <dd>API の名前。</dd>
	 <dt>Type</dt>
	 <dd>API のタイプ。有効なエントリーは、<em>whisk</em>、<em>cf-apps</em>、または <em>user-defined</em> です。</dd>
	 <dt>Managed</dt>
	 <dd>値が true である場合、エンドポイントが検出されたが、ゲートウェイで公開されていないことを示します。</dd>
	 <dt>Exposed</dt>
	 <dd>API がゲートウェイでライブであるか (<em>true</em>)、ライブではないか (<em>false</em>) を示します。
	 <dt>Shared</dt>
	 <dd>API が Bluemix 組織外で共有されているか (<em>true</em>)、共有されていないか (<em>false</em>) を示します。</dd>
	 <dt>Managed URL</dt>
	 <dd>API が公開されている場合、API の共有バージョンのロケーションを示します。API が公開されていない場合、値は <em>undefined</em> です。</dd>
   </dl>


### 例

以下は、エンドポイント・マネージャーで使用可能なすべての API を返します。

```
bluemix apim apis 
```

以下は、使用可能なすべての OpenWhisk API を返します。

```
bluemix apim apis --api-provider whisk
```

## bluemix apim api-create
{: #apim_api-create}


既存の非管理対象 API を、その Swagger ファイルをインポートすることによって管理対象 API にします。

### 構文

```
bluemix apim api-create --name <API_NAME> --file <PATH_TO_OPEN_API_DEFINITION_FILE> --provider cf-apps [--expose]
```
{: codeblock}

### 必須フラグ

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>管理する API の名前を指定します。</dd>
   <dt>--file</dt>
   <dd>Open API 定義ファイル (YAML 形式 または JSON 形式) へのパスを指定します。</dd>
   <dt>--provider</dt>
   <dd>作成する API のタイプを指定します。注: ここでは <em>cf-apps</em> が唯一の有効なエントリーです。
   </dl>

### コマンド・オプション

   <dl>
   <dt>--expose</dt>
   <dd>エンドポイントを作成した後に、自動的に公開します。</dd>
   </dl>

### 出力

このコマンドによって、以下の情報が出力されます。
* 正常に作成されました
* エラー (およびエラーの説明)

### 例

以下で、reservations1 という yaml 定義ファイルを持つ、apinumber1 という名前の Cloud Foundry API を管理します。

```
bluemix apim api-create --name apinumber1 --file ~/dev/apis/reservations1.yaml --provider cf-apps
```

以下で、definition1 という json 定義ファイルを持つ、cfapi という Cloud Foundry アプリを管理します。

```
bluemix apim api-create --name cfapi --file ~/dev/apis/definition1.json --provider cf-apps
```

## bluemix apim api-delete
{: #apim_api-delete}

データベースから管理対象 API を削除します。

### 構文

```
bluemix apim api-delete --name <API_NAME> --confirm
```
{: codeblock}

### 必須フラグ

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>削除する API の名前を指定します。**重要:** Cloud Foundry API を削除すると、その API は管理対象状態ではなくなりますが、Cloud Foundry アプリは削除されません。OpenWhisk API を削除すると API 全体が削除され、削除後に再作成する必要があります。</dd>
   <dt>--confirm</dt>
   <dd>コマンドが確認プロンプトを出さずに完了する必要があることを確認します。</dd>
   </dl>


### 出力

このコマンドによって、以下の情報が出力されます。
* 正常に削除されました
* エラー (およびエラーの説明)

### 例

以下は、Cloud Foundry API cloudapi1 を削除します。

```
bluemix apim api-delete --name cloudapi1 --confirm
```


## bluemix apim api-expose
{: #apim_api-expose}

管理対象 API を、自分の {{site.data.keyword.Bluemix_notm}} 組織内の他のユーザーから見えるようにします。

### 構文
```
bluemix apim api-expose --name <API_NAME>
```
{: codeblock}

### 必須フラグ

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>公開する API の名前を指定します。</dd>
   </dl>

### 出力

このコマンドによって、以下の情報が出力されます。
* 正常に公開されました
* エラー (およびエラーの説明)

### 例

以下は、自分の {{site.data.keyword.Bluemix_notm}} 組織に cloudfound1 という Cloud Foundry API を公開します。

```
bluemix apim api-expose --name cloudfound1
```


## bluemix apim api-share
{: #apim_api-share}


管理対象 API を、自分の {{site.data.keyword.Bluemix_notm}} 組織の外部にいる他のユーザーから見えるようにします。

### 構文
```
bluemix apim api-share --name <API_NAME>
```
{: codeblock}

### 必須フラグ

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>共有する API の名前を指定します。</dd>
   </dl>

### 出力

このコマンドによって、以下の情報が出力されます。
* 正常に共有されました
* エラー (およびエラーの説明)

### 例

以下は、自分の {{site.data.keyword.Bluemix_notm}} 組織の外部で cloudfound1 という Cloud Foundry API を共有します。
```
bluemix apim api-share --name cloudfound1
```


## bluemix apim api-unexpose
{: #apim_api-unexpose}


自分の{{site.data.keyword.Bluemix_notm}} 組織内の他のユーザーに見えるようになっている管理対象 API を、他のユーザーから見えないようにします。

### 構文
```
bluemix apim api-unexpose --name <API_NAME>
```
{: codeblock}

### 必須フラグ

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>自分の {{site.data.keyword.Bluemix_notm}} 組織内の他のユーザーから見えないようにする API の名前を指定します。</dd>
   </dl>

### 出力

このコマンドによって、以下の情報が出力されます。
* 正常に非公開にしました
* エラー (およびエラーの説明)

### 例

openwhisk1 という OpenWhisk API を、自分の {{site.data.keyword.Bluemix_notm}} 組織の他のメンバーから見えないようにします。

```
bluemix apim api-unexpose --name openwhisk1
```


## bluemix apim api-unshare
{: #apim_api-unshare}


自分の{{site.data.keyword.Bluemix_notm}} 組織の外部にいる他のユーザーから見えている管理対象 API を、見えないようにします。

### 構文
```
bluemix apim api-unshare --name <API_NAME>
```
{: codeblock}

<strong>必須フラグ</strong>:

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>共有を停止する API の名前を指定します。</dd>
   </dl>

### 出力

このコマンドによって、以下の情報が出力されます。
* 正常に共有解除しました
* エラー (およびエラーの説明)

### 例

以下は、自分の {{site.data.keyword.Bluemix_notm}} 組織の外部で cloudfound1 という Cloud Foundry API の共有を停止します。

```
bluemix apim api-unshare --name cloudfound1
```



## bluemix apim api-update
{: #apim_api-update}


定義ファイルを置き換えることによって、管理対象 API の設定を更新します。重要: これで、API 内の既存の定義を、新規ファイルの定義で完全に置き換えることになります。既存のファイルに存在するが、新規ファイルで空であるか欠落している項目はすべて、定義から削除されます。

### 構文
```
bluemix apim api-update --name <API_NAME> --file <NEW_OPEN_API_DEFINITION_FILE>
```
{: codeblock}

### 必須フラグ

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>更新する API の名前を指定します。</dd>
   <dt>--file</dt>
   <dd>置き換わる Open API 定義ファイル (YAML 形式 または JSON 形式) へのパスを指定します。</dd>
   </dl>

### 出力

このコマンドによって、以下の情報が出力されます。
* 正常に更新されました
* エラー (およびエラーの説明)


### 例

以下で、whiskapi1 という OpenWhisk API を definition1.json という名前の定義ファイルで更新します。

```
bluemix apim api-update --name whiskapi1 --filePath ~/path/definitions/definition1.json
```


## bluemix apim keys
{: #apim_api-keys}


管理対象 API に関連付けられたキーのプロパティーを表示します。

### 構文
```
bluemix apim api-keys --name <API_NAME> --bluemix|--external
```
{: codeblock}

### 必須フラグ

   <dl>
   <dt>--name <i>API_NAME</i></dt>
   <dd>公開する API の名前を指定します。</dd>
   <dt>--bluemix</dt>
   <dd>指定された API の {{site.data.keyword.Bluemix_notm}} API キーをリストします。</dd>
   <dt>--external</dt>
   <dd>指定された API の外部 API キーをリストします。</dd>
   </dl>

### 出力

このコマンドは、指定された API に関して以下の情報をリストするテーブルを出力します。


   <dl>
     <dt>Key Name</dt>
	 <dd>API キーの名前。</dd>
	 <dt>Key Type</dt>
	 <dd>API キーのタイプ。有効なエントリーは、<em>bluemix</em> および <em>external</em> です。</dd>
	 <dt>Client ID</dt>
	 <dd>キーで識別されるクライアントの名前。</dd>
	 <dt>Secret Provided</dt>
	 <dd>当該 API に、API の秘密が提供されているかどうかを示します。可能な値は、<em>true</em> (秘密がある場合) および <em>false</em> (秘密がない場合) です。
   </dl>


### 例

cloudfound1 という名前の API に関連付けられた外部キーをすべて返します。

```
bluemix apim --name cloudfound1 --external
```

自分の{{site.data.keyword.Bluemix_notm}} 組織の内部にいるユーザーが myapi1 という名前の自分の API を見ることができるようにするキーを返します。

```
bluemix apim --name myapi1 --bluemix 
```
 
