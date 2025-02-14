---
title: <connectionManagement> 요소(네트워크 설정)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement
- http://schemas.microsoft.com/.NetConfiguration/v2.0#connectionManagement
helpviewer_keywords:
- <connectionManagement> element
- connectionManagement element
ms.assetid: bedccaab-12a2-4511-8f67-e961f249aec6
ms.openlocfilehash: faaba1b9de302ed916ad1a81c7e80b3fb5a67170
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664165"
---
# <a name="connectionmanagement-element-network-settings"></a>\<connectionManagement > 요소 (네트워크 설정)
네트워크 호스트에 대한 최대 연결 수를 지정합니다.  
  
 \<configuration>  
\<system.net>  
\<connectionManagement>  
  
## <a name="syntax"></a>구문  
  
```xml  
<connectionManagement>   
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
 없음  
  
### <a name="child-elements"></a>자식 요소  
  
|**요소**|**설명**|  
|-----------------|---------------------|  
|[add](add-element-for-connectionmanagement-network-settings.md)|연결 관리 목록에 IP 주소 또는 DNS 이름을 추가합니다.|  
|[clear](clear-element-for-connectionmanagement-network-settings.md)|연결 관리 목록을 지웁니다.|  
|[remove](remove-element-for-connectionmanagement-network-settings.md)|연결 관리 목록에서 IP 주소 또는 DNS 이름을 제거 합니다.|  
  
### <a name="parent-elements"></a>부모 요소  
  
|**요소**|**설명**|  
|-----------------|---------------------|  
|[system.net](system-net-element-network-settings.md)|.NET Framework의 네트워크 연결 방법을 지정하는 설정을 포함합니다.|  
  
## <a name="remarks"></a>설명  
 요소 `connectionManagement` 는 서버 또는 서버 그룹에 대 한 최대 연결 수를 정의 합니다.  
  
## <a name="configuration-files"></a>구성 파일  
 이 요소는 애플리케이션 구성 파일 또는 컴퓨터 구성 파일(Machine.config)에서 사용할 수 있습니다.  
  
## <a name="example"></a>예제  
 다음 예에서는 서버 `www.contoso.com` 에 대 한 4 개의 연결과 다른 모든 서버에 대 한 두 개의 연결을 사용 하도록 응용 프로그램을 구성 합니다.  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address = "http://www.contoso.com" maxconnection = "4" />  
      <add address = "*" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>참고자료

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [네트워크 설정 스키마](index.md)
