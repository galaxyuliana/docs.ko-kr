---
title: <cancelRequestedQueries>WCF의
ms.date: 03/30/2017
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
ms.openlocfilehash: 0f04fc928358c96ca3112422f1a6ccd039269e47
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926243"
---
# <a name="cancelrequestedqueries-of-wcf"></a>\<WCF의 cancelRequestedQueries >
부모 활동에 의한 자식 활동 취소 요청을 추적하는 데 사용되는 쿼리의 컬렉션을 나타냅니다. 추적 참가자가 취소 요청 레코드 개체를 구독하려면 쿼리가 필요합니다.  
  
추적 프로필 쿼리에 대 한 자세한 내용은 [추적 프로필](../../../windows-workflow-foundation/tracking-profiles.md) 을 참조 하세요.  
  
\<system.serviceModel>  
\<tracking>  
\<profiles> \<trackingProfile>  
\<workflow>  
\<cancelRequestedQueries>  
  
## <a name="syntax"></a>구문  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestQueries>
          <cancelRequestQuery activityName="String"
                              childActivityName="String" />
        </cancelRequestQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  

다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성

없음
  
### <a name="child-elements"></a>자식 요소
  
|요소|Description|  
|-------------|-----------------|  
|[\<cancelRequestedQuery>](cancelrequestedquery-of-wcf.md)|부모 활동에 의한 자식 활동 취소 요청을 추적하는 데 사용되는 쿼리입니다.|  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|Description|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> 속성에 의해 식별되는 특정 워크플로에 대한 모든 쿼리를 포함하는 구성 요소입니다.|  
  
## <a name="see-also"></a>참고자료

- <xref:System.Activities.Tracking.CancelRequestedQuery>
- [워크플로 추적](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [추적 프로필](../../../windows-workflow-foundation/tracking-profiles.md)
