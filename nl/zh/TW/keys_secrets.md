---

copyright:
  years: 2017
lastupdated: "2017-11-09"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 管理金鑰和密碼
{: #keys_secrets}

當您的 API 由 API Management 管理時，您可以使用金鑰和密碼來控制對 API 的存取。

## 建立金鑰和密碼
{: #create_key_secret}

若要將金鑰新增至您的 API，請完成下列步驟：

1. 開啟您的 Cloud Foundry 應用程式或 OpenWhisk API（若其尚未開啟時）。

2. 選取導覽中的 *API Management*。

3. 選取「共用 & 金鑰」標籤，以存取該應用程式或 API 的金鑰。*附註：必須等到您第一次儲存應用程式或 API 時才能看到標籤。*

4. 請確定**公開受管理 API** 調節器設為*開* 的位置。您的 API 必須先公開，您才能指派金鑰。

5. 為可以存取您的 {{site.data.keyword.Bluemix_notm}} 組織的客戶建立金鑰。
  1. 在「在 {{site.data.keyword.Bluemix_notm}} 組織內共用」區段中，選取**建立 API 金鑰 +**。金鑰和密碼會自動建立並在正確的欄位中輸入。您無法針對此類型的金鑰更新金鑰或密碼。 
  2. 為您的金鑰和密碼輸入名稱，以幫助您識別它。例如，將使用它的客戶名稱。
  3. 選取**儲存**，以儲存新的金鑰。
  4. 必要的話，您可以重複步驟 *a* 到 *c*，以取得其他金鑰。每一個 API 在此區段中您最多可以有 5 個金鑰。

6. 為不是您的 {{site.data.keyword.Bluemix_notm}} 組織成員的客戶建立金鑰。
  1. 在「在 {{site.data.keyword.Bluemix_notm}} 組織外共用」區段中，選取**建立 API 金鑰 +**。金鑰會自動建立並在正確的欄位中輸入。此類型的金鑰一開始沒有任何密碼顯示。您無法更新此金鑰。 
  2. 為您的金鑰輸入名稱，以幫助您識別它。例如，將使用它的客戶名稱。
  3. 選用項目：如果您要將密碼新增至金鑰中，請針對要將該密碼新增至其中的金鑰選取 **API 入口網站鏈結**，然後選取**設定 API 密碼**。
  4. 選取**儲存**，以儲存新的金鑰。
  5. 必要的話，您可以重複步驟 *a* 到 *d*，以取得其他金鑰。每一個 API 在此區段中您最多可以有 5 個金鑰。選取「共用 & 金鑰」標籤時，會針對 API 列出您的金鑰。

## 在 API 呼叫中指定金鑰和密碼
{: #spec_key_secret}

若您的客戶在呼叫的標頭中包括正確的金鑰、密碼或這兩項時，則他們只能呼叫您的 API。若要呼叫 API，他們必須在 API 呼叫中包括金鑰和密碼，如下列範例中所示：
```
curl --request PUT \
  --url https://appidtest.mybluemix.net/ \
  --header 'accept: application/json' \
  --header 'content-type: application/json' \
  --header 'x-ibm-client-secret: add_secret_here' \
  --data '{"id":999999999999999}'
```
{: codeblock}
其中 *add_secret_here* 會取代為正確金鑰的密碼。 

## 刪除 API 金鑰
{: #delete_key}

在某個時候，您會想要移除金鑰。可能是使用您的 API 的客戶建立其自己的 API 且不再需要您的 API。為了確定其客戶都不再使用您的 API，您可以刪除該金鑰。若要從服務刪除金鑰，請完成下列步驟：

1. 開啟您的 Cloud Foundry 應用程式或 OpenWhisk API（若其尚未開啟時）。

2. 選取導覽中的 *API Management*。

3. 選取*共用 & 金鑰* 標籤。

4. 尋找您要刪除的金鑰。提示：命名金鑰以使其易於識別，在進行此動作時會很有幫助。

5. 在您要刪除的金鑰旁邊，選取選項圖示（三個垂直點）。 

6. 選取**刪除金鑰**。

7. 確認刪除動作，以移除該金鑰。
