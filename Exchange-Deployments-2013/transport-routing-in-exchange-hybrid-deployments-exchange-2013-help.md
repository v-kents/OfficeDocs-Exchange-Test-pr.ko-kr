﻿---
title: 'Exchange 하이브리드 배포의 전송 라우팅: Exchange 2013 Help'
TOCTitle: Exchange 하이브리드 배포의 전송 라우팅
ms:assetid: 36c2cea3-2e2f-40ac-88bd-7e1b6bd27828
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ659050(v=EXCHG.150)
ms:contentKeyID: 50484635
ms.date: 01/10/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Exchange 하이브리드 배포의 전송 라우팅

 

_<strong>적용 대상:</strong>Exchange Server 2013, Exchange Server 2016_

_<strong>마지막으로 수정된 항목:</strong>2016-07-29_

이 항목에서는 인터넷을 통해 주고받는 인바운드 메시지 및 아웃바운드 메시지용 라우팅 옵션에 대해 설명합니다.


> [!IMPORTANT]
> 모든 서버, 서비스 또는 장치를 SMTP 트래픽을 처리하거나 수정하는 온-프레미스 Exchange 서버와 Office 365 사이에 두지 마십시오. 온-프레미스 Exchange 조직과 Office 365 간의 보안 메일 흐름은 조직 간 전송된 메시지에 포함된 정보에 따라 다릅니다. 수정하지 않고 TCP 포트 25에서 SMTP 트래픽을 허용하는 방화벽이 지원됩니다. 서버, 서비스 또는 장치가 온-프레미스 Exchange 조직과 Office 365 간에 보낸 메시지를 처리하는 경우 이 정보가 제거됩니다. 이 경우 메시지가 더 이상 조직 내부로 간주되지 않으며 및 스팸 방지 필터링, 전송 및 저널 규칙, 적용되지 않을 수 있는 기타 정책을 따르게 됩니다.




> [!NOTE]
> 이 항목의 예에는 하이브리드 배포에 Edge 전송 서버 추가가 포함되어 있지 않습니다. 온-프레미스 조직, Exchange Online 조직과 인터넷 간의 라우팅 메시지는 Edge 전송 서버를 추가해도 변경되지 않습니다. 온-프레미스 조직 내에서만 라우팅이 변경됩니다. 하이브리드 배포에 Edge 전송 서버를 추가하는 방법에 대한 자세한 내용은 <A href="edge-transport-servers-with-hybrid-deployments-exchange-2013-help.md">하이브리드 배포의 Edge 전송 서버</A>를 참조하십시오.



## 인터넷에서 보낸 인바운드 메시지

하이브리드 배포 계획 및 구성의 일부로, 인터넷 사용자가 보낸 모든 메시지를 Exchange Online 조직을 통해 라우팅할 것인지 아니면 온-프레미스 조직을 통해 라우팅할 것인지를 결정해야 합니다. 인터넷 사용자가 보낸 모든 메시지는 처음에는 선택한 조직에 배달된 다음 받는 사람의 사서함이 있는 위치에 따라 라우팅됩니다. 메시지가 Exchange Online 조직을 통해 라우팅되도록 할 것인지 또는 온-프레미스 조직을 통해 라우팅되도록 할 것인지는 준수 정책을 두 조직에 보낸 모든 메시지에 적용할 것인지 여부, 각 조직에 있는 사서함 수 등을 포함하여 여러 가지 요소에 의해 결정됩니다.

