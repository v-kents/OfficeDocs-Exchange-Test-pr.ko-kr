﻿---
title: '메일 사용이 가능한 보안 그룹 관리: Exchange 2013 Help'
TOCTitle: 메일 사용이 가능한 보안 그룹 관리
ms:assetid: 80b3b537-4786-4d02-9202-44e373811a25
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Bb123521(v=EXCHG.150)
ms:contentKeyID: 50482292
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# 메일 사용이 가능한 보안 그룹 관리

 

_**적용 대상:** Exchange Online, Exchange Server 2013_

_**마지막으로 수정된 항목:** 2017-10-04_

메일 사용이 가능한 보안 그룹은 메시지 배포 및 Active Directory의 리소스에 대한 액세스 권한 부여에 사용할 수 있습니다. 자세한 내용은 [받는 사람](recipients-exchange-2013-help.md) 항목을 참조하십시오.

## 시작하기 전에 알아야 할 내용

  - 예상 완료 시간: 2~5분

  - 이러한 절차를 수행하려면 먼저 사용 권한을 할당받아야 합니다. 필요한 사용 권한을 확인하려면 다음을 참조하세요. [받는 사람에 게 사용 권한](recipients-permissions-exchange-2013-help.md) 항목의 "메일 그룹" 항목

  - 이 항목의 절차에 적용할 수 있는 바로 가기 키에 대한 자세한 내용은 [Exchange 관리 센터의 바로 가기 키](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md)을 참조하세요.


> [!TIP]
> 문제가 있습니까? Exchange 포럼에서 도움을 요청하세요. 포럼 주소는 다음과 같습니다. <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A>, 또는 <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## 무슨 작업을 하고 싶으십니까?

## 메일 사용이 가능한 보안 그룹 만들기

## EAC를 사용하여 보안 그룹 만들기

1.  EAC에서 **받는 사람** \> **그룹**으로 이동합니다.

2.  **새로 만들기** ![아이콘 추가](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "아이콘 추가") \> **보안 그룹**을 클릭합니다.

3.  **새 보안 그룹** 페이지에서 다음 필드에 값을 입력합니다.
    
      - **\* 표시 이름**   이 입력란에 표시 이름을 입력합니다. 이 이름은 공유 주소록, 받는 사람: 줄(이 그룹으로 전자 메일을 보낸 경우), EAC의 그룹 목록에 표시됩니다. 표시 이름은 필수이며 다른 사람들이 알아 볼 수 있도록 친숙한 형태로 지정해야 합니다. 또한 포리스트에서 고유해야 합니다.
        

        > [!NOTE]
        > 그룹 명명 정책이 적용된 경우 조직에 적용된 명명 제약 조건을 따라야 합니다. 자세한 내용은 <A href="create-a-distribution-group-naming-policy-exchange-2013-help.md">메일 그룹 명명 정책을 만들려면</A> 항목을 참조하십시오. 조직의 그룹 명명 정책을 덮어쓰려는 경우 <A href="override-the-distribution-group-naming-policy-exchange-2013-help.md">메일 그룹 명명 정책을 무시합니다</A>를 참조하십시오.

    
      - **\* 별칭**   이 상자에 보안 그룹의 별칭을 입력합니다. 별칭은 64자를 초과할 수 없으며 포리스트에서 고유해야 합니다. 전자 메일 메시지의 받는 사람: 줄에 별칭을 입력하면 그룹의 표시 이름으로 확인됩니다.
    
      - **설명**   이 상자에서는 다른 사람들이 그룹의 용도를 파악할 수 있도록 보안 그룹에 대해 설명합니다.
    
      - **조직 구성 단위**   기본값(받는 사람 범위) 이외의 OU(조직 구성 단위)를 선택할 수 있습니다. 받는 사람 범위가 포리스트로 설정되어 있으면 기본값은 EAC를 실행 중인 컴퓨터가 포함된 Active Directory 도메인의 사용자 컨테이너로 설정됩니다. 받는 사람 범위가 특정 도메인으로 설정되어 있으면 해당 도메인의 사용자 컨테이너가 기본적으로 선택됩니다. 받는 사람 범위가 특정 OU로 설정되어 있으면 해당 OU가 기본적으로 선택됩니다.
        
        다른 OU를 선택하려면 **찾아보기**를 클릭합니다. 이 대화 상자에는 지정된 범위 내에 있는 포리스트의 모든 OU가 표시됩니다. 원하는 OU를 선택한 다음 **확인**을 클릭합니다.
    
      - **\* 소유자**   기본적으로 그룹을 만든 사람이 소유자가 됩니다. 모든 그룹에는 한 명 이상의 소유자가 있어야 합니다. **추가**를 클릭하여 소유자를 추가할 수 있습니다.
    
      - **구성원**   이 섹션을 사용하면 구성원을 추가하고 그룹에 가입하거나 그룹에서 탈퇴하려는 사용자에 대해 승인이 필요한지 여부를 지정할 수 있습니다.
        
        그룹 소유자는 그룹의 구성원이 아니어도 됩니다. **그룹 소유자를 구성원으로 추가**를 사용하면 소유자를 구성원으로 추가하거나 구성원에서 제거할 수 있습니다.
        
        그룹에 구성원을 추가하려면 **추가**![아이콘 추가](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "아이콘 추가")를 클릭합니다. 구성원 추가를 마쳤으면 **확인**을 클릭하여 **새 보안 그룹** 페이지로 돌아갑니다.
        
        그룹 소유자가 사용자의 그룹 참가 요청을 받도록 하려면 **소유자 승인 필요** 확인란을 선택합니다. 이 옵션을 선택하면 그룹 소유자만이 구성원을 제거할 수 있습니다.

