---
title: <userPrincipalName>
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: 423a3249a9298675517f0cff08566c3735fa35f1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940507"
---
# <a name="userprincipalname"></a>\<userPrincipalName>
클라이언트에서 인증할 서비스의 UPN(User Principal Name)을 지정합니다.  
  
 UPN을 설정 하는 방법에 대 한 자세한 내용은 [서비스 id 및 인증](../../../wcf/feature-details/service-identity-and-authentication.md)을 참조 하세요.  
  
\<identity>  
\<userPrincipalName>  
  
## <a name="syntax"></a>구문  
  
```xml  
<userPrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|특성|설명|  
|---------------|-----------------|  
|value|사용자 로그온 이름이라고도 하는 사용자 계정 이름 및 사용자 계정이 있는 도메인을 나타내는 도메인 이름입니다. Windows 도메인에 로그온하는 표준 사용법입니다. 형식은: someone@example.com (의 경우 전자 메일 주소).|  
  
### <a name="child-elements"></a>자식 요소  
 없음  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|Description|  
|-------------|-----------------|  
|[\<identity>](identity.md)|클라이언트에서 인증할 서비스의 ID를 지정합니다.|  
  
## <a name="remarks"></a>설명  
 이 id를 사용 하 여 끝점에 연결 하는 WCF (secure Windows Communication Foundation) 클라이언트는 끝점을 사용 하 여 SSPI 인증을 수행할 때 UPN을 사용 합니다.  
  
## <a name="example"></a>예제  
 다음 구성 코드는 클라이언트에서 인증할 서비스의 UPN을 지정합니다.  
  
```xml  
<identity>
  <userPrincipalName value="someone@cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a>참고자료

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.UpnEndpointIdentity>
- [서비스 ID 및 인증](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
