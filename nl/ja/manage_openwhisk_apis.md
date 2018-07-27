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

# {{site.data.keyword.openwhisk_short}} アクションからの API の作成
{: #manage_openwhisk_apis}

{{site.data.keyword.openwhisk_short}} アクションを API Management によって管理することでメリットがあります。

API Management を使用すると、{{site.data.keyword.openwhisk_short}} アクションを API として公開できます。 API を定義した後に、セキュリティー・ポリシーおよびレート制限ポリシーを適用したり、API 使用量および応答ログを表示したり、API 共有ポリシーを定義したりすることができます。  

{{site.data.keyword.openwhisk_short}} API を作成するには、以下のステップを実行します。

1. {{site.data.keyword.openwhisk_short}} ダッシュボードで**「API」**タブをクリックします。 既に {{site.data.keyword.openwhisk_short}} API を作成済みの場合は、{{site.data.keyword.openwhisk_short}} API のリストが表示されます。 {{site.data.keyword.openwhisk_short}} API がない場合は、「開始」画面が表示されます。 
2. **「{{site.data.keyword.openwhisk_short}} API の作成 (Create a OpenWhisk API)」**をクリックします。 「{{site.data.keyword.openwhisk_short}} 用の API の作成 (Create API for OpenWhisk)」ウィンドウが表示されます。 
3. 「API 情報 (API Info)」セクションのフィールドに入力し、次に**「操作の作成 (Create Operation)」**をクリックします。 「操作の作成 (Create Operation)」ウィンドウが表示されます。 API 用のエンドポイント、https パス、およびメソッドを定義する操作を作成します。
4. 「操作の作成 (Create Operation)」ウィンドウで、{{site.data.keyword.openwhisk_short}} 操作の必須フィールドに入力します。 「操作の作成 (Create Operation)」ウィンドウに含まれるフィールドには、以下のものがあります。

    * パス - API が配置されている場所のパス。 
    * Verb - API の HTTP メソッド。 以下のメソッドから選択します。
	    * DELETE
		* GET
		* HEAD
		* OPTIONS
		* PATCH
		* POST
		* PUT
	* アクションを含むパッケージ (Package containing action) - この API に使用したいアクションが含まれている可能性のある、組織内で既に使用可能なパッケージ。 このフィールドについて詳しくは、『[Cloud Functions パッケージの使用と作成 (Using and creating Cloud Functions packages)](../openwhisk/openwhisk_packages.html)』を参照してください。
	* アクション - **「{{site.data.keyword.Bluemix_notm}} で使用可能なアクション (Actions that are available in {{site.data.keyword.Bluemix_notm}})」**というオプションのみが選択可能です。
	* 応答コンテンツ・タイプ - これは、API が情報を返す際に使用する形式を示します。 以下の形式から選択できます。
	    * application/json - これがデフォルトの形式であり、最も多く使用されます。
		* text/html - これは、Web サイトで使用される応答に使用されます。
		* text/plain - これはプレーン・テキストで指定され、コンマ区切り値ファイルで使用できます。
		* image/svg+xml - これは、画面キャプチャーが応答の主な形式である場合に使用できます。
		* アクションから「Content-Type」ヘッダーを使用 (Use "Content-Type" header from action) - これは、応答のヘッダー内にあるコンテンツのタイプに依存します。 
	
5. **「作成」**を選択して操作を作成します。 その操作が、{{site.data.keyword.openwhisk_short}} アクション・テーブルを呼び出す操作に追加されます。
5. 入力したい残りの情報を入力します。 後で API を管理するときに、残りの情報を追加したり更新したりすることもできます。
6. **「保存」**をクリックします。 API の API 管理概要ページが開き、定義したすべての情報が表示されます。
7. [「API の管理 (Manage APIs)」](manage_apis.html)で API の管理を続行します。
