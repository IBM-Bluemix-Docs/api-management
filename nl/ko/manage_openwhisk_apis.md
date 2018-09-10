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

# {{site.data.keyword.openwhisk_short}} 액션에서 API 작성
{: #manage_openwhisk_apis}

{{site.data.keyword.openwhisk_short}} 액션은 API 관리를 통해 관리된다는 점에서 유용할 수 있습니다.

API 관리를 사용하면 {{site.data.keyword.openwhisk_short}} 액션을 API로서 노출할 수 있습니다. 일단 API가 정의되면, 보안 및 속도 제한 정책을 적용하고 API 사용량 및 응답 로그를 볼 수 있으며 API 공유 정책을 정의할 수 있습니다.  

{{site.data.keyword.openwhisk_short}} API를 작성하려면 다음 단계를 완료하십시오.

1. {{site.data.keyword.openwhisk_short}} 대시보드에서 **API** 탭을 클릭하십시오. {{site.data.keyword.openwhisk_short}} API가 이미 작성된 경우에는 {{site.data.keyword.openwhisk_short}} API의 목록이 표시됩니다. 아직 {{site.data.keyword.openwhisk_short}} API가 없는 경우에는 시작하기 화면이 표시됩니다. 
2. **{{site.data.keyword.openwhisk_short}} API 작성**을 클릭하십시오. {{site.data.keyword.openwhisk_short}}의 API 작성 대화 상자가 표시됩니다. 
3. API 정보 섹션의 필드를 채우고 **조작 작성**을 클릭하십시오. 조작 작성 창이 표시됩니다. API에 대한 메소드 및 https 경로, 엔드포인트를 정의하는 조작을 작성할 수 있습니다.
4. "조작 작성" 창에서 {{site.data.keyword.openwhisk_short}} 조작에 대한 필수 필드를 채우십시오. 다음과 같은 필드가 "조작 작성" 창에 포함되어 있습니다.

    * 경로 - API가 위치한 경로입니다. 
    * 동사 - API에 대한 HTTP 메소드입니다. 다음 메소드에서 선택하십시오.
	    * DELETE
		* GET
		* HEAD
		* OPTIONS
		* PATCH
		* POST
		* PUT
	* 조치가 포함된 패키지 - 조직에서 이미 사용 가능한 패키지 중 이 API에 대해 사용할 조치가 포함된 패키지입니다. 이 필드에 대한 자세한 정보는 [Cloud Functions 패키지 사용 및 작성](../openwhisk/openwhisk_packages.html)을 참조하십시오.
	* 조치 - **{{site.data.keyword.Bluemix_notm}}에서 사용 가능한 조치**가 사용할 수 있는 유일한 옵션입니다.
	* 응답 컨텐츠 유형 - 이는 API가 정보를 리턴하는 형식을 식별합니다. 다음 형식에서 선택할 수 있습니다.
	    * application/json - 이는 기본 형식이며 가장 자주 사용됩니다.
		* text/html - 이는 웹 사이트에 사용되는 응답에 사용됩니다.
		* text/plain - 이는 일반 텍스트로 제공되며 쉼표로 분리된 값 파일에서 사용될 수 있습니다.
		* image/svg+xml - 이는 화면 캡처가 응답의 기본 형식일 때 사용될 수 있습니다.
		* 조치의 "Content-Type" 헤더 사용 - 이는 응답의 헤더에 있는 컨텐츠의 유형에 종속됩니다. 
	
5. **작성**을 선택하여 조작을 작성하십시오. 조작이 {{site.data.keyword.openwhisk_short}} 액션 테이블을 호출하는 조작에 추가됩니다.
5. 채우고 싶은 나머지 정보를 채우십시오. 나중에 API를 관리할 때 나머지 정보를 추가하거나 업데이트할 수도 있습니다.
6. **저장**을 클릭하십시오. API에 대한 API 관리 개요 페이지가 열리며 방금 정의한 모든 정보가 표시됩니다.
7. [API 관리](manage_apis.html)를 통해 API를 계속 관리하십시오.