온-프레미스 및 Exchange Online 조직의 받는 사람에게 전송되는 경로 메시지는 하이브리드 배포에서 MX 레코드를 구성하는 방법에 따라 달라집니다. 기본 방법은 Office 365의 EOP(Exchange Online Protection)을 가리키도록 MX 레코드를 구성하는 것입니다. 이렇게 구성하면 스팸을 가장 정확하게 필터링할 수 있기 때문입니다. 하이브리드 구성 마법사는 온-프레미스 또는 Exchange Online 조직에 대해 인바운드 인터넷 메시지에 대한 라우팅을 구성하지 않습니다. 인바운드 인터넷 메일의 배달 방법을 변경하려면 MX 레코드를 수동으로 구성해야 합니다.

  - **Office 365의 Exchange Online Protection 서비스를 가리키도록 MX 레코드를 변경하는 경우**   하이브리드 배포에 권장되는 구성입니다. 양 조직의 받는 사람에게 전송되는 모든 메시지는 먼저 Exchange Online 조직을 통해 라우팅됩니다. 온-프레미스 조직에 있는 받는 사람에게 보낸 메시지는 먼저 Exchange Online 조직을 통해 라우팅된 다음 온-프레미스 조직의 받는 사람에게 배달됩니다. 이 라우팅 방법은 온-프레미스 조직보다 Exchange Online 조직에 받는 사람이 더 많이 있는 경우에 권장됩니다. 이 구성 옵션은 Exchange Online Protection을 통해 스팸을 검색하고 차단하려는 경우에 필요합니다.

  - **온-프레미스 조직을 가리키도록 MX 레코드를 유지하는 경우**   양 조직의 받는 사람에게 전송되는 모든 메시지는 먼저 온-프레미스 조직을 통해 라우팅됩니다. Exchange Online에 있는 받는 사람에게 보낸 메시지는 먼저 온-프레미스 조직을 통해 라우팅된 다음 Exchange Online의 받는 사람에게 배달됩니다. 이러한 라우팅은 조직에서 주고받은 메시지를 저널링 솔루션으로 점검해야 하는 준수 정책이 있는 조직에 유용합니다. 이 옵션을 선택하는 경우 Exchange Online Protection 기능이 스팸 메시지를 효과적으로 검색할 수 없게 됩니다.