4.  작업을 마치면 **저장**을 클릭하여 보안 그룹을 만듭니다.


> [!NOTE]
> 기본적으로 모든 새로운 메일 사용이 가능한 보안 그룹을 사용하려면 모든 보낸 사람에 대한 인증이 필요합니다. 따라서 외부 보낸 사람은 메일 사용이 가능한 보안 그룹에 메시지를 보낼 수 없습니다. 모든 보낸 사람의 메시지를 수락하도록 메일 사용이 가능한 보안 그룹을 구성하려면 해당 그룹에 대한 메시지 배달 제한 설정을 수정해야 합니다.



## 셸을 사용하여 보안 그룹 만들기

이 예에서는 별칭은 fsadmin이고 이름은 File Server Managers인 보안 그룹을 만듭니다. 이 보안 그룹은 기본 OU에 생성되고, 그룹 소유자가 승인한 모든 사람이 이 그룹에 참가할 수 있습니다.

    New-DistributionGroup -Name "File Server Managers" -Alias fsadmin -Type security

셸을 사용하여 메일 사용이 가능한 보안 그룹을 만드는 데 대한 자세한 내용은 [New-DistributionGroup](https://technet.microsoft.com/ko-kr/library/aa998856\(v=exchg.150\)) 항목을 참조하십시오.

## 작동 여부는 어떻게 확인합니까?

메일 사용이 가능한 보안 그룹을 성공적으로 만들었는지 확인하려면 다음 중 하나를 수행합니다.

  - EAC에서 **받는 사람** \> **그룹**으로 이동합니다. 새 메일 사용이 가능한 보안 그룹이 그룹 목록에 표시됩니다. **그룹 종류**에서 종류는 **보안 그룹**입니다.

  - 셸에서 다음 명령을 실행하여 새 메일 사용이 가능한 보안 그룹에 대한 정보를 표시합니다.
    
        Get-DistributionGroup <Name> | FL Name,RecipientTypeDetails,PrimarySmtpAddress

## 메일 사용이 가능한 보안 그룹 속성 변경

## EAC를 사용하여 메일 사용이 가능한 보안 그룹 속성 변경

1.  EAC에서 **받는 사람** \> **그룹**으로 이동합니다.

2.  그룹 목록에서 확인하거나 변경할 보안 그룹을 클릭하고 **편집**![편집 아이콘](images/JJ218640.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "편집 아이콘")을 클릭합니다.

3.  그룹 속성 페이지에서 다음 섹션 중 하나를 클릭하여 속성을 보거나 변경합니다.
    
      - General
    
      - Ownership
    
      - Membership
    
      - Membership approval
    
      - Delivery management
    
      - Message approval
    
      - Email options
    
      - MailTip
    
      - Group delegation

## 일반

이 섹션을 사용하여 그룹에 대한 기본 정보를 보거나 변경합니다.

  - **\* 표시 이름** 이 이름은 전자 메일의 주소록, 받는 사람: 줄(이 그룹에 전자 메일을 보낸 경우) 및 그룹 목록에 표시됩니다. 표시 이름은 필수이며 다른 사람들이 알아 볼 수 있도록 친숙한 형태로 지정해야 합니다. 또한 도메인 내에서 고유해야 합니다.

  - **\* 별칭**   전자 메일 주소 중에서 @ 기호 왼쪽에 표시되는 부분입니다. 별칭을 변경하면 그룹의 기본 SMTP 주소도 변경되며 새 별칭을 포함하게 됩니다. 또한 이전 별칭을 사용한 전자 메일 주소는 그룹의 프록시 주소로 남아 있습니다.

  - **설명**   이 입력란에는 다른 사람들이 그룹의 용도를 파악할 수 있도록 그룹에 대해 설명합니다. 이 설명은 주소록과 EAC의 세부 정보 창에 나타납니다.

  - **주소록에서 이 그룹 숨기기**   주소록에 이 그룹이 표시되지 않게 하려면 이 확인란을 선택합니다. 이 확인란을 선택한 경우 보낸 사람이 그룹에 메일을 보내려면 받는 사람: 또는 참조: 줄에 그룹의 별칭이나 전자 메일 주소를 입력해야 합니다.
    

    > [!TIP]
    > 일반적으로 보안 그룹은 전자 메일을 보내는 용도가 아닌 그룹 구성원에게 사용 권한을 할당하는 데 사용되므로 숨기는 것이 좋습니다.



  - **조직 구성 단위**   이 읽기 전용 상자는 보안 그룹이 포함된 조직 구성 단위(OU)를 표시합니다. 그룹을 다른 OU로 이동하려면 Active Directory 사용자 및 컴퓨터를 사용해야 합니다.

## 소유권

이 섹션을 사용하면 그룹 소유자를 할당할 수 있습니다. 그룹 소유자는 그룹에 구성원을 추가하고 그룹 참가 요청을 승인하거나 거부할 수 있습니다. 기본적으로 그룹을 만든 사람이 소유자가 됩니다. 모든 그룹에는 한 명 이상의 소유자가 있어야 합니다.

**추가** ![아이콘 추가](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "아이콘 추가")를 클릭하여 소유자를 추가할 수 있습니다. 소유자를 선택한 다음 **제거**![아이콘 제거](images/Dd362328.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "아이콘 제거")를 클릭하여 소유자를 제거할 수 있습니다.

## 구성원

이 섹션을 사용하면 구성원을 추가하거나 제거할 수 있습니다. 그룹 소유자는 그룹의 구성원이 아니어도 됩니다. **구성원** 아래에서 **추가**![아이콘 추가](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "아이콘 추가")를 클릭하여 구성원을 추가할 수 있습니다. 구성원 목록에서 사용자를 선택한 다음 **제거**![아이콘 제거](images/Dd362328.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "아이콘 제거")를 클릭하여 구성원을 제거할 수 있습니다.

## 구성원 승인

이 섹션을 사용하면 사용자가 그룹에 참가할 때 소유자 승인이 필요한지 여부를 지정할 수 있습니다. **소유자 승인 필요** 확인란을 선택하면 그룹 소유자가 그룹 참가 승인을 요청하는 전자 메일을 받습니다. 앞에서 설명한 대로 소유자만이 그룹에서 구성원을 제거할 수 있습니다.


> [!NOTE]
> 이 옵션을 메일 사용이 가능한 보안 그룹과 보안 관련 제한 사항으로 인해 작동 하지 않습니다.



## 배달 관리

이 섹션을 사용하여 이 그룹으로 메일을 보낼 수 있는 사람을 관리합니다.

  - **조직 내부의 보낸 사람만**   조직 내의 보낸 사람만 그룹에 메시지를 보낼 수 있도록 하려면 이 옵션을 선택합니다. 즉, 조직 외부의 사람이 이 그룹에 전자 메일 메시지를 보내면 거부됩니다. 기본 설정입니다.

  - **조직 내부 및 외부의 보낸 사람**   이 옵션을 선택하면 모든 사람이 그룹에 메시지를 보낼 수 있습니다.
    
    특정 보낸 사람만 이 그룹에 메시지를 보낼 수 있도록 하여 메시지를 보낼 수 있는 사람을 추가로 제한할 수 있습니다. **추가**![아이콘 추가](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "아이콘 추가")를 클릭하고 하나 이상의 받는 사람을 선택합니다. 이 목록에 보낸 사람을 추가하면 목록에 있는 사람만 그룹에 메일을 보낼 수 있습니다. 목록에 없는 사람이 보낸 메일은 거부됩니다.
    
    목록에서 사람 또는 그룹을 제거하려면 목록에서 해당 사람 또는 그룹을 선택하고 **제거**![아이콘 제거](images/Dd362328.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "아이콘 제거")를 클릭합니다.
    

    > [!IMPORTANT]
    > 조직 내부의 보낸 사람만 그룹에 메시지를 보낼 수 있도록 그룹을 구성한 경우 이 목록에 메일 연락처를 추가해도 해당 메일 연락처에서 보낸 전자 메일이 거부됩니다.



## 메시지 승인

이 섹션을 사용하여 그룹 중재 옵션을 설정합니다. 중재자는 메시지가 그룹 구성원에게 배달되기 전에 그룹으로 전송된 메시지를 승인 또는 거부합니다.

  - **이 그룹에 전송된 메시지는 중재자의 승인을 받아야 합니다.**   이 확인란은 기본적으로 선택되어 있지 않습니다. 이 확인란을 선택하면 그룹 중재자가 들어오는 메시지를 배달하기 전에 검토합니다. 그룹 중재자는 들어오는 메시지를 승인하거나 거부할 수 있습니다.

  - **그룹 중재자**   그룹 중재자를 추가하려면 **추가**![아이콘 추가](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "아이콘 추가")를 클릭합니다. 중재자를 제거하려면 해당 중재자를 선택하고 **제거**![아이콘 제거](images/Dd362328.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "아이콘 제거")를 클릭합니다. "이 그룹에 전송된 메시지는 중재자의 승인을 받아야 합니다." 확인란을 선택한 경우 중재자를 선택하지 않으면 그룹에 대한 메시지가 승인을 위해 그룹 소유자에게 전송됩니다.

  - **메시지 승인이 필요 없는 보낸 사람**   이 그룹에 대해 중재를 무시할 수 있는 사람이나 그룹을 추가하려면 **추가**![아이콘 추가](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "아이콘 추가")를 클릭합니다. 사람 또는 그룹을 제거하려면 해당 항목을 선택하고 **제거**![아이콘 제거](images/Dd362328.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "아이콘 제거")를 클릭합니다.

  - **중재 알림 선택   **이 섹션에서는 메시지 승인에 대해 사용자들이 알림을 받는 방법을 설정합니다.
    
      - **모든 사용자에게 메시지가 승인되지 않았음을 알립니다.**   기본 설정입니다. 메시지가 승인되지 않은 경우 조직 내부와 외부의 보낸 사람에게 알립니다.
    
      - **메시지가 승인되지 않았을 경우 조직의 보낸 사람에게 알립니다.**   이 옵션을 선택하면 그룹으로 보낸 메시지를 중재자가 승인하지 않는 경우 조직에 속한 사람이나 그룹에게만 해당 사실을 알립니다.
    
      - **승인 메시지가 아닌 경우 알림을 보내지 않습니다.**   이 옵션을 선택하면 그룹 중재자가 승인하지 않은 메시지를 보낸 사람에게 알림을 보내지 않습니다.

## 전자 메일 옵션

이 섹션을 사용하여 그룹과 연결된 전자 메일 주소를 보거나 변경합니다. 여기에는 그룹의 기본 SMTP 주소와 관련된 프록시 주소가 포함됩니다. 기본 SMTP 주소(*회신 주소*)는 주소록에 굵게 표시되며 대문자로 된 **SMTP** 값이 **유형** 열에 표시됩니다.

  - **추가**   이 사서함에 대해 새 전자 메일 주소를 추가하려면 **추가**![아이콘 추가](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "아이콘 추가")를 클릭합니다. 다음 주소 형식 중 하나를 선택합니다.
    
      - **SMTP**   기본 주소 유형입니다. 이 단추를 클릭하고 **\* 전자 메일 주소** 상자에 새 SMTP 주소를 입력합니다.
        

        > [!NOTE]
        > 새 주소를 그룹의 기본 SMTP 주소로 지정하려면 <STRONG>이 주소를 회신 주소로 지정</STRONG> 확인란을 선택합니다. 이 확인란은 <STRONG>이 받는 사람에게 적용된 전자 메일 주소 정책에 따라 전자 메일 주소를 자동으로 업데이트</STRONG> 확인란을 선택하지 않은 경우에만 표시됩니다.

    
      - **사용자 지정 주소 유형**   이 단추를 클릭하고 **\* 전자 메일 주소** 상자에 지원되는 SMTP 이외의 전자 메일 주소 유형 중 하나를 입력합니다.
        

        > [!NOTE]
        > X.400 주소를 제외하고 Exchange는 사용자 지정 주소 형식이 올바른지 확인하지 않습니다. 지정하는 사용자 지정 주소는 해당 주소 유형에 대한 형식 요구 사항을 충족해야 합니다.



  - **편집**   그룹과 연결된 전자 메일 주소를 변경하려면 목록에서 주소를 선택한 다음 **편집**![편집 아이콘](images/JJ218640.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "편집 아이콘")을 클릭합니다.
    

    > [!NOTE]
    > 기존 주소를 그룹의 기본 SMTP 주소로 지정하려면 <STRONG>이 주소를 회신 주소로 지정</STRONG> 확인란을 선택합니다. 앞에서 설명한 대로 이 확인란은 <STRONG>이 받는 사람에게 적용된 전자 메일 주소 정책에 따라 전자 메일 주소를 자동으로 업데이트</STRONG> 확인란을 선택하지 않은 경우에만 표시됩니다.



  - **제거**   그룹과 연결된 전자 메일 주소를 삭제하려면 목록에서 주소를 선택한 다음 **제거**![아이콘 제거](images/Dd362328.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "아이콘 제거")를 클릭합니다.

  - **이 받는 사람에게 적용된 전자 메일 주소 정책에 따라 전자 메일 주소를 자동으로 업데이트**   조직의 전자 메일 주소 정책에 대한 변경 내용에 따라 받는 사람의 전자 메일 주소가 자동으로 업데이트되도록 하려면 이 확인란을 선택합니다. 이 확인란은 기본적으로 선택되어 있습니다.

## MailTip

이 섹션에서는 메일 설명을 추가하여 이 그룹으로 메시지를 보낼 경우 발생할 수 있는 문제를 사용자에게 알릴 수 있습니다. 메일 설명은 새 전자 메일 메시지의 받는 사람, 참조 또는 숨은 참조 필드에 이 그룹이 추가될 때 정보 표시줄에 표시되는 텍스트입니다. 예를 들어 대규모 그룹에 메일 설명을 추가하여 잠재적인 보낸 사람에게 자신의 메시지를 여러 사람에게 보낼 것임을 알려줄 수 있습니다.


> [!NOTE]
> 메일 설명은 HTML 태그를 포함할 수 있지만 스크립트는 사용할 수 없습니다. 표시되는 사용자 지정 메일 설명의 길이는 175자를 초과할 수 없습니다. 단, HTML 태그는 길이 제한 계산에 포함되지 않습니다.



## 그룹 위임

이 섹션에서는 사용자에게 그룹으로 메시지를 보내거나 그룹 대신 메시지를 보내기 위한 권한을 할당합니다(*위임*). 다음 권한을 할당할 수 있습니다.

  - **다른 사람 이름으로 보내기**   이 권한을 사용하면 대리인은 그룹으로서 메시지를 보낼 수 있습니다. 이 권한이 할당되면 대리인에게는 **보낸 사람** 줄에 그룹을 추가하여 해당 메시지를 그룹에서 보낸 것으로 표시할 수 있는 옵션이 제공됩니다.

  - **대신 보내기**   이 권한이 있어도 대리인은 그룹 대신 메시지를 보낼 수 있습니다. 이 사용 권한이 할당된 후 대리인은 **보낸 사람** 줄에 그룹을 추가할 수 있습니다. 메시지는 그룹이 보낸 것으로 나타나며 그룹 대신 대리인이 보낸 것으로 확인됩니다.

대리인에게 권한을 할당하려면 해당 권한 아래의 **추가**를 클릭하여 **받는 사람 선택** 페이지를 표시합니다. 이 페이지에는 해당 권한이 할당될 수 있는 Exchange 조직 내의 모든 받는 사람 목록이 표시됩니다. 원하는 받는 사람을 선택하여 목록에 추가한 다음 **확인**을 클릭합니다. 또한 검색 상자에 받는 사람 이름을 입력한 다음 **검색**![검색 아이콘](images/Dd353189.773574d0-9b92-4cab-9f6b-81532c7418b9(EXCHG.150).gif "검색 아이콘")을 클릭하여 특정 받는 사람을 검색할 수도 있습니다.

## 셸을 사용하여 보안 그룹 속성 변경

**Get-DistributionGroup** 및 **Set-DistributionGroup** cmdlet을 사용하면 보안 그룹에 대한 속성을 확인하고 변경할 수 있습니다. 셸 사용의 이점은 EAC에서는 사용할 수 없는 속성을 변경하고 여러 보안 그룹에 대한 속성을 변경할 수 있다는 것입니다. 메일 그룹 속성별로 해당하는 매개 변수에 대한 자세한 내용은 다음 항목을 참조하십시오.

  - [Get-DistributionGroup](https://technet.microsoft.com/ko-kr/library/bb124755\(v=exchg.150\))

  - [Set-DistributionGroup](https://technet.microsoft.com/ko-kr/library/bb124955\(v=exchg.150\))

다음은 셸을 사용하여 보안 그룹 속성을 변경하는 몇 가지 예입니다.

이 예에서는 조직의 모든 보안 그룹 목록을 표시합니다.

    Get-DistributionGroup -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'MailUniversalSecurityGroup')}

이 예에서는 Seattle Administrators 보안 그룹에 대한 기본 SMTP 주소(회신 주소라고도 함)를 admins@contoso.com에서 seattle.admins@contoso.com으로 변경합니다. 이전 회신 주소는 프록시 주소로 유지됩니다.

    Set-DistributionGroup "Seattle Employees" -EmailAddresses SMTP:sea.admins@contoso.com,smtp:admins@contoso.com

이 예에서는 조직의 모든 보안 그룹을 주소록에서 숨깁니다.

    Get-DistributionGroup -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'MailUniversalSecurityGroup')} | Set-DistributionGroup -HiddenFromAddressListsEnabled $true

