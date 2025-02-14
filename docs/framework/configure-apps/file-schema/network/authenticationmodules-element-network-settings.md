---
title: <authenticationModules> 요소(네트워크 설정)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#authenticationModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules
helpviewer_keywords:
- authenticationModules element
- <authenticationModules> element
ms.assetid: 10fcfaad-82ef-4692-871a-0aec9dfbe75e
ms.openlocfilehash: 6488bfcd97e27a184b4a8cd1498d1c60f32babda
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659481"
---
# <a name="authenticationmodules-element-network-settings"></a>\<authenticationModules > 요소 (네트워크 설정)
네트워크 요청을 인증 하는 데 사용 되는 모듈을 지정 합니다.  
  
 \<configuration>  
\<system.net>  
\<authenticationModules>  
  
## <a name="syntax"></a>구문  
  
```xml  
<authenticationModules>   
</authenticationModules>  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
 없음  
  
### <a name="child-elements"></a>자식 요소  
  
|**요소**|**설명**|  
|-----------------|---------------------|  
|[add](add-element-for-authenticationmodules-network-settings.md)|응용 프로그램에 인증 모듈을 추가 합니다.|  
|[clear](clear-element-for-authenticationmodules-network-settings.md)|응용 프로그램에서 모든 인증 모듈을 지웁니다.|  
|[remove](remove-element-for-authenticationmodules-network-settings.md)|응용 프로그램에서 인증 모듈을 제거 합니다.|  
  
### <a name="parent-elements"></a>부모 요소  
  
|**요소**|**설명**|  
|-----------------|---------------------|  
|[system.net](system-net-element-network-settings.md)|.NET Framework의 네트워크 연결 방법을 지정하는 설정을 포함합니다.|  
  
## <a name="remarks"></a>설명  
 요소 `authenticationModule` 는 서버를 사용 하 여 인증 프로세스를 수행 하는 인증 모듈을 지정 합니다. 인증 모듈은 인터페이스를 <xref:System.Net.IAuthenticationModule> 구현 해야 합니다.  
  
## <a name="configuration-files"></a>구성 파일  
 이 요소는 애플리케이션 구성 파일 또는 컴퓨터 구성 파일(Machine.config)에서 사용할 수 있습니다.  
  
## <a name="example"></a>예제  
 다음 예에서는 인증 모듈을 사용 하도록 설정 합니다. Version 및 PublicKeyToken의 값을 지정 된 모듈의 올바른 값으로 바꾸어야 합니다.  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <add type="System.Net.DigestClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>참고자료

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [네트워크 설정 스키마](index.md)