자세한 내용은 [Exchange Online 및 Office 365 (개요)에 대 한 메일 흐름 모범 사례](https://technet.microsoft.com/ko-kr/library/jj937232\(v=exchg.150\))를 참조하세요.

아래에서 인터넷 사용자로부터 온-프레미스 및 Exchange Online 받는 사람에게 보낸 메시지를 라우팅할 방법에 일치하는 섹션을 읽어 보세요. 각 섹션에서 "온-프레미스 Exchange 서버"는 Exchange 2013 클라이언트 액세스 서버 또는 Exchange 2016 사서함 서버일 수 있습니다.

## 들어오는 인터넷 메시지를 Exchange Online 조직을 통해 라우팅

다음 단계 및 다이어그램은 Office 365 조직의 EOP 서비스를 가리키도록 MX 레코드를 설정한 경우, 하이브리드 배포에서 발생하는 인바운드 메시지 경로를 보여줍니다. 중앙 집중식 메일 전송 사용의 선택 여부에 따라 메시지 경로가 달라집니다.


> [!IMPORTANT]
> 처음 EOP로 배달된 다음 Exchange Online 조직으로 라우팅된 메시지를 받는 각 온-프레미스 사서함에 대해 EOP 라이선스를 구입해야 할 수도 있습니다. 자세한 내용은 Microsoft 재판매인에게 문의하십시오.



중앙 집중식 메일 전송이 **사용 안 함**(기본 구성)으로 설정된 경우, 들어오는 인터넷 메시지는 하이브리드 배포에서 다음과 같이 라우팅됩니다.

1.  인바운드 메시지는 인터넷 보낸 사람으로부터 받는 사람 ji-min@contoso.com 및 yejoon@contoso.com으로 전송됩니다. 조지민 님의 사서함은 온-프레미스 조직의 Exchange 사서함 서버에 있습니다. 나예준 님의 사서함은 Exchange Online에 있습니다.

2.  받는 사람 둘 다 contoso.com 전자 메일 주소를 가지고 있고 contoso.com의 MX 레코드는 EOP를 가리키기 때문에 해당 메시지는 EOP로 배달됩니다.

3.  EOP는 받는 사람 둘 다에 대한 메시지를 Exchange Online으로 라우팅합니다.

4.  Exchange Online은 메시지에서 바이러스를 검색하고 각 받는 사람에 대한 조회를 수행합니다. 조회를 통해 조지민 님의 사서함이 온-프레미스 조직에 있고, 나예준 님의 사서함이 Exchange Online 조직에 있는지 확인합니다.

5.  Exchange Online은 메시지를 두 개의 복사본으로 분할합니다. 메시지 복사본 하나는 David의 사서함으로 배달됩니다.

6.  두 번째 복사본은 Exchange Online에서 다시 EOP로 전송됩니다.

7.  EOP는 온-프레미스 조직의 온-프레미스 Exchange 서버로 메시지를 보냅니다.

8.  Exchange에서 조지민 님의 사서함으로 배달된 Exchange 사서함 서버로 메시지를 보냅니다.

**중앙 집중식 메일 전송을 사용하지 않고(기본 구성) 온-프레미스 및 Exchange Online 조직에 대해 Exchange Online 조직을 통해 메일 라우팅**

![EXO에 대한 중앙 집중식 인바운드](images/JJ659050.f98341e0-088d-49f0-bf8e-09f35255bf9e(EXCHG.150).png "EXO에 대한 중앙 집중식 인바운드")

중앙 집중식 메일 전송이 **사용**으로 설정된 경우, 들어오는 인터넷 메시지는 하이브리드 배포에서 다음과 같이 라우팅됩니다.

1.  인바운드 메시지는 인터넷 보낸 사람으로부터 받는 사람 ji-min@contoso.com 및 yejoon@contoso.com으로 전송됩니다. 조지민 님의 사서함은 온-프레미스 조직의 Exchange 사서함 서버에 있습니다. 나예준 님의 사서함은 Exchange Online에 있습니다.

2.  받는 사람 둘 다 contoso.com 전자 메일 주소를 가지고 있고 contoso.com의 MX 레코드는 EOP 회사를 가리키기 때문에 해당 메시지는 EOP로 배달되어 바이러스 검색이 수행됩니다.

3.  중앙 집중식 메일 전송이 사용되므로, EOP는 받는 사람 모두에 대한 메시지를 온-프레미스 Exchange 클라이언트 액세스 서버로 라우팅합니다.

4.  온-프레미스 Exchange 서버는 각 받는 사람에 대해 조회를 수행합니다. 조회를 통해 조지민 님의 사서함이 온-프레미스 조직에 있고, 나예준 님의 사서함이 Exchange Online 조직에 있는지 확인합니다.

5.  온-프레미스 Exchange 서버는 메시지를 두 개의 복사본으로 분할합니다. 메시지 복사본 하나는 온-프레미스 Exchange 사서함 서버에 있는 조지민 님의 사서함으로 배달됩니다.

6.  두 번째 복사본은 온-프레미스 Exchange 서버에서 다시 EOP로 전송됩니다.

7.  EOP는 메시지를 Exchange Online으로 전송합니다.

8.  Exchange는 메시지를 나예준 님의 사서함으로 배달합니다.

**중앙 집중식 메일 전송을 사용하여 온-프레미스 및 Exchange Online 조직에 대해 Exchange Online 조직을 통해 메일 라우팅**

![인바운드 EXO, 중앙 집중식 사용](images/JJ659050.062422d5-9cb6-42c2-9ec0-31962cd7ada6(EXCHG.150).png "인바운드 EXO, 중앙 집중식 사용")

## 들어오는 인터넷 메시지를 온-프레미스 조직을 통해 라우팅

다음 단계 및 다이어그램은 온-프레미스 조직을 가리키도록 MX 레코드를 유지하는 경우, 하이브리드 배포에서 발생할 인바운드 인터넷 메시지 경로를 보여줍니다.

1.  인바운드 메시지는 인터넷 보낸 사람으로부터 받는 사람 ji-min@contoso.com 및 yejoon@contoso.com으로 전송됩니다. 조지민 님의 사서함은 온-프레미스 조직의 Exchange 사서함 서버에 있습니다. 나예준 님의 사서함은 Exchange Online에 있습니다.

2.  받는 사람이 둘 다 contoso.com 전자 메일 주소를 사용하고 contoso.com의 MX 레코드는 온-프레미스 조직을 가리키므로 해당 메시지는 온-프레미스 Exchange 서버로 배달됩니다.

3.  온-프레미스 Exchange 서버는 온-프레미스 글로벌 카탈로그 서버를 사용하여 각 받는 사람에 대한 조회를 수행합니다. 이 서버는 글로벌 카탈로그 조회를 통해 조지민 님의 사서함은 온-프레미스 Exchange 사서함 서버에 있고, 나예준 님의 사서함은 Exchange Online 조직에 있고 하이브리드 라우팅 주소가 yejoon@contoso.mail.onmicrosoft.com인지 확인합니다.

4.  온-프레미스 Exchange 서버는 메시지를 두 개의 복사본으로 분할합니다. 메시지 복사본 중 한 개는 조지민 님의 사서함에 배달된 온-프레미스 Exchange 사서함 서버로 전송됩니다.

5.  메시지의 두 번째 복사본은 온-프레미스 Exchange 서버에 의해 EOP로 전송됩니다. EOP는 TLS를 사용하도록 구성된 전송 커넥터를 사용하여 Exchange Online 조직으로 전송된 메시지를 받습니다.

6.  EOP는 메시지를 Exchange Online 조직으로 보내며, 여기서 메시지에 대해 바이러스를 검색하고 메시지를 David의 사서함으로 배달합니다.

**온-프레미스 및 Exchange Online 조직에 대한 온-프레미스 조직을 통해 메일 라우팅**

![중앙 집중식 인바운드 메일, 온-프레미스](images/JJ659050.a246a1e2-7593-4d13-9426-73622a545c9a(EXCHG.150).png "중앙 집중식 인바운드 메일, 온-프레미스")

## 인터넷으로 메시지 아웃바운드

조직의 받는 사람에게 주소가 지정된 인바운드 메시지의 라우팅 방법은 물론 Exchange Online 받는 사람이 보내는 아웃바운드 메시지의 라우팅 방법도 선택할 수 있습니다. 하이브리드 구성 마법사를 실행할 때 다음 두 옵션 중 하나를 선택할 수 있습니다.

  - **중앙 집중식 메일 전송 사용 안 함**   하이브리드 구성 마법사에서 기본적으로 선택되는 이 옵션을 사용하면 Exchange Online 조직에서 보내는 아웃바운드 메시지가 인터넷으로 직접 라우팅됩니다. Exchange Online 조직의 받는 사람이 보내는 메시지에 온-프레미스 준수 정책 또는 기타 처리 규칙을 적용할 필요가 없는 경우 이 옵션을 사용합니다.

  - **중앙 집중식 메일 전송 사용**   이 옵션을 선택하면 Exchange Online 조직에서 보내는 아웃바운드 메시지가 온-프레미스 조직을 통해 라우팅됩니다. 동일한 Exchange Online 조직의 다른 받는 사람에게 보내는 메시지를 제외하고, Exchange Online 조직의 받는 사람이 보내는 모든 메시지는 온-프레미스 조직을 통해 전송됩니다. 따라서 Exchange Online 조직에 있든, 온-프레미스 조직에 있든 모든 받는 사람에게 적용해야 하는 프로세스나 요구 사항 및 메시지에 준수 규칙을 적용할 수 있습니다.
    

    > [!NOTE]
    > 중앙 집중식 메일 전송은 특정 준수 관련 전송 요구가 있는 조직에만 권장됩니다. 일반적인 Exchange 조직은 중앙 집중식 메일 전송을 사용하지 않는 것이 좋습니다.



온-프레미스 받는 사람이 보낸 메시지는 항상 하이브리드 구성 마법사에서 선택한 위의 항목과 관계없이 DNS를 사용하여 인터넷 받는 사람에게 직접 전송됩니다.

다음 단계와 다이어그램은 온-프레미스 받는 사람이 보낸 메시지에 대한 아웃바운드 메시지 경로를 보여 줍니다.

1.  온-프레미스 Exchange 사서함 서버에 사서함이 있는 조지민 님은 메시지를 외부 인터넷 받는 사람 seo-yun@cpandl.com에게 보냅니다.

2.  Exchange 서버는 cpandl.com의 MX 레코드를 조회하고 메시지를 인터넷에 있는 cpandl.com 메일 서버로 보냅니다.

**온-프레미스 사용자가 인터넷 받는 사람에게 보낸 메시지**

![온-프레미스에서의 아웃바운드 메일](images/JJ659050.71f287d6-b814-4820-a0dc-575f17d13894(EXCHG.150).png "온-프레미스에서의 아웃바운드 메일")

아래에서 Exchange Online 조직의 받는 사람이 인터넷 받는 사람에게 보낸 메시지를 라우팅할 방법에 일치하는 섹션을 읽어 보십시오.

## DNS를 사용하여 Exchange Online의 인터넷 바인딩 메시지 배달(중앙 집중식 메일 전송 사용 안 함)

다음 단계와 다이어그램은 하이브리드 구성 마법사에서 **중앙 집중식 메일 전송 사용**을 선택하지 않은 경우(기본 구성) 발생하는, Exchange Online 받는 사람으로부터 인터넷 받는 사람에게 전송되는 메시지의 아웃바운드 메시지 경로를 보여줍니다.

1.  Exchange Online 조직에 사서함이 있는 David은 메시지를 외부 인터넷 받는 사람 erin@cpandl.com에게 보냅니다.

2.  Exchange Online은 메시지에서 바이러스를 검색하고 메시지를 Exchange Online EOP 회사로 보냅니다.

3.  EOP는 cpandl.com의 MX 레코드를 조회하고 메시지를 인터넷에 있는 cpandl.com 메일 서버로 보냅니다.

**중앙 집중식 메일 전송을 사용하지 않고(기본 구성) 인터넷으로 직접 라우팅된 Exchange Online 보낸 사람의 메일**

![EXO 직접 아웃바운드 메일](images/JJ659050.fe1c4241-0d6e-47bf-b61d-5af732d2dbbc(EXCHG.150).png "EXO 직접 아웃바운드 메일")

## 온-프레미스 조직을 통해 Exchange Online의 인터넷 바인딩 메시지 라우팅(중앙 집중식 메일 전송 사용)

다음 단계와 다이어그램은 하이브리드 구성 마법사에서 **중앙 집중식 메일 전송 사용**을 선택한 경우 발생하는, Exchange Online 받는 사람으로부터 인터넷 받는 사람에게 전송되는 메시지의 아웃바운드 메시지 경로를 보여줍니다.

1.  Exchange Online 조직에 사서함이 있는 David은 메시지를 외부 인터넷 받는 사람 erin@cpandl.com에게 보냅니다.

2.  Exchange Online은 메시지에서 바이러스를 검색하고 메시지를 EOP로 보냅니다.

3.  EOP는 모든 인터넷 바인딩 메시지를 온-프레미스 서버로 보내도록 구성되어 있으므로 메시지가 온-프레미스 Exchange 서버로 라우팅됩니다. TLS를 사용하여 메시지가 전송됩니다.

4.  온-프레미스 Exchange 서버가 나예준 님의 메시지에 대해 규정 준수, 바이러스 백신 및 관리자가 구성한 다른 모든 프로세스를 수행합니다.

5.  온-프레미스 Exchange 서버는 cpandl.com의 MX 레코드를 조회하고 메시지를 인터넷에 있는 cpandl.com 메일 서버로 보냅니다.

**중앙 집중식 메일 전송을 사용하여 온-프레미스 조직을 통해 라우팅된 Exchange Online 보낸 사람의 메일**

![온-프레미스를 통한 아웃바운드 EXO 메일](images/JJ659050.7ea9ffee-944b-45ae-ba4d-c3484100399b(EXCHG.150).png "온-프레미스를 통한 아웃바운드 EXO 메일")

