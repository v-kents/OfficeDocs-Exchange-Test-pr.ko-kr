﻿---
title: '보존 태그 및 보존 정책: Exchange 2013 Help'
TOCTitle: 보존 태그 및 보존 정책
ms:assetid: 48c13be5-3f01-4849-a089-766210e54f89
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dd297955(v=EXCHG.150)
ms:contentKeyID: 50483022
ms.date: 01/10/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# 보존 태그 및 보존 정책

 

_**적용 대상:** Exchange Online, Exchange Server 2013_

_**마지막으로 수정된 항목:** 2016-12-09_

Microsoft Exchange Server 2013 및 Exchange Online의 MRM(메시징 레코드 관리)은 조직에서 전자 메일 수명 주기를 관리하고 전자 메일 및 기타 통신과 관련된 법적 위험을 줄이는 데 유용합니다. MRM을 사용하면 회사 정책, 정부 규정 또는 법적 요구 사항을 준수하기 위해 필요한 메시지를 간편하게 보존하고, 법적 가치 또는 업무적 가치가 없는 콘텐츠를 쉽게 제거할 수 있습니다.

Exchange Online사서함에 보존 태그 및 보존 정책을 적용하는 방법의 빠른 개요를 보려면 이 [비디오](http://go.microsoft.com/fwlink/?linkid=825854)를 시청하세요.

MRM을 관리하는 단계별 절차를 찾고 있나요? [메시징 레코드 관리 절차](messaging-records-management-procedures-exchange-2013-help.md) 항목을 참조하세요.

**목차**

메시징 레코드 관리 전략

보존 태그

보존 정책

관리되는 폴더 도우미

보존

## 메시징 레코드 관리 전략

Exchange 2013 및 Exchange Online의 MRM은 *보존 태그*와 *보존 정책*을 사용하여 수행됩니다. 이러한 각 보존 기능에 대한 자세한 내용을 설명하기 전에 전체 MRM 전략에서 기능이 어떻게 사용되는지를 살펴보는 것이 중요합니다. 이 전략은 다음을 기반으로 합니다.

  - RPT(*보존 정책 태그*)를 받은 편지함 및 지운 편지함과 같은 기본 폴더에 할당

  - DPT(*기본 정책 태그*)를 사서함에 적용하여 태그가 지정되지 않은 모든 항목의 보존 관리

  - 사용자가 *개인 태그*를 사용자 지정 폴더 및 개별 항목에 할당하도록 허용.

  - 사용자의 받은 편지함 관리 및 저장 습관에서 MRM 기능을 분리. 사용자는 보존 요구 사항에 따라 관리된 폴더의 메시지를 저장할 필요가 없습니다. 개별 메시지는 해당 메시지가 위치한 폴더에 적용되는 것과 다른 보존 태그를 가질 수 있습니다.

다음 그림에서는 이 전략 구현과 관련된 작업을 보여 줍니다.

![메시징 보존에 보존 정책 사용](images/Dd297955.429b51d5-51b8-4816-b8a4-221e0915d0c0(EXCHG.150).gif "메시징 보존에 보존 정책 사용")

맨 위로 이동

## 보존 태그

위의 그림과 같이 보존 태그는 전자 메일 메시지 및 음성 메일과 같은 개별 항목 및 폴더에 보존 설정을 적용하는 데 사용됩니다. 이러한 설정은 사서함에 메시지가 남아 있는 기간 및 메시지가 지정된 보존 기간에 도달한 경우 수행되는 작업을 지정합니다. 메시지가 보존 기간에 도달하면 메시지는 사용자의 원본 위치 보관함으로 이동되거나 삭제됩니다.

![보존 태그의 설정](images/Dd297955.936edd6a-8bc4-4c03-94a3-c240ffe7dd6a(EXCHG.150).png "보존 태그의 설정")

보존 태그를 사용하면 사용자가 보존할 사서함 폴더 및 개별 항목에 태그를 지정할 수 있습니다. 사용자는 더 이상 메시지 보존 요구 사항에 따라 관리자가 프로비전하는 관리되는 폴더의 항목을 저장할 필요가 없습니다.

## 보존 태그의 유형

보존 태그는 해당 태그를 적용할 수 있는 사용자와 사서함에서 적용될 수 있는 위치에 따라 다음 세 가지 유형으로 분류됩니다.


<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>보존 태그의 유형</th>
<th>Applied...</th>
<th>적용한 사람...</th>
<th>사용 가능한 동작...</th>
<th>세부 정보</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>DPT(기본 정책 태그)</p></td>
<td><p>전체 사서함에 자동으로</p>
<p>DPT는 <em>태그가 지정되지 않은</em> 항목에 적용됩니다. 이러한 항목은 보존 태그가 직접 또는 폴더에서 상속에 의해 적용되지 않은 사서함 항목입니다.</p></td>
<td><p>관리자</p></td>
<td><ul>
<li><p>보관함으로 이동</p></li>
<li><p>삭제 및 복구 허용</p></li>
<li><p>영구 삭제</p></li>
</ul></td>
<td><p>사용자는 사서함에 적용된 DPT를 변경할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p>RPT(보존 정책 태그)</p></td>
<td><p>기본 폴더에 자동으로</p>
<p>기본 폴더는 모든 사서함에서 자동으로 만들어지는 폴더입니다. 예를 들면 다음과 같습니다. <strong>받은 편지함</strong>, <strong>지운 편지함</strong> 및 <strong>보낸 편지함</strong><a href="default-folders-that-support-retention-policy-tags-exchange-2013-help.md">보존 정책 태그를 지 원하는 기본 폴더</a>에서 지원되는 기본 폴더 목록을 참조하세요.</p></td>
<td><p>관리자</p></td>
<td><ul>
<li><p>삭제 및 복구 허용</p></li>
<li><p>영구 삭제</p></li>
</ul></td>
<td><p>사용자가 기본 폴더에 적용된 RPT를 변경할 수 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p>개인 태그</p></td>
<td><p>항목 및 폴더에 수동으로</p>
<p>사용자가 받은 편지함 규칙을 통해 태그 지정을 자동화하여 특정 태그가 있는 폴더로 메시지를 이동하거나 메시지에 개인 태그를 적용할 수 있습니다.</p></td>
<td><p>사용자</p></td>
<td><ul>
<li><p>보관함으로 이동</p></li>
<li><p>삭제 및 복구 허용</p></li>
<li><p>영구 삭제</p></li>
</ul></td>
<td><p>개인 태그를 사용하여 항목이 보존되는 기간을 결정할 수 있습니다. 예를 들어 사서함에 7년 후에 항목을 삭제하는 DPT가 있지만 사용자는 뉴스레터 및 자동 알림 등의 항목을 3일 후에 삭제하는 개인 태그를 적용하여 이러한 항목에 대해 예외를 만들 수 있습니다.</p></td>
</tr>
</tbody>
</table>


## 개인 태그에 대한 자세한 정보

개인 태그는 Outlook 2010 및 Outlook Web App 사용자가 보존 정책의 일환으로 사용할 수 있습니다. 다음 그림과 같이 Outlook 2010 및 Outlook Web App에서 **아카이브로 이동** 작업이 적용된 개인 태그는 **보관 정책**으로 나타나고, **삭제 및 복구 허용** 또는 **영구 삭제** 작업이 적용된 개인 태그는 **보존 정책**으로 나타납니다.

![Outlook 2010 및 Outlook Web App의 개인 태그](images/Dd297955.2dbaee13-fdd0-4c30-b821-e662ce2587bb(EXCHG.150).gif "Outlook 2010 및 Outlook Web App의 개인 태그")

사용자를 만든 폴더 또는 개별 항목에 개인 태그를 적용할 수 있습니다. 개인 태그가 적용된 메시지는 항상 개인 태그의 설정에 따라 처리됩니다. 사용자는 메시지에 개인 태그를 적용하여 해당 사서함에 적용된 DPT 또는 RPT에 지정된 설정보다 더 일찍 또는 늦게 메시지를 이동 또는 삭제할 수 있습니다. 보존이 사용되지 않도록 설정된 개인 태그를 만들 수도 있습니다. 이렇게 하면 항목이 절대 보관함으로 이동되지 않거나 만료되지 않도록 태그를 지정할 수 있습니다.


> [!NOTE]  
> 보관 정책은 기본 폴더, 사용자가 만든 폴더나 하위 폴더, 개별 항목에 적용할 수 있습니다. 보존 정책은 사용자가 만든 폴더나 하위 폴더, 개별 항목(기본 폴더의 하위 폴더 및 항목 포함)에 적용할 수 있지만 기본 폴더에는 적용할 수 없습니다.



사용자는 EAC(Exchange 관리 센터)를 사용하여 보존 정책에 연결되지 않은 개인 태그를 추가로 선택할 수도 있습니다. 그런 후에 선택한 태그를 Outlook 2010 및 Outlook Web App에서 사용할 수 있습니다. 사용자가 EAC에서 태그를 추가로 선택할 수 있으려면 사용자의 역할 할당 정책에 [MyRetentionPolicies 역할](myretentionpolicies-role-exchange-2013-help.md)을 추가해야 합니다. 사용자와 관련된 역할 할당 정책에 대한 자세한 내용은 [관리 역할 할당 정책 이해 (영문)](understanding-management-role-assignment-policies-exchange-2013-help.md)를 참조하십시오. 사용자가 개인 태그를 추가로 선택할 수 있게 하면 Exchange 조직의 모든 개인 태그를 사용할 수 있게 됩니다.


> [!NOTE]  
> 개인 태그는 고급 기능입니다. 이러한 태그를 포함하는 정책이 적용된 사서함의 경우(또는 사용자가 사서함에 태그를 추가한 경우) Exchange Enterprise CAL(클라이언트 액세스 라이선스)이 있어야 합니다.



설정

## 보존 기간

보존 태그를 사용하도록 설정할 때는 태그의 보존 기간을 지정해야 합니다. 이 기간은 사용자의 사서함에 도착한 후 메시지를 보존하는 날짜 수를 나타냅니다.

되풀이하지 않는 항목(예: 전자 메일 메시지)의 보존 기간은 끝 날짜가 있는 항목 또는 되풀이 항목(예: 모임 및 작업)과 다르게 계산됩니다. 항목 유형별 보존 기간 계산 방법에 대한 자세한 내용은 [보존 기간 계산 방법](how-retention-age-is-calculated-exchange-2013-help.md)을 참조하십시오.

보존을 사용하지 않도록 설정한 보존 태그를 만들거나 이미 생성된 태그를 사용하지 않도록 설정할 수도 있습니다. 사용하지 않도록 설정된 태그를 적용한 메시지는 처리되지 않으므로 보존 작업이 이루어지지 않습니다. 결과적으로 사용자는 사용하지 않도록 설정된 개인 태그를 **이동 안 함** 태그나 **삭제 안 함** 태그로 사용하여 DPT 또는 그렇지 않으면 메시지에 적용될 RPT를 재정의할 수 있습니다.

## 보존 작업

보존 태그를 만들거나 구성할 때 사서함 항목이 보존 기간에 도달하는 경우 다음 중에서 수행할 보존 작업을 하나 선택할 수 있습니다.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>보존 작업</th>
<th>수행 작업...</th>
<th>예외...</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>보관함으로 이동</strong> 1</p></td>
<td><ul>
<li><p>메시지를 사용자의 보관 사서함으로 이동</p></li>
<li><p>DPT 및 개인 태그에만 사용 가능</p></li>
</ul>
<p>보관에 대한 자세한 내용은 다음을 참조하세요.</p>
<ul>
<li><p><a href="in-place-archiving-in-exchange-2013-exchange-2013-help.md">전체에서 Exchange 2013의 보관</a></p></li>
<li><p><a href="https://technet.microsoft.com/ko-kr/library/dn922147(v=exchg.150)">Exchange Online의 보관 사서함</a></p></li>
</ul></td>
<td><ul>
<li><p>사용자에게 보관 사서함이 없는 경우에는 아무 작업도 수행되지 않습니다.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>삭제 및 복구 허용</strong></p></td>
<td><ul>
<li><p>사용자가 지운 편지함 폴더를 비울 때의 동작을 에뮬레이션합니다.</p></li>
<li><p>항목은 사서함의 <a href="recoverable-items-folder-exchange-2013-help.md">복구 가능한 항목 폴더</a>로 이동된 후 <em>삭제된 항목 보존</em> 기간까지 보존됩니다.</p></li>
<li><p>사용자는 Outlook 또는 Outlook Web App의 <strong>삭제된 항목 복구</strong> 대화 상자를 사용하여 항목을 복구할 또 다른 기회를 얻게 됩니다.</p></li>
</ul></td>
<td><ul>
<li><p>삭제된 항목 보존 기간을 0일로 설정하면 항목이 영구적으로 삭제됩니다. 자세한 내용은 <a href="https://technet.microsoft.com/ko-kr/library/dn163584(v=exchg.150)">Exchange Online 사서함에 대 한 변경 얼마나 오래 영구적으로 삭제 된 항목 보관 됩니다.</a>을 참조하세요.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>영구 삭제</strong></p></td>
<td><ul>
<li><p>메시지를 영구적으로 삭제합니다.</p></li>
<li><p>영구적으로 삭제한 메시지는 복구할 수 없습니다.</p></li>
</ul></td>
<td><ul>
<li><p>사서함에 <a href="in-place-hold-and-litigation-hold-exchange-2013-help.md">원본 위치 유지 및 소송 보존</a> 소송 보존이 적용되면 항목은 보류 매개 변수에 따라 복구할 수 있는 항목 폴더에 보존됩니다. <a href="in-place-ediscovery-exchange-2013-help.md">원본 위치 eDiscovery</a>에서는 이러한 항목이 여전히 검색 결과에 반환됩니다.</p>
<p></p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>보존 기간이 지난 것으로 표시</strong></p></td>
<td><ul>
<li><p>메시지를 만료된 것으로 표시합니다. Outlook 2010 이상 및 Outlook Web App에서는 만료된 것으로 표시된 항목이 '이 항목은 만료되었습니다.’ ‘이 항목은 0일 후에 만료됩니다.’로 시작하는 알림과 함께 표시됩니다. Outlook 2007에서는 만료된 것으로 표시된 항목이 취소선 텍스트를 사용하여 표시됩니다.</p></li>
</ul></td>
<td><p>해당 없음</p></td>
</tr>
</tbody>
</table>



> [!NOTE]  
> 1Exchange 하이브리드 배포에서 온-프레미스 기본 사서함에 대해 클라우드 기반 보관 사서함을 사용하도록 설정할 수 있습니다. 온-프레미스 사서함에 보관 정책을 할당하면 항목이 클라우드 기반 보관함으로 이동됩니다. 항목이 보관 사서함으로 이동되면 온-프레미스 사서함에 해당 복사본이 유지되지 않습니다. 온-프레미스 사서함에 보류 상태가 적용되면 보관 정책은 항목을 클라우드 기반 보관 사서함 항목으로 이동하여 보류로 지정된 기간 동안 유지되도록 합니다.



보존 태그를 만드는 방법에 대한 자세한 내용은 [보존 정책 만들기](create-a-retention-policy-exchange-2013-help.md)를 참조하십시오.

맨 위로 이동

## 보존 정책

하나 이상의 보존 태그를 사서함에 적용하려면 태그를 보존 정책에 추가한 다음 정책을 사서함에 추가해야 합니다. 사서함에는 둘 이상의 보존 정책을 적용할 수 없습니다. 보존 태그는 언제든지 보존 정책에 연결하거나 해제할 수 있으며, 변경 사항은 정책이 적용되는 모든 사서함에 자동으로 적용됩니다.

보존 정책에는 다음과 같은 보존 태그가 포함될 수 있습니다.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>보존 태그 유형</th>
<th>정책의 태그</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>DPT(기본 정책 태그)</p></td>
<td><ul>
<li><p><strong>보관함으로 이동</strong> 작업이 있는 DPT 하나</p></li>
<li><p><strong>삭제 및 복구 허용</strong> 또는 <strong>영구 삭제</strong> 작업이 할당된 DPT 하나</p></li>
<li><p><strong>삭제 및 복구 허용</strong> 또는 <strong>영구 삭제</strong> 작업이 포함된 음성 사서함 메시지에 대한 DPT 하나</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>RTP(보존 정책 태그)</p></td>
<td><ul>
<li><p>지원되는 각 기본 폴더에 대한 RPT 하나</p>

> [!NOTE]  
> 동일한 보존 정책에는 특정 기본 폴더(예: <STRONG>지운 편지함</STRONG>)에 대해 둘 이상의 RPT를 연결할 수 없습니다.


</li>
</ul></td>
</tr>
<tr class="odd">
<td><p>개인 태그</p></td>
<td><ul>
<li><p>개인 태그의 번호</p></li>
</ul>

> [!TIP]  
> 하나의 정책에 개인 태그가 여러 개 있으면 사용자에게 혼동을 일으킬 수 있습니다. 보존 정책에 개인 태그를 10개 이하로 추가하는 것이 좋습니다.


</td>
</tr>
</tbody>
</table>



> [!NOTE]  
> 보존 정책에 보존 태그를 연결할 필요가 없더라도 이 시나리오는 사용하지 않는 것이 좋습니다. 보존 정책이 포함된 사서함에 연결된 보존 태그가 없는 경우 사서함 항목이 만료되지 않을 수 있습니다.



보존 정책은 보관 태그(개인 보관 사서함으로 항목을 이동시키는 태그) 및 삭제 태그(항목을 삭제하는 태그)를 둘 다 포함할 수 있습니다. 사서함 항목에도 두 가지 태그를 모두 적용할 수 있습니다. 보관 사서함에는 별도의 보존 정책이 없습니다. 기본 사서함과 보관 사서함에는 동일한 보존 정책이 적용됩니다.

보존 정책을 만들고자 할 때는 보관 태그와 삭제 태그를 둘 다 포함시킬지 여부를 고려해야 합니다. 앞에서 설명한 것처럼 보존 정책은 **보관함으로 이동** 작업을 사용하는 DPT 하나와 **삭제 및 복구 허용** 또는 **영구 삭제** 작업을 사용하는 DPT 하나를 가질 수 있습니다. **보관함으로 이동** 작업을 사용하는 DPT는 삭제 작업을 사용하는 DPT보다 보존 기간이 짧아야 합니다. 예를 들어 **보관함으로 이동** 작업을 사용하는 DPT를 사용하여 2년 동안 보관 사서함에 항목을 이동시킬 수 있으며, 삭제 작업을 사용하는 DPT를 사용하여 7년 동안 사서함에서 항목을 제거할 수 있습니다. 기본 및 보관 사서함 모두의 항목은 7년 후에 삭제됩니다.

보존 정책과 관련된 관리 작업 목록은 [메시징 레코드 관리 절차](messaging-records-management-procedures-exchange-2013-help.md)를 참조하십시오.

## 기본 보존 정책

Exchange 설치 프로그램에서는 보존 정책 **기본 MRM 정책**을 만듭니다. Exchange Online의 새 사서함에 기본 MRM 정책이 자동으로 적용됩니다 . Exchange Server에서 새 사용자에 대 한 보관함을 만들고 보존 정책을 지정하지 않은 경우 정책이 자동으로 적용됩니다.

보존 기간 또는 보존 작업을 변경하여 기본 MRM 정책에 포함된 태그를 수정하거나, 태그를 사용하지 않도록 설정하거나, 정책에서 태그를 추가하거나 제거하여 정책을 수정할 수 있습니다. 다음번에 관리되는 폴더 도우미가 처리할 때 사서함에 업데이트된 정책이 적용됩니다.

정책에 연결된 보존 태그 목록을 비롯한 자세한 내용을 보려면 [Exchange Online 및 Exchange 서버에서 기본 보존 정책](default-retention-policy-in-exchange-online-and-exchange-server-exchange-2013-help.md)을 참조하세요.

맨 위로 이동

## 관리되는 폴더 도우미

사서함 서버에서 실행되는 사서함 도우미인 관리되는 폴더 도우미는 보존 정책이 적용된 사서함을 처리합니다.

관리되는 폴더 도우미는 사서함의 항목을 조사하고 보존이 적용되는지 여부를 결정하여 보존 정책을 적용합니다. 그런 다음 적절한 보존 태그로 보존이 적용되는 항목을 스탬프 처리하고 보존 기간이 지난 항목에서 지정된 보존 작업을 수행합니다.

관리되는 폴더 도우미는 스로틀 기반 도우미입니다. 스로틀 기반 도우미는 항상 실행되며 예약하지 않아도 됩니다. 사용하는 시스템 자원은 제한되어 있습니다. 관리되는 폴더 도우미가 일정 기간 내에 사서함 서버의 모든 사서함을 처리하도록 구성할 수 있습니다(*작업 주기*라고도 함). 또한 이 도우미는 처리되는 사서함 목록을 지정된 간격(*작업 주기 검사점*이라고도 함)에 따라 새로 고칩니다. 새로 고침 과정에서 도우미는 새로 만들어지거나 이동한 사서함을 큐에 추가합니다. 또한 오류로 인해 성공적으로 처리되지 않은 기존 사서함의 우선 순위를 재설정하여 우선 순위가 높은 사서함을 같은 작업 주기에서 처리될 수 있도록 큐에서 높은 위치로 이동시킵니다.

[Start-ManagedFolderAssistant](https://technet.microsoft.com/ko-kr/library/aa998864\(v=exchg.150\)) cmdlet을 사용하여 도우미를 수동으로 트리거한 후 지정된 사서함을 처리하도록 할 수도 있습니다. 자세한 내용은 [관리 되는 폴더 도우미를 구성 합니다.](configure-the-managed-folder-assistant-exchange-2013-help.md)을 참조하십시오.


> [!NOTE]  
> 관리되는 폴더 도우미는 보존이 적용되지 않는 메시지에서 보존 태그를 사용하지 않도록 설정하여 지정되는 작업을 수행하지 않습니다. 보존 태그를 사용하지 않도록 설정하여 해당 태그를 사용하는 항목이 일시적으로 처리되지 않도록 할 수도 있습니다.



## 폴더 간에 항목 이동

하나의 폴더에서 다른 폴더로 이동된 사서함 항목은 이동된 폴더에 적용되는 태그를 상속받습니다. 항목이 태그가 할당되지 않은 폴더로 이동된 경우 DPT가 항목에 적용됩니다. 항목에 명시적으로 할당된 태그가 있는 경우 해당 태그가 폴더 수준 태그 또는 기본 태그보다 우선합니다.

## 보관 폴더에 보존 태그 적용

사용자가 보관 폴더에 개인 태그를 적용할 경우 이름이 같고 태그가 다른 폴더가 기본 사서함에 있으면 해당 보관 폴더의 태그가 기본 사서함의 태그와 일치하도록 변경됩니다. 이것은 사용자의 기본 사서함에 있는 동일한 폴더와는 다른 만료 동작을 갖는 보관 폴더의 항목을 혼동하지 않게 하기 위해 기본적으로 제공되는 기능입니다. 예를 들어 기본 사서함에 *삭제 - 3년* 태그가 있는 Project Contoso라는 폴더가 있으며, Project Contoso 폴더가 보관 사서함에도 있는 경우 사용자가 1년 후에 폴더의 항목을 삭제하기 위해 *삭제 - 1년* 개인 태그를 적용하면 사서함이 다시 처리될 때 해당 폴더는 삭제 - 3년 태그로 되돌아갑니다.

## 보존 정책에서 보존 태그 제거 또는 삭제

보존 태그가 사서함에 적용된 보존 정책에서 제거되는 경우 해당 태그는 더 이상 사용자가 사용할 수 없으며 사서함의 항목에 적용할 수 없습니다.

해당 태그로 스탬프 처리된 기존 항목은 이러한 설정에 따라 관리되는 폴더 도우미가 계속 처리하고 태그에 지정된 보존 작업이 해당 메시지에 적용됩니다.

하지만 태그를 삭제하는 경우 Active Directory에 저장된 태그 정의는 제거됩니다. 그러면 관리되는 폴더 도우미가 사서함의 모든 항목을 처리하고 제거한 태그가 적용된 항목은 다시 스탬프 처리합니다. 사서함 및 메시지 수에 따라 이 프로세스는 제거한 태그가 포함된 보존 정책이 있는 사서함을 포함하는 모든 사서함 서버에서 리소스를 많이 사용할 수 있습니다.


> [!IMPORTANT]
> 보존 태그가 보존 정책에서 제거되는 경우 해당 태그가 적용된 기존 사서함 항목은 태그의 설정에 따라 계속 만료됩니다. 태그의 설정이 항목에 적용되지 않도록 방지하려면 해당 태그를 삭제해야 합니다. 태그를 삭제하면 해당 태그가 포함된 모든 보존 정책에서 이 태그가 제거됩니다.



## 보존 태그를 사용하지 않도록 설정

보존 태그를 사용하지 않도록 설정하면 관리되는 폴더 도우미는 태그가 적용된 항목을 무시합니다. 보존을 사용하지 않도록 설정된 보존 태그를 포함한 항목은 지정된 보존 작업에 따라 이동 또는 삭제되지 않습니다. 이러한 항목은 계속 태그가 지정된 항목으로 간주되기 때문에 DPT가 해당 항목에 적용되지 않습니다. 예를 들어 보존 태그 설정 문제를 해결하려는 경우 일시적으로 보존 태그를 사용하지 않도록 설정하여 관리되는 폴더 도우미가 해당 태그가 있는 메시지를 처리하지 않도록 중지할 수 있습니다.


> [!NOTE]  
> 사용하지 않도록 설정된 보존 태그의 보존 기간은 사용자에게 <STRONG>없음</STRONG>으로 표시됩니다. 사용자가 절대 삭제하지 않을 것으로 판단되는 항목에 태그를 지정한 경우, 나중에 그 태그를 사용하도록 설정하면 삭제하려고 하지 않았던 항목이 예기치 않게 삭제될 수 있습니다. <STRONG>보관함으로 이동</STRONG> 작업을 사용하는 태그의 경우도 마찬가지입니다.



맨 위로 이동

## 보존

사용자가 근무 중 잠시 자리를 비우고 전자 메일에 액세스할 수 없는 경우 사용자가 다시 돌아와서 전자 메일에 액세스할 수 있기 전까지 보존 설정을 새 메시지에 적용할 수 없습니다. 보존 정책에 따라 메시지가 사용자의 개인 보관함에서 삭제되거나 이동될 수 있습니다. 사서함을 보존 상태로 두면 지정된 기간 동안 사서함이 처리되지 않도록 보존 정책을 일지적으로 중단할 수 있습니다. 사서함을 보존 상태로 두는 경우 보존이 시작되고 끝나도록 예약된 시간을 포함하여 보존에 대해 사서함 사용자(또는 사서함에 액세스할 권한이 있는 다른 사용자)에게 알리는 보존 설명을 추가할 수도 있습니다. 보존 설명은 지원되는 Outlook 클라이언트에서 표시됩니다. 사용자의 기본 설정 언어로 보존 설명을 지역화할 수도 있습니다.


> [!NOTE]  
> 사서함을 보존 상태로 두면 사서함 저장소 할당량이 처리되는 방법에 영향을 주지 않습니다. 사서함 사용 및 해당 사서함 할당량에 따라 사용자가 휴가 중이거나 연장 기간 동안 전자 메일에 액세스할 수 없는 경우 사용자에 대한 사서함 저장소 할당량을 일시적으로 늘리는 것을 고려하십시오. 사서함 저장소 할당량에 대한 자세한 내용은 <A href="configure-storage-quotas-for-a-mailbox-exchange-2013-help.md">사서함에 대 한 저장소 할당량 구성</A>를 참조하십시오.



장기간 부재 중인 동안 사용자에게 전자 메일 양이 크게 증가할 수 있습니다. 전자 메일의 양과 부재 중인 기간에 따라 사용자가 메시지를 정렬하는 데 몇 주가 걸릴 수 있습니다. 이러한 경우 사서함을 보존 상태에서 제거하기 전에 사용자가 메일을 확인하는 데 걸리는 추가 시간을 고려하십시오.

조직에서 MRM을 구현한 적이 없고 사용자가 해당 기능을 잘 모르는 경우 MRM 배포 초기 *웜업 및 학습* 단계 동안 보존을 사용할 수도 있습니다. 사용자가 태그를 지정하기 전에 항목이 이동하거나 삭제될 위험 없이 보존 정책을 만들어 배포하고 사용자에게 해당 정책에 대한 교육을 시킬 수 있습니다. 웜업 및 교육 기간이 종료되기 며칠 전에 사용자에게 웜업 마감 날짜를 알려야 합니다. 마감 후에는 사용자 사서함에서 보존을 제거하여 관리되는 폴더 도우미가 사서함 항목을 처리하고 지정된 보존 작업을 수행하도록 할 수 있습니다.

사서함을 보존 상태로 두는 방법에 대한 자세한 내용은 [사서함 보존에 원본 위치 유지](place-a-mailbox-on-retention-hold-exchange-2013-help.md)를 참조하십시오.

맨 위로 이동
