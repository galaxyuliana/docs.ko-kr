---
title: <webProxyScript> 요소(네트워크 설정)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webProxyScript
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/webProxyScript
helpviewer_keywords:
- <webProxyScript> element
- webProxyScript element
ms.assetid: a13c26db-6218-4af3-9696-38f24b23bfac
ms.openlocfilehash: 8a77c2567401fd80e355bb7fcee17b6684653ebe
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659042"
---
# <a name="webproxyscript-element-network-settings"></a>\<webProxyScript > 요소 (네트워크 설정)
웹 프록시를 검색 하는 데 사용 되는 스크립트의 특징을 구성 합니다.  
  
 \<configuration>  
\<system.net>  
\<settings>  
\<webProxyScript>  
  
## <a name="syntax"></a>구문  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|특성|Description|  
|---------------|-----------------|  
|`downloadTimeout`|스크립트를 다운로드 하는 최대 시간을 시간, 분, 초 단위로 지정 합니다. 기본값은 1 분입니다.|  
  
### <a name="child-elements"></a>자식 요소  
 없음  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|Description|  
|-------------|-----------------|  
|[settings](settings-element-network-settings.md)|<xref:System.Net> 네임스페이스에 대한 기본 네트워크 옵션을 구성합니다.|  
  
## <a name="remarks"></a>설명  
  
## <a name="configuration-files"></a>구성 파일  
 이 요소는 애플리케이션 구성 파일 또는 컴퓨터 구성 파일(Machine.config)에서 사용할 수 있습니다.  
  
## <a name="see-also"></a>참고자료

- [네트워크 설정 스키마](index.md)
