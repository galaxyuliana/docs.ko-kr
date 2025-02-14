---
title: <httpWebRequest> 요소(네트워크 설정)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/httpWebRequest
- http://schemas.microsoft.com/.NetConfiguration/v2.0#httpWebRequest
helpviewer_keywords:
- <httpWebRequest> element
- httpWebRequest element
ms.assetid: 52acd9d2-5bdc-4dc4-9c2a-f0a476ccbb31
ms.openlocfilehash: de5672e5c6762b1e0742e717a3d499a4f93ee8ec
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659337"
---
# <a name="httpwebrequest-element-network-settings"></a>\<httpWebRequest > 요소 (네트워크 설정)
웹 요청 매개 변수를 사용자 지정 합니다.  
  
 \<configuration>  
\<system.net>  
\<settings>  
\<httpWebRequest>  
  
## <a name="syntax"></a>구문  
  
```xml  
<httpWebRequest  
  maximumResponseHeadersLength="size"  
  maximumErrorResponseLength="size"  
  maximumUnauthorizedUploadLength="size"  
  useUnsafeHeaderParsing="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|**특성**|**설명**|  
|-------------------|---------------------|  
|`maximumResponseHeadersLength`|응답 헤더의 최대 길이 (kb)를 지정 합니다. 기본값은 64입니다. 값이-1 이면 응답 헤더에 크기 제한이 적용 되지 않습니다.|  
|`maximumErrorResponseLength`|오류 응답의 최대 길이 (kb)를 지정 합니다. 기본값은 64입니다. 값이-1 이면 오류 응답에 크기 제한이 적용 되지 않습니다.|  
|`maximumUnauthorizedUploadLength`|승인 되지 않은 오류 코드에 대 한 응답으로 업로드의 최대 길이 (바이트)를 지정 합니다. 기본값은 -1입니다. -1은 업로드할 때 크기 제한이 적용되지 않음을 나타냅니다.|  
|`useUnsafeHeaderParsing`|안전 하지 않은 헤더 구문 분석을 사용할 수 있는지 여부를 지정 합니다. 기본값은 `false`입니다.|  
  
### <a name="child-elements"></a>자식 요소  
 없음  
  
### <a name="parent-elements"></a>부모 요소  
  
|**요소**|**설명**|  
|-----------------|---------------------|  
|[settings](settings-element-network-settings.md)|<xref:System.Net> 네임스페이스에 대한 기본 네트워크 옵션을 구성합니다.|  
  
## <a name="remarks"></a>설명  
 기본적으로 .NET Framework는 URI 구문 분석에 대해 RFC 2616를 엄격 하 게 적용 합니다. 일부 서버 응답에는 <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> <xref:System.Net.WebException>허용 되지 않는 필드의 제어 문자가 포함 될 수 있으며,이로 인해 메서드에서이 throw 됩니다. <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> **Useunsafeheaderparsing 분석이** **true**로 설정 된 경우이 경우가 throw 되지 않지만 응용 프로그램은 다양 한 형식의 URI 구문 분석 공격에 취약 합니다. 가장 좋은 방법은 응답에 제어 문자가 포함 되지 않도록 서버를 변경 하는 것입니다.  
  
## <a name="configuration-files"></a>구성 파일  
 이 요소는 애플리케이션 구성 파일 또는 컴퓨터 구성 파일(Machine.config)에서 사용할 수 있습니다.  
  
## <a name="example"></a>예제  
 다음 예제에서는 표준 최대 헤더 길이 보다 큰를 지정 하는 방법을 보여 줍니다.  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <httpWebRequest  
        maximumResponseHeadersLength="128"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>참고자료

- <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>
- [네트워크 설정 스키마](index.md)
