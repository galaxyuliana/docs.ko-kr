---
title: <endToEndTracing>
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 6b23728451a051f21ad3863b9a29e6290c3c837a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919009"
---
# <a name="endtoendtracing"></a>\<endToEndTracing>
서비스 애플리케이션 실행 중에 엔드투엔드 추적의 다양한 측면을 사용하거나 사용하지 않도록 설정할 수 있는 구성 요소입니다.  
  
 \<system.ServiceModel>  
\<diagnostic>  
\<endToEndTracing>  
  
## <a name="syntax"></a>구문  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|특성|Description|  
|---------------|-----------------|  
|`activityTracing`|활동 추적 사용 여부를 지정하는 부울 값입니다.|  
|`messageFlowTracing`|메시지 흐름 추적 사용 여부를 지정하는 부울 값입니다.|  
|`propagateActivity`|propagate 특성을 true로 설정할지 여부를 지정하는 부울 값입니다.|  
  
### <a name="child-elements"></a>자식 요소  
 없음  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[\<diagnostics>](diagnostics.md)|관리자의 런타임 검사 및 제어를 위한 WCF 설정을 정의합니다.|  
  
## <a name="see-also"></a>참고자료

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [엔드투엔드 추적](../../../wcf/diagnostics/tracing/end-to-end-tracing.md)
