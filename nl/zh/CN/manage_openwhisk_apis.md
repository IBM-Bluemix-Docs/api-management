---

copyright:
  years: 2017,2018
lastupdated: "2018-07-02"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 從 {{site.data.keyword.openwhisk_short}} 動作建立 API
{: #manage_openwhisk_apis}

透過 API Management 進行管理，有利於 {{site.data.keyword.openwhisk_short}} 動作。

使用 API Management，您可以將 {{site.data.keyword.openwhisk_short}} 動作公開為 API。在您定義 API 之後，可以套用安全和比率限制原則、檢視 API 使用情形和回應日誌，以及定義 API 共用原則。  

若要建立 {{site.data.keyword.openwhisk_short}} API，請完成下列步驟：

1. 在「{{site.data.keyword.openwhisk_short}} 儀表板」中，按一下 **API** 標籤。如果您已建立 {{site.data.keyword.openwhisk_short}} API，則會顯示 {{site.data.keyword.openwhisk_short}} API 清單。如果您沒有任何 {{site.data.keyword.openwhisk_short}} API，則會顯示「開始使用」畫面。 
2. 按一下**建立 {{site.data.keyword.openwhisk_short}} API**。隨即會顯示「建立 {{site.data.keyword.openwhisk_short}} 的 API」視窗。 
3. 完成「API 資訊」區段中的欄位，然後按一下**建立作業**。隨即會顯示「建立作業」視窗。您可以建立作業來定義 API 端點、https 路徑及 API 的方法。
4. 在「建立作業」視窗中，完成 {{site.data.keyword.openwhisk_short}} 作業的必要欄位。「建立作業」視窗中內含的欄位包括下列欄位：

    * 路徑 - API 所在的路徑。 
    * 動詞 - API 的 HTTP 方法。從下列方法中選取：
	    * DELETE
		* GET
		* HEAD
		* OPTIONS
		* PATCH
		* POST
		* PUT
	* 套件包含動作 - 組織中已有的套件，可能具有您要用於此 API 的動作。如需此欄位的相關資訊，請參閱[使用及建立 Cloud Functions 套件](../openwhisk/openwhisk_packages.html)。
	* 動作 - **{{site.data.keyword.Bluemix_notm}}** 中提供的動作，是唯一可用的選項。
	* 回應內容類型 - 這可識別 API 傳回資訊的格式。您可以從下列格式中選取：
	    * application/json - 這是預設格式，且是最常使用的格式。
		* text/html - 這用於在網站上使用的回應。
		* text/plain - 以純文字提供，可用於以逗點區隔值的檔案。
		* image/svg+xml - 當畫面擷取是回應主要格式時，可使用此格式。
		* 使用動作中的 "Content-Type" 標頭 - 取決於回應標頭中的內容類型。 
	
5. 選取**建立**，以建立作業。「作業」會新增至呼叫 {{site.data.keyword.openwhisk_short}} 動作表格的「作業」。
5. 完成您要完成的其餘資訊。當您管理 API 時，也可以稍後再新增或更新其餘資訊。
6. 按一下**儲存**。隨即會開啟 API 的「API Management 概觀」頁面，並顯示您剛剛所定義的所有資訊。
7. 使用[管理 API](manage_apis.html)，來繼續管理 API。
