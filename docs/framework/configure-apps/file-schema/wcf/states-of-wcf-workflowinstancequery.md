---
title: <states>WCF의<workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: d17f7525-8035-4e9e-85a0-4cddae59f85d
ms.openlocfilehash: ef4ce4b6fa6e60ead10b196b10a7c1489e15ac25
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938974"
---
# <a name="states-of-wcf-workflowinstancequery"></a>\<WCF, \<workflowInstanceQuery의 > 상태 >

추적 레코드가 만들어질 때 추적된 워크플로 인스턴스에서 구독된 상태의 컬렉션을 나타냅니다.  
  
추적 프로필 쿼리에 대 한 자세한 내용은 [추적 프로필](../../../windows-workflow-foundation/tracking-profiles.md) 을 참조 하세요.  
  
\<system.serviceModel> \<tracking>  
\<profiles>  
\<trackingProfile>  
\<workflow>  
\<workflowInstanceQueries>  
\<workflowInstanceQuery>  
\<states>  
  
## <a name="syntax"></a>구문  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <workflowInstanceQueries>
          <workflowInstanceQuery>
            <states>
              <state name="Name" />
            </states>
          </workflowInstanceQuery>
        </workflowInstanceQueries>
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
|[\<states>](state-of-wcf-workflowinstancequery.md)|추적 레코드가 만들어질 때 추적된 워크플로 인스턴스에서 구독된 상태입니다.|  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|Description|  
|-------------|-----------------|  
|[\<workflowInstanceQuery>](../windows-workflow-foundation/workflowinstancequery.md)|시작된 이벤트나 완료된 이벤트와 같이 워크플로 인스턴스 수명 주기의 변경 내용을 추적하는 쿼리입니다.|  
  
## <a name="remarks"></a>설명

반환되는 레코드는 이 컬렉션의 상태를 기준으로 필터링됩니다.  
  
가능한 상태 값은 다음 표에 설명되어 있습니다.  
  
|상태|설명|  
|-----------|-----------------|  
|Aborted|워크플로 인스턴스가 중단되었습니다.|  
|Completed|워크플로 인스턴스가 완료되었습니다.|  
|삭제됨|워크플로 인스턴스가 삭제되었습니다.|  
|Idle|워크플로 인스턴스가 유휴 상태입니다.|  
|Persisted|워크플로 인스턴스가 지속되었습니다.|  
|Resumed|워크플로 인스턴스가 다시 시작되었습니다.|  
|Started|워크플로 인스턴스가 시작되었습니다.|  
|UnhandledException|워크플로 인스턴스에서 처리되지 않은 예외가 발생했습니다.|  
|Unloaded|워크플로 인스턴스가 언로드되었습니다.|  
|Canceled|워크플로 인스턴스가 취소되었습니다.|  
|Suspended|워크플로 인스턴스가 일시 중단된 경우|  
|Terminated|워크플로 인스턴스가 종료됩니다.|  
|Unsuspended|워크플로 인스턴스의 일시 중단이 해제됩니다.|  
  
## <a name="example"></a>예제

다음 구성은 이 쿼리를 사용하여 `Started` 인스턴스 상태에 대한 워크플로 인스턴스 수준 추적 레코드를 구독합니다.  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a>참고자료

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [워크플로 추적](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [추적 프로필](../../../windows-workflow-foundation/tracking-profiles.md)