## 작동 여부는 어떻게 확인합니까?

보안 그룹에 대한 속성을 성공적으로 변경했는지 확인하려면 다음을 수행합니다.

  - EAC에서 해당 그룹을 선택하고 **편집**![편집 아이콘](images/JJ218640.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "편집 아이콘")을 클릭하여 변경한 속성이나 기능을 확인합니다. 변경한 속성에 따라, 선택한 그룹에 대한 세부 정보 창에 해당 속성 변경 내용이 표시될 수도 있습니다.

  - 셸에서 **Get-DistributionGroup** cmdlet을 사용하여 변경 사항을 확인합니다. 셸을 사용할 때 얻을 수 있는 한 가지 이점은 여러 그룹의 여러 속성을 볼 수 있다는 것입니다. 모든 보안 그룹이 주소록에서 숨겨진 위의 예에서 다음 명령을 실행하여 새 값을 확인합니다.
    
        Get-DistributionGroup -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'MailUniversalSecurityGroup')} |
         fl Name,HiddenFromAddressListsEnabled


<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><img src="images/Bb123521.eac8a413-9498-4220-8544-1e37d1aaea13(EXCHG.150).png" title="LinkedIn Learning용 단축 아이콘" alt="LinkedIn Learning용 단축 아이콘" /> <strong>Office 365를 처음 사용하시나요?</strong><br />
LinkedIn Learning에서 제공하는 <a href="https://support.office.com/en-us/article/office-365-admin-and-it-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5">Office 365 admins and IT pros</a>의 무료 비디오 과정을 확인해보세요.</p></td>
</tr>
</tbody>
</table>
