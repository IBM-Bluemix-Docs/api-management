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

# 추가 API 관리 기능에 액세스
{: #upgrade}

{{site.data.keyword.Bluemix}} API와 함께 제공되는 API 관리 기능을 사용하면 호출 속도, OAuth 및 보기 분석을 제한적으로 제어할 수 있습니다. {{site.data.keyword.apiconnect_full}} 서비스로 업그레이드하면 API에 대한 관리를 보다 잘 제어할 수 있습니다. {{site.data.keyword.apiconnect_short}} 서비스는 보안 정책에 대한 추가 선택사항과 함께 속도 제한에 대한 추가 제어 권한을 제공합니다. 이와 더불어 API를 소셜 네트워크에서 공유하고 개발자 커뮤니티에 참여할 수 있도록 사용자는 완벽하게 사용자 정의할 수 있는 개발자 포털을 구성할 수 있습니다. 기타 유용한 측면에는 다음이 포함됩니다.
* 라이프사이클 관리
* 컴포지트 API
* 웹 서비스 통합
* 프로토콜 중개
* 스키마에서 API 생성
* 마이크로 서비스 개발

{{site.data.keyword.apiconnect_short}} 서비스로 마이그레이션하기는 어렵지 않으며, 관리 중인 API를 API 관리에서 다시 작성할 필요가 없습니다. API를 자동으로 또는 수동으로 마이그레이션할 수 있습니다.

## API를 {{site.data.keyword.apiconnect_short}}로 자동 마이그레이션
{: #auto_migrate_api}

{{site.data.keyword.apiconnect_short}}로 업그레이드하려면 마이그레이션하는 API 유형에 대해 다음 프로시저를 선택하고 완료하여 API를 API 관리에서 {{site.data.keyword.apiconnect_short}} 서비스로 마이그레이션해야 합니다.

### Cloud Functions API

1. {{site.data.keyword.Bluemix_notm}} 메뉴에서 **Functions**를 선택하여 Cloud Functions를 보십시오.

2. Functions 목록의 탐색에서 **API**를 선택하십시오.

3. 마이그레이션할 Function API의 이름을 선택하십시오.

4. 탐색에서 **정의**를 선택하십시오.

5. *API 정의 파일* 섹션에서 **API 정의 파일** > **API Connect에서 열기** > **계속**을 선택하십시오. 기존 {{site.data.keyword.apiconnect_short}} 서비스가 아직 있는 경우 API를 기존 서비스로 자동으로 마이그레이션합니다. 아직 {{site.data.keyword.apiconnect_short}} 서비스가 구성되지 않은 경우 무료 라이트 플랜으로 서비스를 자동 추가하고 API를 마이그레이션합니다. 인스턴스가 프로비저닝에 실패한 경우 [{{site.data.keyword.apiconnect_short}}로 API 수동 마이그레이션](#man_migrate_api)의 단계를 완료하여 새 서비스로 수동으로 마이그레이션하십시오. 

6. 원래 API의 화면을 닫기 전에 **관리 API 노출**에 대한 슬라이더를 사용 안함으로 설정하십시오. 이렇게 하면 이전 버전의 엔드포인트에서 조치를 수행할 수 없습니다.

### Cloud Foundry API

1. {{site.data.keyword.Bluemix_notm}} 대시보드에서 기존 Cloud Foundry API 소스를 여십시오. 

2. 탐색 메뉴에서 **API 관리**를 선택하십시오.

3. 탐색에서 **정의**를 선택하십시오.

4. **API 정의 파일** > **API Connect에서 열기** > **계속**을 선택하십시오. 기존 {{site.data.keyword.apiconnect_short}} 서비스가 아직 있는 경우 API를 기존 서비스로 자동으로 마이그레이션합니다. 아직 {{site.data.keyword.apiconnect_short}} 서비스가 구성되지 않은 경우 무료 라이트 플랜으로 서비스를 자동 추가하고 API를 마이그레이션합니다. 인스턴스가 프로비저닝에 실패한 경우 [{{site.data.keyword.apiconnect_short}}로 API 수동 마이그레이션](#man_migrate_api)의 단계를 완료하여 새 서비스로 수동으로 마이그레이션하십시오.
   
5. 컨텐츠를 {{site.data.keyword.apiconnect_short}} 인스턴스로 마이그레이션한 후 마이그레이션된 버전에 액세스하기 위해 제공된 링크를 선택하십시오.
    **중요:** API의 여러 인스턴스 실행과 관련된 문제를 방지하려면 API의 원래 버전에서 *API 관리* 슬라이더를 사용 안함으로 설정해야 합니다.

6. 탐색에서 **API** 탭을 선택하십시오.

7. **드래프트**를 선택하여 새 API를 확인하십시오.

## API를 {{site.data.keyword.apiconnect_short}}로 수동 마이그레이션
{: #man_migrate_api}

{{site.data.keyword.apiconnect_short}} 서비스로 API를 마이그레이션하는 프로세스가 올바르게 완료되지 않은 경우 다음 단계를 완료하여 수동으로 마이그레이션하십시오.

1. API를 여십시오.
	1. {{site.data.keyword.Bluemix_notm}}에 로그인하십시오.
	2. Cloud Foundry 앱의 경우 다음을 수행하십시오. 
		1. 메뉴에서 **대시보드**를 선택하십시오.
		2. 마이그레이션할 Cloud Foundry 앱의 이름을 선택하십시오.
		3. 탐색에서 **API 관리**를 선택하십시오.
	3. Cloud Functions 조치의 경우 다음을 수행하십시오. 
		1. 메뉴에서 **Functions**를 선택하십시오.
		2. 탐색에서 **API**를 선택하십시오.
		3. 마이그레이션할 API의 이름을 선택하십시오.
2. API 관리에서 API에 대한 Swagger 문서를 다운로드하십시오.
    1. 탐색에서 **정의**를 선택하십시오.
	2. **API 정의 파일**을 선택하십시오.
    3. 파일 유형에 따라 **YAML 내보내기** 또는 **JSON 내보내기**를 선택하여 API의 정의를 다운로드하십시오. 파일이 다운로드 폴더로 다운로드됩니다.
3. {{site.data.keyword.apiconnect_short}} 인스턴스를 작성하고 준비하십시오. 
	1. 탐색의 **API**로 이동하여 서비스를 필터링하십시오.
	2. API Connect 서비스를 선택하십시오. 
    3. {{site.data.keyword.Bluemix_notm}} 카탈로그에서 {{site.data.keyword.apiconnect_short}} 서비스의 인스턴스를 작성하십시오.
	4. 플랜을 선택하십시오. 라이트 플랜은 무료 옵션입니다.
	5. **작성**을 선택하여 인스턴스를 작성하십시오.
4. 다음 단계를 완료하여 {{site.data.keyword.apiconnect_short}} 인스턴스로 Swagger 문서를 가져오십시오.
	1. {{site.data.keyword.apiconnect_short}} 서비스 대시보드의 메뉴에서 **탐색 대상... (>>)** > **드래프트**를 선택하십시오.
	2. API 탭을 선택하십시오.
	3. **+추가** > **URL 또는 파일에서 API 가져오기**를 선택하십시오.
	4. API 관리에서 다운로드된 Swagger 파일을 찾아서 선택하십시오. **열기**를 선택하십시오.
	5. **가져오기**를 선택하여 API를 {{site.data.keyword.apiconnect_short}} 서비스로 가져오십시오.
5. API의 여러 인스턴스 실행으로 인한 문제를 방지하려면 API의 원래 버전에서 *API 관리* 슬라이더를 사용 안함으로 설정해야 합니다.

API가 {{site.data.keyword.apiconnect_short}} 서비스 인스턴스에서 사용 가능합니다. 

## API 공개

다음 단계를 완료하여 계속해서 API를 공개할 수 있습니다.

1. 카탈로그를 작성하십시오.
	1. **+추가**를 선택하여 카탈로그를 작성하십시오.
	2. 표시 이름과 카탈로그의 이름을 입력하고 **추가**를 선택하십시오.
	3. 작성된 카탈로그를 선택하십시오.
2. API에 대한 설정을 지정하십시오.
    1. **제품 작성**을 선택하십시오.
	2. 제품의 이름을 지정하십시오.
	2. 해당 설정을 보려는 작성된 제품을 선택하십시오.
	3. API에 대한 속도 제한을 설정하십시오.
	4. API에 대한 티어를 설정하십시오.
3. 필요하면 API에 대한 엔드포인트를 추가하십시오.
    1. API를 선택하십시오.
	2. 어셈블리 탭을 선택하십시오.
	3. 아직 지정되지 않았으면 엔드포인트를 추가하십시오.
	
 API를 마이그레이션한 후 {{site.data.keyword.apiconnect_short}} 서비스 타일을 열거나 {{site.data.keyword.Bluemix_notm}} 대시보드를 통해 모든 API 관리 기능에 액세스할 수 있습니다. 

