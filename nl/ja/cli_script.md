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

# API Management CLI を使用したコマンドの実行
{: #apim-cli-over}

{{site.data.keyword.Bluemix_notm}} API Management CLI を使用すると、{{site.data.keyword.Bluemix_notm}} グラフィカル・ユーザー・インターフェースで実行できるものと同じタスクの一部をコマンド・ラインで実行できます。コマンドは、端末ウィンドウで個別に入力することも、スクリプトでシーケンスとして呼び出すこともできます。
{:shortdesc}

## 前提条件
{: #apim-cli-script-prereq}

API Management CLI を使用するには、事前に以下のステップを完了している必要があります。

* [Bluemix ID](../../admin/adminpublic.html#signing-up-for-bluemix){: new_window} を取得します。 
* [Bluemix コマンド・ライン](../../cli/reference/bluemix_cli/index.html#getting-started){: new_window}をダウンロードしてインストールします。
* {{site.data.keyword.Bluemix_notm}} [API Management コマンド・ライン・プラグイン](../../cli/reference/bluemix_cli/index.html#install_plug-in){: new_window}をインストールします。
* {{site.data.keyword.Bluemix_notm}} コマンド・ラインに[ログイン](../../cli/reference/bluemix_cli/bx_cli.html){: new_window}します。

## API 用のコマンドのサンプル CLI シーケンス

以下のステップは、API へのゲートウェイの追加から、API からのゲートウェイの削除まで、API Management コマンドの完全なサイクルを示しています。

1. {{site.data.keyword.Bluemix_notm}} へのログイン 
    ```
    bluemix login -a https://api.ng.bluemix.net -c account_ID (1) -u username -p password
    ```
    {:codeblock}
    コマンド・ライン・インターフェースによってデフォルトの {{site.data.keyword.Bluemix_notm}} 組織にログインします。

2. API の表示
    ```
    bluemix apim apis
    ```
    {:codeblock}
    デフォルト組織内の API を表示します。

3. API の作成
    ```
    bluemix apim api-create --name <API_NAME> --file <path_to_Swagger_file>
    ```
    {:codeblock}
    Swagger ファイルを使用して、{{site.data.keyword.Bluemix_notm}} 組織内で指定した API から管理対象 API を作成します。

4. 既存の API 定義の更新
    ```
    bluemix apim api-update --name <API_NAME> --file <path_to_new_Swagger_file>
    ```
    {:codeblock}
    指定した API の既存の定義を、新しい Swagger ファイル定義に置き換えます。

5. API の公開
    ```
    bluemix apim api-expose --name <API_NAME>
    ```
    {:codeblock}
    API を公開します。

6. API の共有
    ```
    bluemix apim api-share --name <API_NAME>
    ```
    {:codeblock}
    自分の {{site.data.keyword.Bluemix_notm}} 組織の外部にいる他のユーザーと API を共有します。

7. API の公開の停止
    ```
    bluemix apim api-unexpose --name <API_NAME>
    ```
    {:codeblock}
    自分の {{site.data.keyword.Bluemix_notm}} 組織の外部での API の共有を停止します。

8. API のキーの表示
    ```
    bluemix apim keys --name <API_NAME>
    ```
    {:codeblock}
    API に関連付けられているキーを表示します (存在する場合)。

9. API の共有の停止
    ```
    bluemix apim api-unshare --name <API_NAME>
    ```
    {:codeblock}
    API の共有を停止します。
	
10. API の削除
    ```
    bluemix apim api-delete --name <API_NAME>
    ```
    {:codeblock}
    API からゲートウェイを削除します。管理されなくなります。
    重要: Cloud Foundry API を削除した場合、ベースの Cloud Foundry アプリは {{site.data.keyword.Bluemix_notm}} サービス内に残りますが、管理されなくなります。OpenWhisk API を削除すると、個々の OpenWhisk アクション間のすべての相互作用がなくなります。OpenWhisk API が削除された後に、再度それを使用したい場合は、再作成する必要があります。
    
API Management コマンドとそのオプションの完全なリストについては、『[コマンド・ライン・インターフェースのコマンド (Command-line interface commands)](../../cli/plugins/api-management-cliplugin/index.html)』を参照してください。

