---
title: <custom>
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: b5cc522604fa7aca8ca6eae787520265b36fef6f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925948"
---
# <a name="custom"></a>\<custom>
사용자 지정 피어 확인자 서비스의 설정을 지정합니다.  
  
\<system.serviceModel>  
\<bindings>  
\<netPeerBinding>  
\<binding>  
\<resolver>  
\<custom>  
  
## <a name="syntax"></a>구문  
  
```xml  
<custom address="Uri"
        resolverType="String">
  <headers/>
  <identity/>
</custom>
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|특성|Description|  
|---------------|-----------------|  
|`address`|사용자 지정 피어 확인자 서비스를 호스트하는 피어 노드의 엔드포인트 주소를 지정하는 URI입니다.|  
|`resolverType`|사용자 지정 피어 확인자 서비스의 형식을 지정하는 문자열입니다.|  
  
### <a name="child-elements"></a>자식 요소  
  
|요소|Description|  
|-------------|-----------------|  
|[\<identity>](identity.md)|이 요소로 구성된 사용자 지정 피어 확인자의 ID를 지정합니다. 이 요소는 <xref:System.ServiceModel.Configuration.IdentityElement> 형식입니다.|  
|[\<headers>](headers-element.md)|사용자 지정 피어 확인자에서 처리하는 SOAP 메시지에 사용되는 주소 헤더 컬렉션입니다.|  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|Description|  
|-------------|-----------------|  
|[\<resolver>](resolver.md)|메시에 참여하는 몇 개의 노드를 나타내는 피어 노드 주소 집합에 대한 피어 메시 ID를 확인하는 데 사용되는 피어 확인자입니다.|  
  
## <a name="remarks"></a>설명  
 이 요소는 서비스를 호스트하는 피어의 엔드포인트 주소 및 모든 특정 바인딩 설정을 포함하여 사용자 지정 피어 확인자 서비스에 대한 기본 설정을 정의합니다. 사용자 지정 해결 프로그램을 만드는 방법에 대 한 자세한 내용은 [PeerChannel 응용 프로그램에 사용자 지정 해결 프로그램 추가](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))를 참조 하세요.  
  
## <a name="see-also"></a>참고자료

- <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>
- <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>
- <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>
- <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>
- [피어 확인자](../../../wcf/feature-details/peer-resolvers.md)
- [PeerChannel 응용 프로그램에 사용자 지정 해결 프로그램 추가](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))
