---
title: <scopes>의 <add>
ms.date: 03/30/2017
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
ms.openlocfilehash: b190cb72e21d47bdc62aab2daba0f6eea1ee04ac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926625"
---
# <a name="add-of-scopes"></a>\<\<범위 > 추가 >
쿼리 중에 서비스 엔드포인트를 필터링하기 위해 사용할 수 있는 사용자 지정 범위 URI를 추가합니다.  
  
\<system.ServiceModel>  
\<behaviors>  
\<endpointBehaviors>  
\<behavior>  
\<endpointDiscovery>  
\<scopes>  
\<add>  
  
## <a name="syntax"></a>구문  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enable="Boolean">
        <scopes>
          <add scope="URI" />
        </scopes>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|특성|설명|  
|---------------|-----------------|  
|범위|서비스를 찾기 위한 일치 기준으로 사용할 수 있는 엔드포인트의 범위 정보가 포함되는 URI입니다.|  
  
### <a name="child-elements"></a>자식 요소  
 없음  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|Description|  
|-------------|-----------------|  
|[\<scopes>](scopes.md)|쿼리 중에 서비스 엔드포인트를 필터링하기 위해 사용할 수 있는 사용자 지정 범위 URI를 지정하는 구성 요소의 컬렉션을 포함합니다.|  
  
## <a name="see-also"></a>참고자료

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
