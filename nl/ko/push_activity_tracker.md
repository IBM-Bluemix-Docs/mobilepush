---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-06-06"

keywords: push notifications, notifications, activity tracker events

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# Activity Tracker 이벤트
{: #push_activity_tracker}

{{site.data.keyword.cloudaccesstrailfull}} 서비스는 사용자의 IBM Cloud 서비스에 대한 상호작용을 모니터합니다. 사용자 및 애플리케이션이 IBM Cloud 서비스와 상호작용하는 방법을 검색하고 분석할 수 있습니다.

클라우드 관리자, 보안 및 개발자는 다음을 수행할 수 있습니다.

<dl>
	<dt>보안 위반을 모니터하고 조사하기 위해 환경에 대한 인사이트 얻기</dt>
	<dd>사용자 및 애플리케이션과 프로비저닝된 IBM Cloud 리소스 간의 상호작용을 캡처합니다. 가능한 보안 위반 또는 무단 액세스를 조사하십시오.</dd>
	<dt>규제, 준수 및 레코드 보유 요구 아카이브</dt>
	<dd>필요한 만큼 이벤트를 저장하고 클라우드 클래스의 경제적 스토리지 솔루션을 안전하게 보호합니다. API를 통해 수집된 이벤트 데이터를 조회하거나 클라우드 활동 데이터를 내보내십시오.</dd>
	<dt>디버깅 및 용량 플랜을 수행할 DevOps 팀을 위한 클라우드 투명성</dt>
	<dd>클라우드 활동 이벤트는 IBM Cloud 관련 IT 오퍼레이션에 대한 투명성을 제공합니다. 클라우드 서비스가 사용된 시기 및 방법을 식별하여 애플리케이션을 격리하고 디버그하십시오. 시간 경과에 따라 수집된 데이터를 조회하여 클라우드 성장 및 계절성 요구를 예측하십시오.</dd>
	<dt>콜렉션 단순화 및 클라우드 보안 개선</dt>
	<dd>{{site.data.keyword.cloudaccesstrailshort}}에서 자동으로 IBM Cloud 이벤트를 캡처합니다.</dd>
</dl>


{{site.data.keyword.cloudaccesstrailshort}} 활동 로그를 사용하여 다음 정보를 식별할 수 있습니다.

- 클라우드 서비스에 API 호출을 수행한 사용자
- API 호출이 발생하는 곳의 소스 IP 주소
- API 호출이 발생하는 때의 시간소인
- API 호출의 상태

## 이벤트 목록
{: #actions}

다음 표에는 {{site.data.keyword.mobilepushshort}}에 대한 {{site.data.keyword.cloudaccesstrailshort}} 이벤트가 나열되어 있습니다.
<table>
  <caption>표 1. 이벤트를 생성하는 조치 목록</caption>
  <tr>
    <th>조치</th>
	  <th>설명</th>
  <tr>
  <tr>
    <td>imfpush.app.update</td>
	  <td>애플리케이션에 대한 업데이트</td>
  </tr>
  <tr>
    <td>imfpush.app-conf.delete</td>
	  <td>애플리케이션 구성 삭제</td>
  </tr>
  <tr>
    <td>imfpush.app-conf.update</td>
	  <td>애플리케이션 구성 업데이트</td>
  </tr>
  <tr>
    <td>imfpush.app-tag.create</td>
	  <td>태그 작성</td>
  </tr>
  <tr>
    <td>imfpush.app-tag.delete</td>
	  <td>태그 삭제</td>
  </tr>
  <tr>
    <td>imfpush.app-tag.update</td>
	  <td>태그 업데이트</td>
  </tr>  
  <tr>
    <td>imfpush.app-webhook.create</td>
	  <td>웹훅 작성</td>
  </tr> 
  <tr>
    <td>imfpush.app-webhook.delete</td>
	  <td>웹훅 삭제</td>
  </tr>   
  <tr>
    <td>imfpush.app-webhook.update</td>
	  <td>웹훅 업데이트</td>
  </tr>   
</table>


{{site.data.keyword.cloudaccesstrailshort}} 작업에 대한 자세한 정보는 [여기의 문서](https://cloud.ibm.com/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov){: new_window}를 참조하십시오.


현재, Activity Tracker 이벤트는 `IBM Cloud - 미국 남부 지역`에서만 사용 가능합니다.
{: note}
