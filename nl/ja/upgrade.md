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

# 追加の API Management フィーチャーの利用
{: #upgrade}

{{site.data.keyword.Bluemix}} API と共に提供される  API Management 機能により、呼び出しレート、OAuth、およびビューの分析を限定的に制御できます。 {{site.data.keyword.apiconnect_full}} サービスにアップグレードすることによって、より充実した API の管理制御が可能になります。 {{site.data.keyword.apiconnect_short}} サービスでは、セキュリティー・ポリシーの選択肢の数が増え、レート制限をさらにきめ細かく制御できます。 これに加えて、API をソーシャル化して開発者コミュニティーを運用できるように、完全にカスタマイズ可能な開発者ポータルを構成できます。 その他の利点としては、以下のような機能が挙げられます。
* ライフサイクル管理
* 複合 API
* Web サービスの統合
* プロトコル・メディエーション
* スキーマからの API 生成
* マイクロサービス開発

{{site.data.keyword.apiconnect_short}} サービスへのマイグレーションは簡単であり、API Management によって管理しているどの API も再作成する必要はありません。 API のマイグレーションは自動で行うことも手動で行うこともできます。

## {{site.data.keyword.apiconnect_short}} への API の自動マイグレーション
{: #auto_migrate_api}

{{site.data.keyword.apiconnect_short}} にアップグレードすることを決定した場合、API Management から {{site.data.keyword.apiconnect_short}} サービスへ API をマイグレーションする必要があります。そのためには、マイグレーションする API のタイプを選択し、それに対して以下の手順を実行します。

### Cloud Functions API

1. {{site.data.keyword.Bluemix_notm}} メニューで**「機能」**を選択して、Cloud Functions を表示します。

2. 「機能」リストのナビゲーションで**「API」**を選択します。

3. マイグレーションする機能 API の名前を選択します。

4. ナビゲーションで**「定義」**を選択します。

5. *「API 定義ファイル」*セクションで、**「API 定義ファイル」** > **「API Connect で開く (Open in API Connect)」** > **「続行」**を選択します。既存の {{site.data.keyword.apiconnect_short}} サービスが既にある場合は、API が既存のサービスに自動的にマイグレーションされます。 まだ {{site.data.keyword.apiconnect_short}} サービスを構成していない場合は、自動的に無料のライト・プランでサービスが追加され、API がマイグレーションされます。 インスタンスをプロビジョンできなかった場合は、『[{{site.data.keyword.apiconnect_short}} への API の手動マイグレーション](#man_migrate_api)』のステップを実行して、手動で新規サービスにマイグレーションしてください。 

6. 元の API の画面を閉じる前に、**「管理対象 API の公開」**のスライダーを無効にします。 これにより、どのユーザーも古いバージョンのエンドポイントを操作できなくなります。

### Cloud Foundry API

1. {{site.data.keyword.Bluemix_notm}} ダッシュボードで既存の Cloud Foundry API ソースを開きます。 

2. ナビゲーション・メニューで**「API Management」**を選択します。

3. ナビゲーションで**「定義」**を選択します。

4. **「API 定義ファイル」** > **「API Connect で開く (Open in API Connect)」** > **「続行」**を選択します。既存の {{site.data.keyword.apiconnect_short}} サービスが既にある場合は、API が既存のサービスに自動的にマイグレーションされます。 まだ {{site.data.keyword.apiconnect_short}} サービスを構成していない場合は、自動的に無料のライト・プランでサービスが追加され、API がマイグレーションされます。 インスタンスをプロビジョンできなかった場合は、『[{{site.data.keyword.apiconnect_short}} への API の手動マイグレーション](#man_migrate_api)』のステップを実行して、手動で新規サービスにマイグレーションしてください。
   
5. コンテンツが {{site.data.keyword.apiconnect_short}} インスタンスにマイグレーションされたら、提供されたリンクを選択して、マイグレーション済みのバージョンにアクセスします。
    **重要:** 実行中の API の複数インスタンスでの問題を回避するため、必ず元のバージョンの API で*「API の管理 (Manage the API)」*スライダーを無効にしてください。

6. ナビゲーションで**「API」**タブを選択します。

7. **「ドラフト (Drafts)」**を選択して、新規 API を表示します。

## {{site.data.keyword.apiconnect_short}} への API の手動マイグレーション
{: #man_migrate_api}

API を {{site.data.keyword.apiconnect_short}} サービスにマイグレーションするプロセスが正しく完了しなかった場合、以下のステップを実行して手動でマイグレーションしてください。

1. API を開きます。
	1. {{site.data.keyword.Bluemix_notm}} にサインインします。
	2. Cloud Foundry アプリの場合: 
		1. メニューで**「ダッシュボード」**を選択します。
		2. マイグレーションする Cloud Foundry アプリの名前を選択します。
		3. ナビゲーションで**「API Management」**を選択します。
	3. Cloud Functions アクションの場合: 
		1. メニューで**「機能」**を選択します。
		2. ナビゲーションで**「API」**を選択します。
		3. マイグレーションする API の名前を選択します。
2. API Management から API の Swagger 文書をダウンロードします。
    1. ナビゲーションで**「定義」**を選択します。
	2. **「API 定義ファイル」**を選択します。
    3. ファイル・タイプに応じて**「YAML のエクスポート」**または**「JSON のエクスポート」**を選択して、API の定義をダウンロードします。 ファイルは downloads フォルダーにダウンロードされます。
3. {{site.data.keyword.apiconnect_short}} インスタンスを作成して準備します。 
	1. ナビゲーションで**「API」**に移動して、サービスをフィルター処理します。
	2. API Connect サービスを選択します。 
    3. {{site.data.keyword.Bluemix_notm}} カタログから {{site.data.keyword.apiconnect_short}} サービスのインスタンスを作成します。
	4. プランを選択します。 ライト・プランは無料のオプションです。
	5. **「作成」**を選択してインスタンスを作成します。
4. 以下のステップを実行して、{{site.data.keyword.apiconnect_short}} インスタンスに Swagger 文書をインポートします。
	1. {{site.data.keyword.apiconnect_short}} サービス・ダッシュボードのメニューで**「ナビゲート先... (>>) (Navigate to... (>>))」** > **「ドラフト (Drafts)」**を選択します。
	2. 「API」タブを選択します。
	3. **「+追加 (+Add)」** > **「ファイルまたは URL から API をインポート (Import API from a file or URL)」**を選択します。
	4. API Management からダウンロードした Swagger ファイルを見つけて選択します。 **「開く」**を選択します。
	5. **「インポート」**を選択して、API を {{site.data.keyword.apiconnect_short}} サービスにインポートします。
5. API の複数インスタンスの実行から生じる問題を回避するため、必ず元のバージョンの API で*「API の管理 (Manage the API)」*スライダーを無効にしてください。

API が {{site.data.keyword.apiconnect_short}} サービス・インスタンス内で使用可能です。 

## API の公開

続いて、以下のステップを実行して API を公開することができます。

1. カタログを作成します。
	1. **「+追加 (+Add)」**を選択してカタログを作成します。
	2. 表示名とカタログの名前を入力して**「追加」**を選択します。
	3. 作成したカタログを選択します。
2. API の設定を指定します。
    1. **「製品の作成 (Create product)」**を選択します。
	2. 製品の名前を指定します。
	2. 作成した製品を選択して、その設定を表示します。
	3. API のレート制限を設定します。
	4. API の層を設定します。
3. 必要に応じて、API 用のエンドポイントを追加します。
    1. API を選択します。
	2. 「アセンブリー (Assembly)」タブを選択します。
	3. エンドポイントがまだ指定されていない場合は、エンドポイントを追加します。
	
 API をマイグレーションすると、{{site.data.keyword.apiconnect_short}} サービス・タイルを開くことによって、および {{site.data.keyword.Bluemix_notm}} ダッシュボードを通じて、API Management のすべてのフィーチャーにアクセスできるようになります。 

